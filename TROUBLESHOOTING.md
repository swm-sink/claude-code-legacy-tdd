# Legacy Code TDD Framework - Troubleshooting Guide

*Quick solutions to common issues encountered during legacy code transformation*

## 🚨 Emergency Procedures

### Immediate Production Issues

#### "Something broke in production after our transformation!"
```bash
# IMMEDIATE ACTION: Emergency rollback
./rollback.sh

# OR use feature flags for instant rollback
FeatureFlag.disableAll()

# Verify rollback success
/legacy-validate --emergency-mode
```

**Steps**:
1. **Don't panic** - rollback procedures are designed for this
2. **Execute rollback immediately** - investigate later
3. **Verify original functionality restored** - run characterization tests
4. **Communicate with team** - let everyone know system is stable
5. **Post-mortem analysis** - understand what went wrong

#### "Tests are failing after rollback"
```bash
# This indicates characterization tests weren't comprehensive enough
# Immediate action: Fix the failing functionality manually

# 1. Identify what's still broken
git diff HEAD~2 HEAD --name-only

# 2. Run specific test suites
npm test -- --testPathPattern=characterization

# 3. If tests are failing, the rollback wasn't complete
git reset --hard <last-known-good-commit>
```

---

## 🔍 Assessment Issues

### "Assessment command fails or gives unclear results"

#### Problem: `/legacy-assess-risk` exits with errors
```
Error: Unable to analyze codebase
Exit code: 1
```

**Solutions**:
```bash
# 1. Check file permissions
ls -la src/
chmod -R 644 src/**/*.{js,py,swift,java}

# 2. Verify code can be parsed
# For JavaScript/Node.js:
npx eslint src/ --no-eslintrc --parser @babel/eslint-parser

# For Python:
python -m py_compile src/**/*.py

# For Swift:
swiftc -syntax-only src/**/*.swift

# 3. Run assessment with debugging
/legacy-assess-risk --debug --verbose
```

#### Problem: "Assessment results seem wrong or misleading"
```
Assessment Score: 95/100 (seems too optimistic)
Test Coverage: 0%
```

**Diagnosis**:
```bash
# 1. Verify assessment is scanning correct directories
/legacy-assess-risk --show-scan-paths

# 2. Check if assessment is finding test files
find . -name "*test*" -o -name "*Test*" -o -name "*spec*"

# 3. Manual verification of complexity
find . -name "*.js" -exec wc -l {} \; | sort -nr | head -10
```

**Solutions**:
- Ensure assessment scans all source directories
- Verify test file naming conventions match framework expectations
- Run assessment on specific high-risk files: `/legacy-assess-risk --target="src/specific-file.js"`

### "Assessment takes too long or hangs"

#### Problem: Assessment runs for hours without completing
```bash
# Kill hanging assessment safely
pkill -f "legacy-assess"

# Run with timeout and limited scope
timeout 300 /legacy-assess-risk --quick-scan --max-files=100
```

**Solutions**:
```bash
# 1. Exclude large files/directories
/legacy-assess-risk --exclude="node_modules,build,dist,*.min.js"

# 2. Run incremental assessment
/legacy-assess-risk --incremental --since="1 week ago"

# 3. Focus on specific areas
/legacy-assess-risk --target-directory="src/core" --fast-mode"
```

---

## 🛡️ Safety Net Issues

### "Cannot achieve 90% coverage requirement"

#### Problem: Coverage stuck at 70-80% despite adding tests
```
Current Coverage: 78%
Required: 90%
Blocking: All transformation commands
```

**Diagnosis**:
```bash
# 1. Identify uncovered code
/legacy-coverage-report --show-uncovered --detailed

# 2. Find untestable code
/legacy-dependency-analysis --find-untestable

# 3. Analyze coverage gaps
npm run coverage -- --reporter=html
open coverage/index.html  # View detailed coverage report
```

**Solutions**:

**Option A: Add Characterization Tests for Missing Coverage**
```javascript
// For hard-to-test legacy code, add characterization tests
describe('Legacy code characterization', () => {
    it('should preserve current behavior of untested methods', () => {
        const result = legacyObject.difficultToTestMethod();
        
        // Document actual current behavior
        expect(result).toEqual(expect.any(Object));
        expect(result.status).toBeDefined();
        
        // Golden master test for complex output
        expect(result).toMatchSnapshot();
    });
});
```

**Option B: Use Seams to Make Code Testable**
```bash
# Create seams for untestable dependencies
/legacy-dependency-inject --target="UntestableSingleton" --create-seam
```

**Option C: Mock External Dependencies**
```bash
# Generate mocks for external dependencies
/legacy-mock-generator --target-untestable --auto-mock
```

#### Problem: "Tests pass but coverage tool shows 0%"
```
All tests: ✅ PASSED
Coverage: 0% (ERROR)
```

**Solutions**:
```bash
# 1. Coverage tool configuration issue
# For JavaScript/Jest:
cat > jest.config.js << EOF
module.exports = {
    collectCoverage: true,
    collectCoverageFrom: [
        'src/**/*.{js,jsx}',
        '!src/**/*.test.{js,jsx}',
        '!src/index.js'
    ],
    coverageDirectory: 'coverage',
    coverageReporters: ['text', 'lcov', 'html']
};
EOF

# 2. For Python/pytest:
pip install pytest-cov
pytest --cov=src --cov-report=html

# 3. For Swift/Xcode:
xcodebuild test -enableCodeCoverage YES
```

### "Characterization tests keep failing"

#### Problem: Tests fail immediately after creation
```
✅ Created 47 characterization tests
❌ 23 tests failing on first run
```

**This is often a configuration issue**:

**Solution 1: Environment Consistency**
```bash
# Ensure test environment matches characterization environment
# 1. Database state
npm run db:seed-test-data

# 2. External service mocking
npm run start-mock-services

# 3. Configuration
cp .env.test .env.characterization

# 4. Re-run characterization
/legacy-characterize-behavior --refresh --clean-environment
```

**Solution 2: Data Dependencies**
```javascript
// Fix characterization tests with proper test data setup
beforeEach(async () => {
    // Reset to exact state when characterization was captured
    await TestDataManager.loadCharacterizationState();
    await MockServices.resetToCharacterizationState();
});
```

---

## 🔄 Transformation Issues

### "Sprout method integration not working"

#### Problem: New sprouted method never gets called
```javascript
// Sprouted method exists but is never executed
function sproutedEnhancement() {
    console.log("This never appears");
}
```

**Diagnosis**:
```bash
# 1. Check integration point
grep -r "sproutedEnhancement" src/

# 2. Verify feature flag
console.log(FeatureFlag.newEnhancement.isEnabled); // Should be true

# 3. Check call site
```

**Solutions**:
```javascript
// Ensure proper integration in existing method
function existingLegacyMethod() {
    const result = originalLegacyLogic();
    
    // Add integration point with logging
    if (FeatureFlag.newEnhancement.isEnabled) {
        console.log("Feature flag enabled, calling sprouted method");
        sproutedEnhancement(result);
    } else {
        console.log("Feature flag disabled, skipping sprouted method");
    }
    
    return result;
}
```

### "Extract method breaking existing behavior"

#### Problem: Method extraction changes program behavior
```
✅ Method extracted successfully
❌ 12 characterization tests now failing
```

**This indicates extraction wasn't truly safe**:

**Immediate Action: Rollback**
```bash
git revert HEAD~1
/legacy-validate --verify-rollback
```

**Root Cause Analysis**:
```bash
# Compare behavior before/after extraction
git diff HEAD~2 HEAD

# Run specific failing tests with detailed output
npm test -- --verbose CharacterizationTests
```

**Common Causes and Fixes**:

**Cause 1: Variable Scope Issues**
```javascript
// WRONG: Extraction changed variable scope
function extractedMethod() {
    // Local variable now instead of closure variable
    let result = processData();
    return result;
}

// CORRECT: Preserve original variable scope
function extractedMethod(sharedState) {
    // Pass shared state to maintain behavior
    sharedState.result = processData();
    return sharedState.result;
}
```

**Cause 2: Side Effect Changes**
```javascript
// WRONG: Side effects lost during extraction
function extractedMethod() {
    return calculateValue(); // Missing side effects
}

// CORRECT: Preserve all side effects
function extractedMethod() {
    updateGlobalState(); // Preserve side effect
    logActivity();       // Preserve side effect
    return calculateValue();
}
```

### "Performance regression after transformation"

#### Problem: System slower after applying framework techniques
```
Before transformation: 200ms response time
After transformation: 500ms response time
```

**Diagnosis**:
```bash
# 1. Profile the application
npm run performance-profile

# 2. Compare before/after metrics
/legacy-performance-compare --baseline=before-transformation

# 3. Identify bottlenecks
/legacy-assess-risk --focus=performance --detailed"
```

**Common Causes and Solutions**:

**Cause 1: Test Overhead in Production**
```javascript
// PROBLEM: Test code running in production
if (process.env.NODE_ENV === 'test' || FeatureFlag.testing.isEnabled) {
    // This should not run in production!
    runPerformanceTests();
}

// SOLUTION: Proper environment checks
if (process.env.NODE_ENV === 'test') {
    runPerformanceTests();
}
```

**Cause 2: Excessive Characterization Validation**
```javascript
// PROBLEM: Characterization checks in production
function processData(data) {
    const result = newImplementation(data);
    
    // Remove this from production code!
    if (FeatureFlag.characterizationValidation.isEnabled) {
        validateAgainstCharacterization(result);
    }
    
    return result;
}
```

**Cause 3: Too Many Feature Flag Checks**
```javascript
// PROBLEM: Feature flag overhead
function hotPath() {
    if (FeatureFlag.optimization1.isEnabled) { /* ... */ }
    if (FeatureFlag.optimization2.isEnabled) { /* ... */ }
    if (FeatureFlag.optimization3.isEnabled) { /* ... */ }
    // 20+ feature flag checks in hot path
}

// SOLUTION: Cache feature flag state
class FeatureFlagCache {
    constructor() {
        this.cache = new Map();
        this.refreshInterval = 60000; // 1 minute
        this.lastRefresh = 0;
    }
    
    isEnabled(flag) {
        if (Date.now() - this.lastRefresh > this.refreshInterval) {
            this.refreshCache();
        }
        return this.cache.get(flag) || false;
    }
}
```

---

## 🔧 Command-Specific Issues

### `/legacy-sprout` Issues

#### "Sprout class not integrating properly"
```bash
# Generated sprout class but integration fails
Error: Cannot resolve SproutedClass
```

**Solutions**:
```bash
# 1. Check imports and exports
grep -r "export.*SproutedClass" src/
grep -r "import.*SproutedClass" src/

# 2. Verify dependency injection
/legacy-dependency-inject --verify-integration --target="SproutedClass"

# 3. Check build system
npm run build -- --verbose
```

#### "Sprout method tests failing"
```
Generated sprouted method tests: ❌ FAIL
TypeError: Cannot read property 'sproutedMethod' of undefined
```

**Common Fix**:
```javascript
// Test setup issue - method not properly attached
beforeEach(() => {
    // WRONG:
    // sut = new OriginalClass();
    
    // CORRECT: Ensure sprouted method is attached
    sut = new OriginalClass();
    sut.sproutedMethod = require('../sprouted/sproutedMethod');
});
```

### `/legacy-extract` Issues

#### "Extract fails with dependency errors"
```bash
/legacy-extract --target="LargeClass.method"
Error: Cannot extract - too many dependencies
```

**Solutions**:
```bash
# 1. Break dependencies first
/legacy-dependency-inject --target="LargeClass" --break-dependencies

# 2. Use smaller extraction scope
/legacy-extract --target="LargeClass.method" --scope="minimal"

# 3. Extract in multiple phases
/legacy-extract --target="LargeClass.method" --phase=1 --partial
```

### `/legacy-validate` Issues

#### "Validation fails with cryptic errors"
```bash
/legacy-validate
Error: Validation framework internal error
Exit code: 255
```

**Diagnosis and Fix**:
```bash
# 1. Check validation environment
/legacy-validate --check-environment

# 2. Run individual validations
/legacy-validate --test-coverage-only
/legacy-validate --characterization-only
/legacy-validate --performance-only

# 3. Clear validation cache
rm -rf .legacy-cache/
/legacy-validate --rebuild-cache
```

---

## 📊 Coverage and Testing Issues

### "Tests pass individually but fail when run together"

#### Problem: Test suite has race conditions or shared state
```bash
npm test src/components/UserManager.test.js  # ✅ PASS
npm test  # ❌ FAIL: UserManager tests failing
```

**Solutions**:

**Fix 1: Isolate Test State**
```javascript
// PROBLEM: Tests sharing global state
describe('UserManager', () => {
    beforeEach(() => {
        // Reset global state between tests
        UserManager.resetGlobalState();
        MockDatabase.clear();
        FeatureFlag.resetToDefaults();
    });
});
```

**Fix 2: Parallel Test Isolation**
```javascript
// Use test-specific databases/resources
beforeEach(async () => {
    const testId = Math.random().toString(36);
    const testDatabase = await createTestDatabase(`test_${testId}`);
    const testContainer = new TestContainer(testDatabase);
    
    sut = new UserManager(testContainer);
});
```

### "Coverage reports are inconsistent"

#### Problem: Coverage varies between runs
```bash
Run 1: 87% coverage
Run 2: 93% coverage  
Run 3: 81% coverage
```

**Common Causes**:

**Cause 1: Non-Deterministic Tests**
```javascript
// PROBLEM: Random or time-based behavior
it('should process within reasonable time', () => {
    const start = Date.now();
    const result = processor.process();
    const duration = Date.now() - start;
    
    expect(duration).toBeLessThan(100); // Flaky!
});

// SOLUTION: Deterministic testing
it('should process efficiently', () => {
    const mockTimer = new MockTimer();
    const processor = new Processor(mockTimer);
    
    const result = processor.process();
    
    expect(mockTimer.elapsed).toBeLessThan(100);
});
```

**Cause 2: Environment Dependencies**
```javascript
// PROBLEM: Tests depend on external environment
const config = {
    apiUrl: process.env.API_URL || 'https://api.example.com'
};

// SOLUTION: Explicit test configuration
const config = {
    apiUrl: process.env.NODE_ENV === 'test' 
        ? 'http://localhost:3001'
        : process.env.API_URL
};
```

---

## 🏗️ Architecture and Design Issues

### "Framework commands conflict with existing tools"

#### Problem: Framework interferes with existing development tools
```bash
/legacy-assess
Error: Conflicts with existing eslint configuration
Cannot proceed with assessment
```

**Solutions**:

**Fix 1: Tool Configuration Isolation**
```bash
# Create framework-specific configuration
mkdir .legacy-framework/
cp .eslintrc.js .legacy-framework/eslint.config.js

# Modify framework to use isolated config
/legacy-assess-risk --config-dir=".legacy-framework"
```

**Fix 2: Selective Tool Integration**
```bash
# Configure framework to work with existing tools
cat > .legacy-config.json << EOF
{
    "respectExistingConfig": true,
    "linter": "existing",
    "testRunner": "existing",
    "coverageTool": "existing"
}
EOF
```

### "Team resistance to framework adoption"

#### Problem: Team members avoid using the framework
```
"It's too complex"
"Takes too long"
"We know how to refactor safely without it"
```

**Solutions**:

**Approach 1: Start Small and Demonstrate Value**
```bash
# Choose smallest, safest transformation first
/legacy-assess-risk --find-low-risk

# Show quick wins with sprouting
/legacy-sprout --feature="simple-logging" --demo-mode

# Document time savings and safety improvements
```

**Approach 2: Address Specific Concerns**

**"Too Complex" → Provide Training**
- Start team with Level 1 commands only
- Pair programming sessions for framework adoption
- Create team-specific quick reference guides

**"Takes Too Long" → Show Long-Term Benefits**
- Track velocity improvements over time
- Measure bug reduction in framework-managed code
- Calculate time saved by avoiding production incidents

**"We Don't Need It" → Demonstrate Risk Reduction**
- Show assessment results revealing hidden risks
- Compare transformation outcomes with/without framework
- Share success stories from other teams

### "Framework doesn't fit our development process"

#### Problem: Framework assumptions don't match team workflow
```
Our team:
- No feature flags in production
- Continuous deployment without staging
- Monorepo with 50+ services
```

**Adaptation Strategies**:

**No Feature Flags → Use Branch-Based Deployment**
```bash
# Modify framework for branch-based safety
/legacy-sprout --deployment-strategy="branch" --no-feature-flags

# Use environment-based rollback
ENVIRONMENT=staging /legacy-validate
ENVIRONMENT=production /legacy-rollback-if-needed
```

**Continuous Deployment → Enhanced Testing**
```bash
# Increase test coverage requirements
/legacy-safety-net --minimum-coverage=95 --include-integration

# Add deployment validation
/legacy-validate --production-readiness --block-on-failure
```

**Monorepo → Service-Specific Configuration**
```bash
# Configure framework per service
for service in services/*/; do
    cd "$service"
    /legacy-assess-risk --service-specific
    cd - > /dev/null
done
```

---

## 🚀 Performance Optimization

### "Framework commands are too slow"

#### Problem: Assessment and validation take too long for daily use
```bash
time /legacy-assess
# Real: 15m30s (too slow for regular use)
```

**Optimization Strategies**:

**Enable Incremental Processing**
```bash
# Only analyze changed files
/legacy-assess-risk --incremental --since="last-commit"

# Cache analysis results
/legacy-assess-risk --cache-results --cache-dir=".legacy-cache"

# Parallel processing
/legacy-assess-risk --parallel --max-workers=4
```

**Use Fast Mode for Development**
```bash
# Quick assessment for development
/legacy-assess-risk --fast --focus="critical-only"

# Full assessment for CI/CD
/legacy-assess-risk --comprehensive --all-checks
```

**Profile and Optimize**
```bash
# Profile framework performance
/legacy-assess-risk --profile --output-timing

# Identify bottlenecks
/legacy-debug --performance --verbose
```

### "Test suite runs too slowly"

#### Problem: Comprehensive test suite takes too long
```bash
npm test  # 25 minutes for full suite
```

**Solutions**:

**Parallel Test Execution**
```bash
# Configure Jest for parallel execution
npm install --save-dev jest-parallel

# Run tests in parallel
npm test -- --maxWorkers=50%
```

**Test Categorization**
```bash
# Quick tests for development
npm run test:unit  # 3 minutes

# Full tests for CI
npm run test:all   # 25 minutes

# Characterization tests separately
npm run test:characterization  # 8 minutes
```

**Smart Test Selection**
```bash
# Only run tests for changed code
npm test -- --onlyChanged

# Run tests related to specific files
npm test -- --findRelatedTests src/UserManager.js
```

---

## 📋 Best Practices for Troubleshooting

### Systematic Debugging Approach

1. **Isolate the Problem**
   - Run commands individually to identify which step fails
   - Use minimal test cases to reproduce issues
   - Check logs and error messages carefully

2. **Check Environment Consistency**
   - Verify Node.js/Python/Swift versions match requirements
   - Ensure dependencies are installed correctly
   - Check file permissions and access rights

3. **Validate Configuration**
   - Review framework configuration files
   - Check integration with existing development tools
   - Verify environment variables and settings

4. **Use Debug Mode**
   - Run commands with `--debug` and `--verbose` flags
   - Enable detailed logging for analysis
   - Capture and share error traces when seeking help

### Prevention Strategies

#### Regular Framework Maintenance
```bash
# Weekly framework validation
/legacy-validate --comprehensive --report-issues

# Monthly assessment updates
/legacy-assess-risk --refresh-baselines --update-targets

# Quarterly framework updates
git pull origin main  # Update framework
./update-team-training.sh  # Refresh team knowledge
```

#### Team Communication
- **Share troubleshooting knowledge** - document solutions in team wiki
- **Regular framework check-ins** - discuss issues and improvements weekly
- **Escalation procedures** - know when to seek expert help

#### Monitoring and Alerting
```bash
# Set up automated framework health checks
crontab -e
# Add: 0 9 * * * /legacy-validate --health-check --alert-on-failure
```

---

## 🆘 Getting Help

### Self-Service Resources

1. **[Command Reference](COMMAND_REFERENCE.md)** - Detailed documentation for all commands
2. **[User Guide](USER_GUIDE.md)** - Progressive learning and skill development
3. **[Examples](EXAMPLES.md)** - Real-world transformation walkthroughs

### Community Support

- **Search Known Issues**: Check if your problem has been encountered before
- **Framework Updates**: Ensure you're using the latest version
- **Team Knowledge Sharing**: Leverage collective team experience

### When to Seek Expert Help

**Seek immediate expert help if**:
- Production system is unstable after framework use
- Multiple rollback attempts have failed
- Team is blocked on critical business functionality

**Seek guidance for**:
- Complex architectural transformations
- Custom framework adaptations
- Performance optimization challenges

### Emergency Contacts

```bash
# For critical production issues:
# 1. Execute emergency rollback first
./rollback.sh

# 2. Validate system stability
/legacy-validate --emergency-mode

# 3. Document the issue for post-mortem
echo "Issue: $(date)" >> emergency-log.txt
git log --oneline -10 >> emergency-log.txt
```

---

**Remember**: Most issues have straightforward solutions. The framework is designed to be safe and recoverable. When in doubt, use the rollback procedures and analyze the problem systematically. The safety infrastructure is there to protect you - trust it and use it.