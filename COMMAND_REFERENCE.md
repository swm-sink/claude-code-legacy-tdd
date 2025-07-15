# 📚 Command Reference - Legacy Code TDD Framework

*Complete documentation of all 24 commands organized by safety-first workflow*

**🎯 SAFETY FIRST:** Commands are organized by phases with mandatory prerequisites. Each phase must be completed before proceeding to the next.

---

## 🚦 Command Execution Phases

### Command Dependencies and Flow
```
Phase 1: ASSESSMENT          Phase 2: SAFETY NET         Phase 3: TRANSFORMATION     Phase 4: VALIDATION
┌─────────────────────┐      ┌─────────────────────┐      ┌─────────────────────┐     ┌─────────────────────┐
│ 5 Assessment        │ ──>  │ 5 Safety Commands   │ ──>  │ 10 Transform        │ ──> │ 4 Validation        │
│ Commands            │      │                     │      │ Commands            │     │ Commands            │
└─────────────────────┘      └─────────────────────┘      └─────────────────────┘     └─────────────────────┘
 
        MANDATORY ORDER              MANDATORY ORDER               SAFE TO EXECUTE           CONTINUOUS VALIDATION
```

**⚠️ BLOCKING REQUIREMENTS:**
- Phase 2 commands BLOCKED until Phase 1 complete
- Phase 3 commands BLOCKED until 90% test coverage achieved
- Phase 4 commands run continuously during transformation

---

## 📊 Phase 1: Assessment Commands (5 Commands)

**Goal**: Understand legacy code before touching anything

### `/legacy-assess-risk`
**Purpose**: Identify complexity hotspots and critical transformation areas

**Usage**:
```bash
/legacy-assess-risk
/legacy-assess-risk --target="src/specific-file.js"
/legacy-assess-risk --detailed --include-metrics
```

**What it does**:
- Analyzes code complexity using cyclomatic complexity metrics
- Identifies god objects and excessive method counts
- Scans for potential security vulnerabilities
- Generates risk heat map for transformation planning

**Output**:
```
RISK ASSESSMENT COMPLETE:
- High Risk Files: 3 (>500 lines or complexity >20)
- Medium Risk Files: 12 (200-500 lines or complexity 10-20)
- Low Risk Files: 47 (manageable complexity)

TRANSFORMATION READINESS SCORE: 67/100
RECOMMENDATION: Proceed with comprehensive safety net
```

---

### `/legacy-coverage-report`
**Purpose**: Analyze test coverage gaps and priorities

**Usage**:
```bash
/legacy-coverage-report
/legacy-coverage-report --minimum-threshold=90
/legacy-coverage-report --show-uncovered --detailed
```

**What it does**:
- Generates comprehensive test coverage analysis
- Identifies uncovered critical business logic
- Prioritizes areas needing characterization tests
- Validates coverage meets 90% requirement

**Output**:
```
COVERAGE ANALYSIS:
- Overall Coverage: 73%
- Critical Path Coverage: 45% (INSUFFICIENT)
- Business Logic Coverage: 82%

COVERAGE GAPS IDENTIFIED:
- PaymentProcessor.js: 12% coverage (CRITICAL)
- UserManager.swift: 34% coverage (HIGH PRIORITY)
- DatabaseHelper.py: 0% coverage (BLOCKING)

RECOMMENDATION: Focus on critical paths first
```

---

### `/legacy-dependency-analysis`
**Purpose**: Map coupling and identify seam opportunities

**Usage**:
```bash
/legacy-dependency-analysis
/legacy-dependency-analysis --detect-cycles --identify-seams
/legacy-dependency-analysis --target="UserManager"
```

**What it does**:
- Maps all dependencies and coupling relationships
- Identifies circular dependencies
- Locates potential seams for dependency injection
- Analyzes external dependency usage

**Output**:
```
DEPENDENCY ANALYSIS:
- Total Dependencies: 47
- Circular Dependencies: 3 (REQUIRES ATTENTION)
- Tight Coupling Points: 8
- Seam Opportunities: 23

SEAM LOCATIONS IDENTIFIED:
- Constructor injection: 15 opportunities
- Method parameter injection: 8 opportunities
- Property injection: 12 opportunities
```

---

### `/legacy-antipattern-scan`
**Purpose**: Detect code quality issues and LLM antipatterns

**Usage**:
```bash
/legacy-antipattern-scan
/legacy-antipattern-scan --focus=god-objects --include-complexity
/legacy-antipattern-scan --custom-patterns="YourDomainPatterns"
```

**What it does**:
- Scans for god objects (>20 methods or >500 lines)
- Identifies long parameter lists and deep nesting
- Detects LLM-specific antipatterns
- Validates SOLID principle adherence

**Output**:
```
ANTIPATTERN SCAN RESULTS:
- God Objects: 2 detected
- Long Parameter Lists: 8 methods (>5 parameters)
- Deep Nesting: 15 methods (>4 levels)
- Duplicate Code: 23 blocks

PRIORITY FIXES:
1. UserManager.swift: God object (73 methods)
2. PaymentProcessor.js: Long parameter list (8 parameters)
3. DatabaseHelper.py: Deep nesting (6 levels)
```

---

### `/legacy-security-baseline`
**Purpose**: Document security posture and establish baseline

**Usage**:
```bash
/legacy-security-baseline
/legacy-security-baseline --comprehensive --include-dependencies
/legacy-security-baseline --owasp-compliance
```

**What it does**:
- Scans for known security vulnerabilities
- Identifies hardcoded secrets and credentials
- Analyzes input validation and sanitization
- Establishes security baseline for transformation

**Output**:
```
SECURITY BASELINE ESTABLISHED:
- Vulnerabilities Found: 12 (8 high, 4 medium)
- Hardcoded Secrets: 3 instances
- Input Validation: 67% of endpoints protected
- OWASP Top 10 Compliance: 6/10 categories

CRITICAL SECURITY ISSUES:
1. SQL injection in PaymentProcessor.js
2. Hardcoded API keys in config.js
3. Missing input validation in UserController.js
```

---

## 🛡️ Phase 2: Safety Infrastructure Commands (5 Commands)

**Goal**: Build comprehensive protection before making changes

### `/legacy-safety-net`
**Purpose**: Create characterization tests and safety infrastructure

**Usage**:
```bash
/legacy-safety-net
/legacy-safety-net --target-coverage=90 --include-performance
/legacy-safety-net --focus=business-logic
```

**What it does**:
- Generates characterization tests for existing behavior
- Creates golden master tests for complex outputs
- Establishes performance baselines
- Builds comprehensive safety infrastructure

**Output**:
```
SAFETY NET CREATION COMPLETE:
- Characterization Tests: 147 generated
- Golden Master Tests: 23 created
- Performance Baselines: 15 established
- Coverage Achieved: 92%

SAFETY NET VALIDATION:
✅ All existing behavior captured
✅ Performance baselines recorded
✅ Rollback procedures ready
✅ Ready for safe transformation
```

---

### `/legacy-seam-identify`
**Purpose**: Find safe dependency injection points

**Usage**:
```bash
/legacy-seam-identify
/legacy-seam-identify --focus=constructors --include-method-seams
/legacy-seam-identify --target="UserManager"
```

**What it does**:
- Analyzes code for natural seam points
- Identifies constructor injection opportunities
- Locates method parameter seams
- Maps property injection possibilities

**Output**:
```
SEAM IDENTIFICATION COMPLETE:
- Constructor Seams: 34 opportunities
- Method Parameter Seams: 67 opportunities  
- Property Seams: 23 opportunities
- Factory Seams: 12 opportunities

RECOMMENDED SEAM PRIORITIES:
1. UserManager constructor (15 dependencies)
2. PaymentProcessor.process() method (8 parameters)
3. DatabaseHelper properties (5 singletons)
```

---

### `/legacy-mock-generator`
**Purpose**: Create test doubles for external dependencies

**Usage**:
```bash
/legacy-mock-generator
/legacy-mock-generator --target-seams --include-stubs-spies
/legacy-mock-generator --auto-mock --validate-doubles
```

**What it does**:
- Generates mock objects for external dependencies
- Creates test stubs and spies
- Validates mock behavior matches real dependencies
- Integrates mocks with existing test infrastructure

**Output**:
```
MOCK GENERATION COMPLETE:
- Mock Objects: 28 created
- Test Stubs: 15 generated
- Spy Objects: 12 created
- Validation: 100% mocks verified

MOCK INTEGRATION:
✅ Database mocks functional
✅ Network service mocks ready
✅ File system mocks operational
✅ External API mocks validated
```

---

### `/legacy-rollback-prepare`
**Purpose**: Ensure every change can be immediately reversed

**Usage**:
```bash
/legacy-rollback-prepare
/legacy-rollback-prepare --enable-feature-flags --setup-monitoring
/legacy-rollback-prepare --emergency-procedures
```

**What it does**:
- Sets up feature flag infrastructure
- Creates automated rollback scripts
- Establishes monitoring and alerting
- Documents emergency procedures

**Output**:
```
ROLLBACK SYSTEM READY:
- Feature Flags: Implemented for all changes
- Rollback Scripts: Automated procedures created
- Monitoring: Real-time change tracking enabled
- Emergency Procedures: Documented and tested

ROLLBACK VALIDATION:
✅ <30 second rollback capability
✅ Feature flag instant disabling
✅ Monitoring alerts configured
✅ Emergency procedures tested
```

---

## 🔄 Phase 3: Safe Transformation Commands (10 Commands)

**Goal**: Safely modify and improve legacy code

### `/legacy-sprout`
**Purpose**: Add new functionality without changing existing code

**Usage**:
```bash
/legacy-sprout --feature="logging" --integration-point="PaymentProcessor"
/legacy-sprout --feature="analytics" --type="method"
/legacy-sprout --feature="fraud-detection" --type="class"
```

**What it does**:
- Creates new methods or classes for additional functionality
- Minimally integrates with existing legacy code
- Maintains 100% test coverage for new code
- Preserves existing behavior completely

**Output**:
```
SPROUT IMPLEMENTATION COMPLETE:
- New Code: 156 lines (100% test coverage)
- Integration Points: 2 minimal touchpoints
- Existing Code Changed: 0 lines
- Legacy Behavior: Preserved exactly

SPROUT VALIDATION:
✅ New functionality fully tested
✅ Zero impact on existing code
✅ Integration points verified
✅ Rollback capability confirmed
```

---

### `/legacy-extract-method`
**Purpose**: Reduce complexity by extracting focused methods

**Usage**:
```bash
/legacy-extract-method --target="UserManager.processUser"
/legacy-extract-method --target="PaymentProcessor.validateCard" --scope="minimal"
/legacy-extract-method --split-by-responsibility
```

**What it does**:
- Extracts complex methods into smaller, focused units
- Maintains identical behavior through characterization tests
- Reduces cyclomatic complexity
- Improves code readability and testability

**Output**:
```
METHOD EXTRACTION COMPLETE:
- Original Method: 234 lines reduced to 45 lines
- Extracted Methods: 4 focused methods created
- Complexity Reduction: 67% improvement
- Test Coverage: 100% maintained

EXTRACTION VALIDATION:
✅ All characterization tests pass
✅ Behavior preserved exactly
✅ Complexity significantly reduced
✅ Methods now independently testable
```

---

### `/legacy-extract-interface`
**Purpose**: Create testable abstractions for dependencies

**Usage**:
```bash
/legacy-extract-interface --target="DatabaseHelper"
/legacy-extract-interface --create-abstractions --dependency-inject
/legacy-extract-interface --interface-segregation
```

**What it does**:
- Creates interfaces for concrete dependencies
- Enables dependency injection patterns
- Improves testability through abstraction
- Follows interface segregation principle

**Output**:
```
INTERFACE EXTRACTION COMPLETE:
- Interfaces Created: 8 abstractions
- Dependency Injection: Enabled for 12 classes
- Testability: Significantly improved
- SOLID Compliance: Interface segregation achieved

INTERFACE VALIDATION:
✅ All implementations satisfy interfaces
✅ Dependency injection functional
✅ Test doubles work correctly
✅ Production code unchanged
```

---

### `/legacy-wrap-method`
**Purpose**: Add cross-cutting concerns transparently

**Usage**:
```bash
/legacy-wrap-method --target="APIService.fetch" --enhancement="logging"
/legacy-wrap-method --target="PaymentProcessor.process" --enhancement="monitoring"
/legacy-wrap-method --enhancement="caching,retry"
```

**What it does**:
- Adds functionality like logging, monitoring, caching
- Preserves original method signatures and behavior
- Uses decorator or wrapper patterns
- Maintains complete backward compatibility

**Output**:
```
METHOD WRAPPING COMPLETE:
- Enhanced Methods: 5 methods wrapped
- Cross-cutting Concerns: Added transparently
- Original Behavior: Preserved exactly
- Feature Flags: Enabled for safe deployment

WRAPPING VALIDATION:
✅ Original functionality unchanged
✅ Enhancements working correctly
✅ Performance impact minimal
✅ Rollback capability verified
```

---

### `/legacy-dependency-inject`
**Purpose**: Break hard dependencies through injection

**Usage**:
```bash
/legacy-dependency-inject --target="UserManager"
/legacy-dependency-inject --break-singletons --use-constructor
/legacy-dependency-inject --create-container
```

**What it does**:
- Converts singletons to injected dependencies
- Creates constructor injection patterns
- Builds dependency injection container
- Improves testability and modularity

**Output**:
```
DEPENDENCY INJECTION COMPLETE:
- Singleton Dependencies: 12 converted
- Constructor Injection: Implemented
- DI Container: Created and configured
- Testability: Dramatically improved

INJECTION VALIDATION:
✅ All dependencies injectable
✅ Test doubles work correctly
✅ Production behavior unchanged
✅ Memory usage optimized
```

---

### `/legacy-antipattern-fix`
**Purpose**: Systematically improve code quality

**Usage**:
```bash
/legacy-antipattern-fix --target="god-objects"
/legacy-antipattern-fix --fix="long-parameter-lists" --refactor-safe
/legacy-antipattern-fix --comprehensive --priority="high"
```

**What it does**:
- Fixes god objects through systematic decomposition
- Reduces long parameter lists using objects
- Eliminates deep nesting through extraction
- Improves SOLID principle adherence

**Output**:
```
ANTIPATTERN FIX COMPLETE:
- God Objects: 2 decomposed into 8 focused classes
- Long Parameter Lists: 8 methods refactored
- Deep Nesting: 15 methods simplified
- SOLID Compliance: Significantly improved

ANTIPATTERN VALIDATION:
✅ All characterization tests pass
✅ Complexity metrics improved
✅ Maintainability increased
✅ Performance maintained
```

---

### `/legacy-parallel-change`
**Purpose**: Gradual migration for major changes

**Usage**:
```bash
/legacy-parallel-change --old="LegacyPaymentProcessor" --new="SecurePaymentProcessor"
/legacy-parallel-change --migration-percentage=25
/legacy-parallel-change --comparison-mode --validate-results
```

**What it does**:
- Runs old and new implementations in parallel
- Gradually migrates traffic to new implementation
- Compares results for validation
- Enables safe, gradual migration

**Output**:
```
PARALLEL CHANGE SETUP:
- Old Implementation: Preserved and functional
- New Implementation: Ready for gradual migration
- Traffic Split: 25% to new, 75% to old
- Result Comparison: Enabled for validation

PARALLEL VALIDATION:
✅ Both implementations functional
✅ Traffic splitting working
✅ Result comparison operational
✅ Rollback capability instant
```

---

### `/legacy-characterize-behavior`
**Purpose**: Document and test existing behavior exactly

**Usage**:
```bash
/legacy-characterize-behavior --target="PaymentProcessor"
/legacy-characterize-behavior --include-bugs --golden-master
/legacy-characterize-behavior --comprehensive --all-methods
```

**What it does**:
- Creates tests documenting current behavior
- Captures existing bugs and quirks
- Generates golden master tests
- Provides safety net for refactoring

**Output**:
```
BEHAVIOR CHARACTERIZATION COMPLETE:
- Characterization Tests: 89 tests created
- Current Behavior: Documented exactly
- Golden Master Tests: 15 complex outputs captured
- Bug Preservation: 7 existing bugs documented

CHARACTERIZATION VALIDATION:
✅ All current behavior captured
✅ Tests provide safety net
✅ Bugs documented (not fixed)
✅ Ready for safe refactoring
```

---

### `/legacy-rollback-test`
**Purpose**: Validate rollback procedures work correctly

**Usage**:
```bash
/legacy-rollback-test --dry-run
/legacy-rollback-test --full-test --validate-recovery
/legacy-rollback-test --emergency-simulation
```

**What it does**:
- Tests rollback procedures without actual rollback
- Validates recovery mechanisms work
- Simulates emergency rollback scenarios
- Ensures rollback capability is reliable

**Output**:
```
ROLLBACK TEST COMPLETE:
- Dry Run: Successful simulation
- Recovery Time: 23 seconds (within 30s target)
- Emergency Procedures: Validated
- Rollback Reliability: 100% success rate

ROLLBACK VALIDATION:
✅ Rollback procedures functional
✅ Recovery time acceptable
✅ Emergency procedures tested
✅ Confidence in rollback capability
```

---

### `/legacy-assess`
**Purpose**: Comprehensive legacy code assessment

**Usage**:
```bash
/legacy-assess
/legacy-assess --comprehensive --all-checks
/legacy-assess --compare-before-after
```

**What it does**:
- Runs complete assessment across all dimensions
- Combines risk, coverage, dependencies, and security
- Generates comprehensive transformation plan
- Provides go/no-go decision for transformation

**Output**:
```
COMPREHENSIVE ASSESSMENT COMPLETE:
- Overall Health Score: 73/100
- Transformation Readiness: PROCEED WITH CAUTION
- Risk Level: MEDIUM
- Required Safety Net: COMPREHENSIVE

ASSESSMENT SUMMARY:
- Risk Analysis: 3 high-risk components identified
- Coverage Analysis: 67% current, 90% target
- Dependency Analysis: 5 circular dependencies
- Security Analysis: 8 vulnerabilities found
- Antipattern Analysis: 12 issues detected

RECOMMENDATION: Build comprehensive safety net before transformation
```

---

## ✅ Phase 4: Quality Validation Commands (4 Commands)

**Goal**: Ensure transformation effectiveness and quality

### `/legacy-validate`
**Purpose**: Comprehensive validation of transformation results

**Usage**:
```bash
/legacy-validate
/legacy-validate --comprehensive --all-checks
/legacy-validate --emergency-mode --quick-check
```

**What it does**:
- Validates all characterization tests pass
- Checks test coverage meets requirements
- Verifies performance baselines maintained
- Confirms security baseline not degraded

**Output**:
```
VALIDATION COMPLETE:
✅ Characterization Tests: 147/147 passing
✅ Test Coverage: 93% (exceeds 90% requirement)
✅ Performance: No regression detected
✅ Security: Baseline maintained
✅ Integration: All systems functional

TRANSFORMATION STATUS: SUCCESSFUL
Ready for production deployment
```

---

### `/legacy-mutation-test`
**Purpose**: Validate test effectiveness through mutation testing

**Usage**:
```bash
/legacy-mutation-test
/legacy-mutation-test --target="PaymentProcessor" --comprehensive
/legacy-mutation-test --score-threshold=90
```

**What it does**:
- Introduces code mutations to test test quality
- Validates tests catch actual bugs
- Measures test effectiveness beyond coverage
- Identifies weak spots in test suite

**Output**:
```
MUTATION TESTING COMPLETE:
- Mutations Generated: 234
- Mutations Killed: 211 (90% kill rate)
- Test Effectiveness: EXCELLENT
- Weak Spots: 3 areas identified

MUTATION VALIDATION:
✅ Test suite quality high
✅ 90% mutation kill rate achieved
✅ Bug detection capability strong
✅ Test improvements recommended for 3 areas
```

---

### `/legacy-property-test`
**Purpose**: Verify algorithmic properties and invariants

**Usage**:
```bash
/legacy-property-test --target="SortingAlgorithm"
/legacy-property-test --mathematical-properties
/legacy-property-test --invariant-checking
```

**What it does**:
- Tests mathematical properties of algorithms
- Validates invariants hold under all conditions
- Generates comprehensive test cases
- Provides high confidence in correctness

**Output**:
```
PROPERTY TESTING COMPLETE:
- Properties Tested: 12 algorithmic properties
- Invariants Verified: 8 system invariants
- Test Cases Generated: 10,000 cases
- Violations Found: 0

PROPERTY VALIDATION:
✅ All mathematical properties hold
✅ System invariants maintained
✅ Edge cases handled correctly
✅ High confidence in correctness
```

---

### `/legacy-security-test-generate`
**Purpose**: Generate comprehensive security tests

**Usage**:
```bash
/legacy-security-test-generate
/legacy-security-test-generate --owasp-top-10 --comprehensive
/legacy-security-test-generate --penetration-testing
```

**What it does**:
- Generates security test cases for all endpoints
- Tests for OWASP Top 10 vulnerabilities
- Creates penetration testing scenarios
- Validates security improvements

**Output**:
```
SECURITY TEST GENERATION COMPLETE:
- Security Tests: 156 tests generated
- OWASP Coverage: 10/10 categories tested
- Penetration Tests: 23 scenarios created
- Vulnerability Tests: 45 specific tests

SECURITY VALIDATION:
✅ All security tests pass
✅ OWASP compliance verified
✅ Penetration tests successful
✅ Security posture improved
```

---

## 🔍 Command Usage Patterns

### Quick Reference by Use Case

**Starting a new legacy transformation:**
```bash
# Phase 1: Assessment
/legacy-assess-risk
/legacy-coverage-report
/legacy-dependency-analysis
/legacy-antipattern-scan
/legacy-security-baseline

# Phase 2: Safety Net
/legacy-safety-net
/legacy-seam-identify
/legacy-mock-generator
/legacy-rollback-prepare
```

**Adding new functionality safely:**
```bash
# Use sprouting for new features
/legacy-sprout --feature="new-feature" --type="method"
/legacy-validate
```

**Reducing complexity of existing code:**
```bash
# Extract methods to reduce complexity
/legacy-extract-method --target="ComplexClass.hugeMethod"
/legacy-validate
```

**Improving testability:**
```bash
# Break dependencies and create abstractions
/legacy-extract-interface --target="DatabaseService"
/legacy-dependency-inject --target="UserManager"
/legacy-validate
```

**Major architectural changes:**
```bash
# Use parallel change for gradual migration
/legacy-parallel-change --old="LegacyService" --new="ModernService"
/legacy-validate
```

**Continuous quality improvement:**
```bash
# Regular validation and testing
/legacy-mutation-test
/legacy-property-test
/legacy-security-test-generate
```

### Error Handling and Rollback

**If any command fails:**
```bash
# Emergency rollback
/legacy-rollback-test --dry-run
./rollback.sh
/legacy-validate --emergency-mode
```

**If tests start failing:**
```bash
# Check characterization tests
/legacy-characterize-behavior --refresh
/legacy-validate
```

### Performance Optimization

**For faster execution:**
```bash
# Use incremental mode
/legacy-assess --incremental --since="last-commit"
/legacy-validate --quick-check
```

**For comprehensive analysis:**
```bash
# Full analysis mode
/legacy-assess --comprehensive --all-checks
/legacy-validate --comprehensive
```

---

## 🎯 Success Metrics

### Command Completion Indicators

**Phase 1 Complete:** All assessment commands show "READY FOR TRANSFORMATION"
**Phase 2 Complete:** Test coverage ≥90% and all safety infrastructure operational
**Phase 3 Complete:** Transformation goals achieved with all tests passing
**Phase 4 Complete:** All validation commands show "SUCCESSFUL"

### Quality Gates

- **Test Coverage**: Must maintain ≥90% throughout transformation
- **Characterization Tests**: Must pass 100% before and after changes
- **Performance**: No regression >10% in critical paths
- **Security**: Baseline must be maintained or improved

---

**Remember**: This framework prioritizes safety over speed. Every command is designed to preserve existing functionality while gradually improving code quality, security, and maintainability. Trust the process and the safety infrastructure it provides.