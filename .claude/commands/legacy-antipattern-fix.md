---
allowed-tools: ["Bash", "Glob", "Grep", "LS", "Read", "Write", "Edit", "MultiEdit"]
description: "Systematically eliminate identified antipatterns while maintaining all existing functionality through comprehensive safety testing"
---

# Legacy Antipattern Fix - Systematic Code Quality Improvement

## Dynamic Context Gathering

!find . -name "*.py" -o -name "*.js" -o -name "*.java" -o -name "*.swift" -o -name "*.ts" | xargs wc -l | sort -nr | head -10

!grep -r "class.*Manager\|class.*Helper\|class.*Utility" . --include="*.py" --include="*.js" --include="*.java" --include="*.swift" --include="*.ts" | head -10

!git log --oneline -5 && echo "\n=== Recent commits ==="

## File References

@antipattern-analysis.json @god-objects.json @characterization-tests/ @coverage-report.json

**Command**: `/legacy-antipattern-fix`  
**Phase**: Transformation  
**Coverage Requirement**: 90%+ coverage + antipattern analysis complete (blocks without this)  
**Risk Level**: Medium (systematic refactoring with comprehensive safety net)

## Objective

Systematically eliminate identified antipatterns (god objects, long methods, high coupling) and LLM-specific issues while maintaining all existing functionality through comprehensive characterization testing and immediate rollback capability.

## Context

This command uses the results from `/legacy-antipattern-scan` to systematically fix code quality issues that impede maintenance and AI-assisted development. It follows Michael Feathers' principles by ensuring safety through testing before making any modifications.

## Antipattern Fix Strategy Tasks

1. **Prerequisite Validation**:
   - Verify that 90%+ test coverage requirement has been met and antipattern analysis is complete
   - Confirm that comprehensive characterization tests are in place for all components to be modified
   - Validate that rollback procedures are prepared and tested for immediate recovery
   - Check that dependency injection and interface extraction have been completed where needed

2. **Antipattern Prioritization and Sequencing**:
   - **Critical Priority**: Fix god objects >30 methods, force unwrapping in business logic, security vulnerabilities
   - **High Priority**: Fix long methods >100 lines, large files >1000 lines, high parameter counts >5
   - **Medium Priority**: Fix SOLID principle violations, dependency injection opportunities, naming issues
   - **Low Priority**: Fix minor code smells, documentation gaps, performance optimizations

3. **Fix Strategy Planning**:
   - **Decomposition Strategy**: Plan how to break down god objects into focused, single-responsibility classes
   - **Method Extraction Planning**: Identify logical boundaries for extracting methods from long functions
   - **Coupling Reduction Strategy**: Plan dependency injection and interface extraction to reduce coupling
   - **Safety Validation**: Ensure each fix maintains existing behavior through comprehensive testing

4. **LLM-Specific Antipattern Resolution**:
   - **Context Pollution Fixes**: Split massive files >1000 lines that overwhelm LLM context windows
   - **Naming Clarity**: Replace ambiguous variable names (temp, data, obj) with clear, descriptive names
   - **Complexity Reduction**: Reduce deep nesting >4 levels that confuses LLM understanding
   - **Abstraction Separation**: Separate mixed abstraction levels in methods for clearer LLM comprehension

## God Object Decomposition Tasks

### God Object Analysis and Decomposition

1. **Responsibility Analysis**:
   - Identify distinct responsibilities within god objects using Single Responsibility Principle
   - Group related methods and data that belong together in cohesive classes
   - Analyze dependencies between different responsibility areas
   - Plan extraction sequence to minimize disruption and maintain working state

2. **Class Extraction Implementation**:
   - Create new focused classes for each identified responsibility
   - Move related methods and data to appropriate new classes
   - Implement proper delegation between classes to maintain existing behavior
   - Add comprehensive tests for new classes to ensure correct behavior

3. **Reference Update and Integration**:
   - Update all references to moved methods and data throughout the codebase
   - Implement composition or aggregation patterns to maintain object relationships
   - Add factory methods or dependency injection to create and wire new class instances
   - Validate that all existing functionality continues to work correctly

### Method Decomposition and Extraction

1. **Long Method Analysis**:
   - Identify logical blocks within long methods that can be extracted
   - Analyze variable usage and scope to determine extraction boundaries
   - Plan method signatures for extracted methods to minimize parameter passing
   - Ensure extracted methods have clear, single responsibilities

2. **Method Extraction Implementation**:
   - Extract logical blocks into well-named, focused methods
   - Implement proper parameter passing and return value handling
   - Maintain exact behavior preservation through careful variable scoping
   - Add comprehensive tests for extracted methods to validate functionality

## Framework-Specific Antipattern Fixes

### iOS/Swift Antipattern Fixes
- Decompose massive View Controllers using delegation and child view controller patterns
- Replace force unwrapping with safe optional handling and guard statements
- Implement protocol-based abstractions to reduce concrete class dependencies
- Use Swift access control to properly encapsulate extracted class responsibilities

### JavaScript/Node.js Antipattern Fixes
- Split large modules into focused, single-responsibility modules
- Replace callback hell with Promise chains or async/await patterns
- Implement proper error handling instead of silent failures
- Use ES6+ features to improve code clarity and reduce boilerplate

### Python Antipattern Fixes
- Decompose large classes using composition and mixin patterns
- Replace bare except clauses with specific exception handling
- Add type hints to improve code clarity and IDE support
- Use Python decorators and context managers appropriately

### Java Antipattern Fixes
- Decompose god objects using composition and interface-based design
- Replace large switch statements with polymorphism or strategy patterns
- Implement proper exception handling instead of exception swallowing
- Use appropriate access modifiers and encapsulation

## Coupling Reduction and Dependency Management

### Dependency Injection Integration

1. **Hard Dependency Replacement**:
   - Replace singleton usage with dependency injection at identified seams
   - Convert static method calls to interface-based dependency injection
   - Implement factory patterns for complex object creation
   - Add configuration-based dependency wiring for flexibility

2. **Interface-Based Abstraction**:
   - Use previously extracted interfaces to reduce coupling to concrete implementations
   - Implement adapter patterns to integrate with external dependencies
   - Add abstraction layers for system resources and external services
   - Create clean architectural boundaries through proper interface design

### SOLID Principle Implementation

1. **Single Responsibility Enforcement**:
   - Ensure each class and method has a single, well-defined responsibility
   - Split classes that handle multiple concerns into focused components
   - Extract cross-cutting concerns into separate, reusable components
   - Validate responsibility separation through comprehensive testing

2. **Open/Closed Principle Implementation**:
   - Replace large conditional statements with polymorphism or strategy patterns
   - Implement extension points for new functionality without modifying existing code
   - Use configuration and dependency injection to enable behavior modification
   - Add plugin or extension patterns where appropriate

## Quality Validation and Testing

### Comprehensive Testing Strategy

1. **Characterization Test Validation**:
   - Run all existing characterization tests to ensure behavior preservation
   - Add additional characterization tests for complex refactoring scenarios
   - Validate edge cases and error conditions continue to work correctly
   - Test performance characteristics to ensure no regressions

2. **New Component Testing**:
   - Create comprehensive unit tests for all newly extracted classes and methods
   - Implement integration tests for complex refactoring involving multiple components
   - Add property-based tests for complex algorithms and business logic
   - Validate thread safety and concurrency behavior where applicable

### Code Quality Metrics Validation

1. **Complexity Metrics**: Verify that cyclomatic complexity and method length are within acceptable limits
2. **Coupling Metrics**: Validate that coupling between components has been reduced
3. **Cohesion Metrics**: Ensure that new classes and methods have high cohesion
4. **Maintainability Metrics**: Verify that maintainability index has improved

## Antipattern Fix Validation

### Before/After Comparison

1. **Antipattern Count Reduction**: Measure reduction in identified antipatterns
2. **Code Quality Improvement**: Validate improvement in static analysis metrics
3. **Testability Enhancement**: Verify that code is more testable and mockable
4. **LLM Comprehension**: Ensure code is more understandable for AI-assisted development

### Long-term Quality Assurance

1. **Maintenance Burden Reduction**: Validate that code is easier to understand and modify
2. **Bug Proneness Reduction**: Ensure that antipattern fixes reduce likelihood of bugs
3. **Development Velocity**: Verify that code changes can be made more safely and quickly
4. **Team Understanding**: Ensure team can understand and work with refactored code effectively

## Rollback and Recovery Procedures

### Immediate Rollback Triggers
- Any characterization test failures after antipattern fix implementation
- Performance degradation or memory issues introduced by refactoring
- Compilation errors or runtime exceptions introduced by code changes
- Integration failures with existing systems or external dependencies

### Rollback Execution
1. **Git-Based Rollback**: Use version control to restore previous working state
2. **Component-Level Rollback**: Roll back individual antipattern fixes that cause issues
3. **Dependency Restoration**: Restore original dependency relationships if injection causes problems
4. **Validation Testing**: Run comprehensive tests to ensure successful rollback

## Success Criteria

- Identified antipatterns systematically eliminated with measurable quality improvement
- All existing behavior preserved with 100% characterization test validation
- Code quality metrics improved (reduced complexity, coupling, increased cohesion)
- LLM-specific issues resolved to improve AI-assisted development
- Maintainability and testability significantly enhanced
- Complete rollback capability maintained throughout antipattern fix process

## Integration

- Documents antipattern fix completion status and quality improvements
- Provides foundation for ongoing code quality maintenance and improvement
- Enables more effective AI-assisted development through clearer code structure
- Establishes quality standards and patterns for future development

## Rollback

Antipattern fixes can be selectively or completely reversed if issues arise:
1. **Selective Rollback**: Reverse specific antipattern fixes that cause problems
2. **Complete Restoration**: Restore original code structure if extensive issues occur
3. **Quality Validation**: Verify that rollback restores original functionality
4. **Issue Analysis**: Document antipattern fix failures for future improvement attempts