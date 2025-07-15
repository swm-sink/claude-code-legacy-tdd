---
allowed-tools: ["Bash", "Glob", "Grep", "LS", "Read"]
description: "Generate comprehensive test coverage report for legacy codebase baseline and gap analysis"
---

# Legacy Code Coverage Analysis

## Dynamic Context Gathering

!find . -name "*test*" -o -name "*spec*" -o -name "test_*" -o -name "*_test.*" | head -20

!find . -name "coverage*" -o -name ".coverage" -o -name "*.lcov" -o -name "coverage.xml" | head -10

!ls -la | grep -E "(jest|pytest|mocha|rspec|gradle|maven|xcode)" || echo "No common test runners found"

## File References

@jest.config.js @pytest.ini @coverage.xml @.coveragerc @package.json @pom.xml @build.gradle

Perform comprehensive test coverage analysis for this legacy codebase and establish the 90%+ coverage requirement that must be met before any transformation work begins.

## Coverage Analysis Tasks

1. **Current Coverage Assessment**:
   - Run existing test suite and analyze coverage results
   - Identify which files/classes have zero test coverage
   - Find critical business logic components that lack tests
   - Analyze coverage by component type (models, services, controllers, utilities)

2. **Critical Gap Identification**:
   - Focus on business-critical components (payment, authentication, data processing)
   - Identify public APIs and interfaces that need coverage
   - Find complex algorithms and business rules without tests
   - Locate error handling paths that are untested

3. **Test Type Analysis**:
   - **Unit Tests**: Component-level testing coverage
   - **Integration Tests**: API and service integration coverage  
   - **Characterization Tests**: Legacy behavior preservation tests
   - **End-to-End Tests**: Critical user journey coverage

4. **Coverage Quality Assessment**:
   - Identify tests that exist but don't actually validate behavior
   - Find tests that only cover happy paths (missing edge cases)
   - Analyze test effectiveness for catching regressions
   - Review test maintainability and clarity

## 90% Coverage Requirement

This framework requires **90% minimum test coverage** before ANY transformation work can begin. This is not just line coverage, but meaningful behavioral coverage that:

- **Preserves existing functionality** during refactoring
- **Catches regressions** when changes are made
- **Documents expected behavior** for legacy components
- **Enables safe transformation** with confidence

## Coverage Strategy Recommendations

### For Each Uncovered Component:
1. **Characterization Tests First**: Document actual current behavior
2. **Edge Case Coverage**: Test error conditions and boundary cases  
3. **Integration Points**: Test how components interact with dependencies
4. **Business Logic**: Ensure all business rules are covered

### Priority Order:
1. **Critical Business Logic** (payment, auth, data) - 100% coverage required
2. **Public APIs and Interfaces** - 95% coverage required
3. **Core Application Logic** - 90% coverage required
4. **Utility and Helper Functions** - 85% coverage minimum

## Framework Integration

This analysis establishes:
- **Blocking mechanism**: Transformation commands will refuse to run below 90% coverage
- **Characterization test requirements**: What needs golden master tests
- **Seam identification input**: Where dependency injection can happen safely
- **Rollback validation**: Tests that verify rollback success

## Output Requirements

Create a detailed coverage report that includes:

### Current State Summary
- Overall coverage percentage and line/branch coverage
- List of completely uncovered files with business criticality assessment
- Coverage gaps in critical business logic components

### Gap Analysis
- Specific methods/functions that need test coverage
- Recommended test types for each gap (unit, integration, characterization)
- Priority order for achieving 90% coverage

### Implementation Plan
- Step-by-step approach to reach 90% coverage
- Estimated effort for each component
- Dependencies between coverage tasks

Use your understanding of testing frameworks and coverage tools to provide specific, actionable guidance for this codebase.