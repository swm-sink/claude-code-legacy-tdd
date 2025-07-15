---
allowed-tools: ["Bash", "Glob", "Grep", "LS", "Read", "Write", "Edit", "MultiEdit"]
description: "Safely extract methods from large, complex functions to improve readability while preserving all existing behavior"
---

# Legacy Method Extraction - Safe Refactoring Through Method Decomposition

## Dynamic Context Gathering

!find . -name "*.py" -o -name "*.js" -o -name "*.java" -o -name "*.swift" -o -name "*.ts" | xargs grep -A 50 "def \|function \|public \|private " | grep -c "^--" && echo "Methods found"

!find . -name "*.py" -o -name "*.js" -o -name "*.java" -o -name "*.swift" -o -name "*.ts" | xargs wc -l | sort -nr | head -5

!git log --oneline -3 && echo "\n=== Recent commits ==="

## File References

@characterization-tests/ @coverage-report.json @safety-net-config.json @rollback-procedures.md

**Command**: `/legacy-extract-method`  
**Phase**: Transformation  
**Coverage Requirement**: 90% coverage + safety net complete (Google exemplary standard - blocks without this)  
**Risk Level**: Medium (modifies existing code with comprehensive safety net)

## Objective

Safely extract methods from large, complex functions to improve readability, testability, and maintainability while preserving all existing behavior through comprehensive characterization testing and immediate rollback capability.

## Context

Method extraction is one of the safest refactoring techniques in Michael Feathers' arsenal. This command identifies long methods, extracts focused functionality into new methods, and maintains 100% behavioral preservation through characterization tests and validation.

## Method Extraction Analysis Tasks

1. **Prerequisite Validation**:
   - Verify that 90%+ test coverage requirement has been met and safety net infrastructure is complete
   - Confirm that characterization tests are in place and passing for target components
   - Validate that rollback procedures are prepared and tested for immediate recovery
   - Check that mock infrastructure and dependency injection seams are ready

2. **Target Method Identification**:
   - **Long Method Detection**: Identify methods exceeding 50 lines that are candidates for extraction
   - **Complexity Analysis**: Assess cyclomatic complexity and identify complex logical blocks within methods
   - **Business Logic Separation**: Find mixed abstraction levels where business logic is intertwined with infrastructure concerns
   - **Code Duplication Identification**: Locate repeated code patterns that can be extracted into reusable methods

3. **Extraction Opportunity Analysis**:
   - **Logical Cohesion Assessment**: Identify code blocks that perform single, focused operations
   - **Variable Usage Analysis**: Map local variable usage to determine extraction boundaries and parameter requirements
   - **Dependency Mapping**: Understand what external dependencies and state the extracted method will need
   - **Side Effect Identification**: Catalog all side effects (state changes, I/O operations, external calls) within extraction candidates

4. **Safety-First Extraction Planning**:
   - **Characterization Test Enhancement**: Create additional characterization tests specifically for extraction validation
   - **Extraction Sequence Planning**: Determine order of extractions to minimize risk and maintain working state
   - **Parameter Design**: Plan extracted method signatures to minimize coupling while preserving functionality
   - **Naming Strategy**: Develop clear, intention-revealing names for extracted methods

## Method Extraction Implementation Tasks

### Pre-Extraction Safety Validation

1. **Enhanced Characterization Testing**:
   - Create comprehensive tests that capture the behavior of the target method before extraction
   - Include edge cases, error conditions, and state changes in characterization tests
   - Document any side effects, I/O operations, or external dependencies in the tests
   - Validate that characterization tests are reliable and catch any behavioral changes

2. **Extraction Boundary Analysis**:
   - Identify the exact lines of code to extract while maintaining logical cohesion
   - Map all local variables, parameters, and return values that cross extraction boundaries
   - Analyze variable scoping and lifetime to ensure extracted method has proper access
   - Plan for any temporary variables or state that needs to be passed between methods

### Safe Method Extraction Process

1. **Extract Method with TDD Approach**:
   - Create the new extracted method with appropriate signature and parameter list
   - Implement the extracted method by moving the identified code block while preserving exact behavior
   - Update the original method to call the new extracted method with proper parameters
   - Ensure that all variable scoping and return value handling is preserved

2. **Immediate Validation and Testing**:
   - Run all characterization tests to verify that behavior is exactly preserved
   - Execute comprehensive test suite to ensure no regressions are introduced
   - Validate that all edge cases and error conditions continue to work correctly
   - Test performance to ensure no significant degradation from method extraction

3. **Incremental Extraction Strategy**:
   - Extract one method at a time to maintain working state throughout the process
   - Validate each extraction completely before proceeding to the next extraction
   - Use feature flags or conditional compilation if available to enable rollback
   - Document each extraction step for audit trail and rollback reference

## Framework-Specific Method Extraction

### iOS/Swift Method Extraction
- Extract methods using Swift function syntax with appropriate access control
- Handle Swift optionals and error throwing in extracted method signatures
- Use protocol extensions and generics where appropriate for extracted utility methods
- Maintain proper memory management and avoid retain cycles in extracted methods

### JavaScript/Node.js Method Extraction
- Extract methods as function expressions or arrow functions based on context
- Handle JavaScript closures and variable scoping properly in extracted methods
- Maintain proper `this` binding and context in extracted class methods
- Use ES6+ features appropriately (destructuring, default parameters) in extracted methods

### Python Method Extraction
- Extract methods following Python naming conventions and PEP 8 guidelines
- Handle Python decorators and maintain proper function signature preservation
- Use appropriate parameter handling (args, kwargs) when extracting flexible methods
- Maintain proper exception handling and docstring documentation in extracted methods

### Java Method Extraction
- Extract methods with appropriate access modifiers and exception declarations
- Handle Java generics and maintain type safety in extracted method signatures
- Use Java annotations appropriately for extracted methods (Override, SuppressWarnings)
- Maintain proper exception handling and follow Java coding conventions

## Method Extraction Validation

### Behavioral Preservation Validation
1. **Comprehensive Test Execution**: Run all existing tests to ensure no behavioral changes
2. **Characterization Test Validation**: Verify extracted functionality produces identical outputs
3. **Edge Case Testing**: Test boundary conditions, error scenarios, and unusual inputs
4. **Integration Testing**: Ensure extracted methods work correctly with rest of system

### Code Quality Assessment
1. **Readability Improvement**: Verify that extracted methods improve code readability and maintainability
2. **Single Responsibility**: Ensure extracted methods follow single responsibility principle
3. **Naming Quality**: Validate that extracted method names clearly communicate intent
4. **Parameter Appropriateness**: Ensure extracted method parameters are reasonable and necessary

### Performance and Security Validation
1. **Performance Testing**: Verify that method extraction doesn't introduce performance regressions
2. **Security Assessment**: Ensure extracted methods don't introduce security vulnerabilities
3. **Memory Usage**: Validate that extracted methods don't cause memory leaks or excessive allocation
4. **Thread Safety**: For concurrent code, ensure extracted methods maintain thread safety

## Rollback and Recovery Procedures

### Immediate Rollback Triggers
- Any characterization test failures after method extraction
- Performance degradation exceeding 5% of baseline
- Any compilation errors or runtime exceptions introduced
- Test coverage dropping below 90% requirement

### Rollback Execution
1. **Git-Based Rollback**: Use git revert to immediately restore previous working state
2. **Feature Flag Rollback**: If using feature flags, disable extracted functionality
3. **Manual Rollback**: Step-by-step reversal of extraction changes if needed
4. **Validation After Rollback**: Run full test suite to confirm successful rollback

## Success Criteria

- Long methods successfully decomposed into focused, single-responsibility methods
- All existing behavior preserved with 100% characterization test validation
- Code readability and maintainability improved through better method organization
- 90%+ test coverage maintained throughout extraction process
- Complete rollback capability available for any extraction that causes issues
- Performance and security characteristics preserved or improved

## Integration

- Documents method extraction completion status and refactoring improvements
- Maintains comprehensive test coverage and safety net throughout transformation
- Provides foundation for further refactoring by improving method-level testability
- Establishes pattern for safe code improvement through incremental refactoring

## Rollback

Method extraction can be immediately reversed if any issues arise:
1. **Git Revert**: Complete reversal to pre-extraction state with single git command
2. **Test Validation**: Run characterization tests to verify successful rollback
3. **Issue Analysis**: Document extraction failure causes for future improvement
4. **Alternative Approach**: Plan different extraction strategy if original approach failed