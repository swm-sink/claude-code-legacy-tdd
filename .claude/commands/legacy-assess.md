# Legacy Code Assessment - Comprehensive Analysis

**Command**: `/legacy-assess`  
**Phase**: Initial Assessment  
**Coverage Requirement**: Current state analysis + 90% minimum target establishment

## Objective

Perform complete legacy codebase analysis combining risk assessment, test coverage analysis, dependency mapping, antipattern detection, and security baseline in a single comprehensive command.

## Context

This is the MANDATORY first command that must be run before any legacy code work. It establishes the complete picture of the codebase state and sets the 90%+ coverage requirements for all future work.

## Implementation

### Step 1: Risk Assessment Analysis
```bash
# Comprehensive complexity analysis
find . -name "*.swift" -exec wc -l {} \; | awk '{sum+=$1} END {print "Total Lines: " sum}'
find . -name "*.swift" -exec grep -c "class\|struct\|enum\|protocol" {} \; | awk '{sum+=$1} END {print "Total Types: " sum}'

# Critical risk patterns
echo "=== CRITICAL RISK ANALYSIS ==="
find . -name "*.swift" -exec grep -l "!" {} \; | wc -l | awk '{print "Force Unwrap Files: " $1}'
find . -name "*.swift" -exec grep -l "fatalError\|assert\|precondition" {} \; | wc -l | awk '{print "Crash Risk Files: " $1}'
find . -name "*.swift" -exec grep -l "try!" {} \; | wc -l | awk '{print "Force Try Files: " $1}'

# God object detection (classes with >20 methods)
echo "=== GOD OBJECT DETECTION ==="
find . -name "*.swift" -exec awk '/^class|^struct/ {class=$2} /func / {count++} /^}/ {if(count>20) print FILENAME":"class" has "count" methods"; count=0}' {} \;
```

### Step 2: Current Test Coverage Analysis
```bash
# Swift/iOS coverage analysis
if [ -f "*.xcworkspace" ] || [ -f "*.xcodeproj" ]; then
    echo "=== iOS PROJECT COVERAGE ANALYSIS ==="
    xcodebuild test -workspace *.xcworkspace -scheme * -destination 'platform=iOS Simulator,name=iPhone 15' -enableCodeCoverage YES 2>/dev/null || echo "Manual coverage analysis required"
fi

# Generic test file analysis
echo "=== CURRENT TEST COVERAGE ==="
TEST_FILES=$(find . -name "*Test*" -o -name "*test*" -o -name "*spec*" | wc -l)
SOURCE_FILES=$(find . -name "*.swift" -o -name "*.java" -o -name "*.js" -o -name "*.py" | grep -v -i test | wc -l)
echo "Test Files: $TEST_FILES"
echo "Source Files: $SOURCE_FILES"
COVERAGE_RATIO=$(echo "scale=2; $TEST_FILES / $SOURCE_FILES * 100" | bc -l 2>/dev/null || echo "0.0")
echo "Estimated Coverage: ${COVERAGE_RATIO}%"

if (( $(echo "$COVERAGE_RATIO < 90" | bc -l 2>/dev/null || echo "1") )); then
    echo "❌ COVERAGE INSUFFICIENT: Current $COVERAGE_RATIO% < Required 90%"
    echo "⚠️  TRANSFORMATION BLOCKED until 90%+ coverage achieved"
else
    echo "✅ COVERAGE SUFFICIENT: $COVERAGE_RATIO% >= Required 90%"
fi
```

### Step 3: Dependency and Architecture Analysis
```bash
echo "=== DEPENDENCY ANALYSIS ==="

# Import/dependency analysis
echo "External Dependencies:"
find . -name "*.swift" -exec grep -h "^import " {} \; | sort | uniq -c | sort -nr | head -10

# Circular dependency detection
echo "Potential Circular Dependencies:"
find . -name "*.swift" -exec grep -l "class\|struct" {} \; | head -20 | while read file; do
    classes=$(grep "class\|struct" "$file" | awk '{print $2}' | cut -d: -f1)
    echo "$file: $classes"
done

# Coupling analysis
echo "High Coupling Indicators:"
find . -name "*.swift" -exec grep -c "\.shared\|\.singleton\|\.instance" {} \; | grep -v ":0" | head -10
```

### Step 4: Antipattern and Code Quality Analysis
```bash
echo "=== ANTIPATTERN DETECTION ==="

# God object detection (detailed)
echo "God Objects (>20 methods):"
find . -name "*.swift" -exec awk 'BEGIN{methods=0; class=""} /^class |^struct / {if(methods>20 && class!="") print FILENAME":"class" ("methods" methods)"; class=$2; methods=0} /func / {methods++} END{if(methods>20) print FILENAME":"class" ("methods" methods)"}' {} \;

# Long method detection (>50 lines)
echo "Long Methods (>50 lines):"
find . -name "*.swift" -exec awk '/func / {start=NR; name=$2} /^    }/ {if(NR-start>50) print FILENAME":"name" ("NR-start" lines)"}' {} \;

# High parameter count (>5 parameters)
echo "High Parameter Count (>5):"
find . -name "*.swift" -exec grep -n "func.*(" {} \; | grep -E "\([^)]*,[^)]*,[^)]*,[^)]*,[^)]*," | head -10

# SOLID principle violations
echo "Single Responsibility Violations:"
find . -name "*.swift" -exec grep -l "Manager\|Handler\|Controller\|Service\|Helper\|Utility" {} \; | head -10
```

### Step 5: Security Baseline Analysis
```bash
echo "=== SECURITY BASELINE ==="

# Hardcoded secrets detection
echo "Potential Hardcoded Secrets:"
find . -name "*.swift" -exec grep -i "password\|secret\|key\|token\|api_key" {} \; | grep -v "//\|func\|var.*:" | head -5

# Unsafe network calls
echo "Unsafe Network Patterns:"
find . -name "*.swift" -exec grep -l "http://\|allowsArbitraryLoads\|NSAppTransportSecurity" {} \; | head -5

# Input validation gaps
echo "Input Validation Gaps:"
find . -name "*.swift" -exec grep -l "URLSession\|Alamofire" {} \; | xargs grep -L "guard\|validation\|sanitiz" | head -5

# Authentication weaknesses
echo "Authentication Patterns:"
find . -name "*.swift" -exec grep -n "auth\|login\|token\|session" {} \; | head -10
```

### Step 6: Comprehensive Assessment Summary
```bash
echo "=== LEGACY CODE ASSESSMENT SUMMARY ==="
echo "Generated: $(date)"
echo ""
echo "📊 QUANTITATIVE ANALYSIS:"
echo "- Total Source Files: $SOURCE_FILES"
echo "- Current Test Coverage: ${COVERAGE_RATIO}%"
echo "- Coverage Gap: $(echo "90 - $COVERAGE_RATIO" | bc -l)% (must reach 90%+)"
echo ""
echo "🚨 CRITICAL ISSUES:"
echo "- Force unwrapping files require immediate attention"
echo "- God objects need decomposition before transformation"
echo "- Security gaps require hardening"
echo ""
echo "📋 TRANSFORMATION READINESS:"
if (( $(echo "$COVERAGE_RATIO < 90" | bc -l 2>/dev/null || echo "1") )); then
    echo "❌ NOT READY: Coverage insufficient ($COVERAGE_RATIO% < 90%)"
    echo "📝 NEXT STEPS:"
    echo "1. Run /legacy-safety-net to achieve 90%+ coverage"
    echo "2. Address critical security issues"
    echo "3. Re-run /legacy-assess to verify readiness"
else
    echo "✅ READY: Coverage sufficient for safe transformation"
    echo "📝 NEXT STEPS:"
    echo "1. Use /legacy-sprout for new functionality"
    echo "2. Use /legacy-extract for refactoring"
    echo "3. Run /legacy-validate continuously"
fi
```

## Success Criteria
- Complete codebase analysis performed
- 90% coverage target established
- Critical risks identified and prioritized
- Security baseline documented
- Clear go/no-go decision provided

## Integration
- Updates `agent-comms/coordination.json` with assessment results
- Establishes coverage baseline for all future commands
- Blocks unsafe operations until coverage requirements met

## Rollback
Assessment is read-only and requires no rollback procedures.