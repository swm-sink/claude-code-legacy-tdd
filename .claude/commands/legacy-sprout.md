---
allowed-tools: ["Bash", "Glob", "Grep", "LS", "Read", "Write", "Edit", "MultiEdit"]
description: "Safely add new functionality using sprout method and sprout class techniques without modifying existing legacy code"
---

# Legacy Sprout - Safe New Functionality Addition

## Dynamic Context Gathering

!find . -name "*.py" -o -name "*.js" -o -name "*.java" -o -name "*.swift" -o -name "*.ts" | xargs grep -l "class\|def\|function" | head -20

!find . -name "*test*" -o -name "*spec*" | wc -l && echo "Current test files"

!git status --porcelain && git log --oneline -3

## File References

@characterization-tests/ @package.json @requirements.txt @pom.xml @coverage-report.json

**Command**: `/legacy-sprout`  
**Phase**: Transformation  
**Coverage Requirement**: Maintain 90% coverage + 100% coverage for new code (Google exemplary standard - blocks without this)  
**Risk Level**: Low (adds new code without modifying existing legacy code)

## Objective

Safely add new functionality to legacy systems using sprout method and sprout class techniques without modifying existing legacy code, maintaining full test coverage and providing immediate rollback capability.

## Context

This command implements Michael Feathers' safest transformation techniques - adding new functionality through "sprouting" rather than modifying existing code. All new code follows Test-Driven Development with 100% coverage while preserving existing behavior completely.

## Sprouting Strategy Analysis Tasks

1. **Prerequisite Validation**:
   - Verify that 90%+ test coverage requirement has been met from `/legacy-coverage-report`
   - Confirm that characterization tests are in place from `/legacy-characterize-behavior`
   - Validate that safety net infrastructure is complete from `/legacy-safety-net`
   - Check that rollback procedures are prepared and tested

2. **Integration Point Analysis**:
   - **Target Component Assessment**: Analyze the existing component where new functionality needs to be integrated
   - **Complexity Evaluation**: Assess current component complexity (method count, line count, responsibilities)
   - **Sprouting Strategy Selection**: Determine whether to use sprout method or sprout class approach
   - **Integration Approach**: Plan minimal integration touchpoints that preserve existing functionality

3. **Sprouting Strategy Selection**:
   - **Sprout Method Criteria**: Simple features that can be added as new methods to existing classes (< 15 methods, < 300 lines)
   - **Sprout Class Criteria**: Complex features that warrant new classes to avoid god object antipatterns
   - **Risk Assessment**: Evaluate integration complexity and potential impact on existing code
   - **Rollback Planning**: Ensure chosen approach allows for complete rollback via feature flags

## Sprout Method Implementation Tasks

### For Simple Features Added as New Methods

1. **Test-First Development**:
   - **Create Test Structure**: Set up comprehensive test files for sprouted methods with 100% coverage requirement
   - **Write Failing Tests**: Implement tests for all functionality including edge cases and error scenarios
   - **Test Edge Cases**: Cover boundary conditions, invalid inputs, and error handling comprehensively
   - **Performance Testing**: Include performance tests to ensure sprouted functionality meets requirements

2. **Implementation with TDD Cycle**:
   - **RED Phase**: Verify tests fail appropriately before implementation
   - **GREEN Phase**: Implement sprouted method with minimal functionality to pass tests
   - **REFACTOR Phase**: Optimize implementation while maintaining test coverage and functionality
   - **Integration**: Add minimal, feature-flagged integration with existing workflow

3. **Sprouted Method Integration**:
   - **Minimal Coupling**: Add sprouted method to existing class without modifying existing methods
   - **Feature Flag Integration**: Use feature flags to control when sprouted functionality is active
   - **Optional Execution**: Ensure existing workflows continue unchanged when feature is disabled
   - **Backwards Compatibility**: Maintain complete backwards compatibility with existing behavior

## Sprout Class Implementation Tasks

### For Complex Features Requiring New Classes

1. **Test-Driven Class Design**:
   - **Comprehensive Test Suite**: Create exhaustive tests covering all functionality, dependencies, and integration points
   - **Dependency Injection**: Design class with full dependency injection for testability and mocking
   - **Protocol Design**: Create protocols/interfaces for all dependencies to enable comprehensive testing
   - **Concurrency Testing**: Include thread safety and concurrent execution tests where applicable

2. **Class Implementation with Full TDD**:
   - **Protocol-First Design**: Define interfaces before implementing concrete classes
   - **Dependency Injection**: Implement constructor injection for all external dependencies
   - **Error Handling**: Comprehensive error handling with well-defined error types and recovery strategies
   - **Async Operations**: Proper handling of asynchronous operations with completion handlers or async/await

3. **Service Integration Architecture**:
   - **Minimal Integration Points**: Design integration to require minimal changes to existing legacy code
   - **Feature Flag Controls**: Implement feature flag system for safe deployment and instant rollback
   - **Optional Service Usage**: Ensure existing functionality works completely without new sprouted service
   - **Dependency Container**: Register new service in dependency injection container for testing

## Framework-Specific Sprouting Implementation

### iOS/Swift Projects
- **Protocol-Based Design**: Use Swift protocols for dependency injection and testing
- **XCTest Integration**: Implement comprehensive XCTest-based testing with expectations for async operations
- **Dependency Injection**: Use property injection or constructor injection with protocol types
- **Feature Flags**: Implement UserDefaults-based or remote config feature flag system

### Node.js/JavaScript Projects  
- **Module-Based Sprouting**: Create new modules/classes without modifying existing code
- **Jest Testing**: Implement Jest-based testing with comprehensive mocking and async testing
- **Dependency Injection**: Use constructor injection or factory patterns for dependency management
- **Feature Toggles**: Implement configuration-based feature toggling system

### Python Projects
- **Class-Based Sprouting**: Create new classes with dependency injection for comprehensive testing
- **Pytest Testing**: Use pytest with fixtures and parameterization for comprehensive test coverage
- **Mock Integration**: Use unittest.mock for dependency mocking and test isolation
- **Configuration Management**: Implement feature flag system through configuration files or environment variables

### Java Projects
- **Interface-Based Design**: Create interfaces for all dependencies and use dependency injection frameworks
- **JUnit Testing**: Implement JUnit-based testing with Mockito for comprehensive mocking
- **Spring Integration**: Use Spring dependency injection for clean separation and testability
- **Properties-Based Features**: Use application properties for feature flag management

### Generic Projects
- **Manual Sprouting**: Implement sprouting patterns appropriate for the specific technology stack
- **Custom Testing**: Create comprehensive testing approach suitable for the project's testing capabilities
- **Configuration-Based Features**: Implement feature flag system appropriate for the technology
- **Documentation-Heavy**: Create extensive documentation for manual testing and validation procedures

## Coverage and Quality Requirements

### 100% Coverage for Sprouted Code
1. **Complete Line Coverage**: Every line of new sprouted code must be covered by tests
2. **Branch Coverage**: All decision branches and error paths must be tested
3. **Integration Coverage**: All integration points with existing code must be tested
4. **Performance Coverage**: Performance characteristics must be validated and tested

### Quality Standards for Sprouted Code
1. **Clean Code Principles**: Follow SOLID principles and clean code practices
2. **Comprehensive Error Handling**: Handle all error scenarios gracefully with proper error types
3. **Thread Safety**: Ensure thread safety for concurrent access where applicable
4. **Documentation**: Include comprehensive documentation for all public interfaces

## Integration and Rollback Strategy

### Minimal Integration Approach
1. **Feature Flag Integration**: All sprouted functionality controlled by feature flags
2. **Optional Execution**: Existing code paths work identically when sprouted features are disabled
3. **Single Integration Point**: Minimize the number of places where existing code calls sprouted functionality
4. **Backwards Compatibility**: Ensure no behavioral changes when sprouted features are disabled

### Rollback Capabilities
1. **Feature Flag Rollback**: Instant rollback by disabling feature flags
2. **Git Rollback**: Complete code rollback via git revert if needed
3. **Validation Testing**: Automated testing to verify rollback success
4. **Monitoring Integration**: Monitor sprouted functionality performance and errors

## Sprouted Code Validation

### Testing Requirements
1. **Unit Test Coverage**: 100% coverage for all sprouted methods and classes
2. **Integration Testing**: Comprehensive testing of sprouted functionality with existing system
3. **Regression Testing**: Verify existing characterization tests continue passing
4. **Performance Testing**: Ensure sprouted functionality meets performance requirements

### Quality Validation
1. **Code Review**: Manual review of all sprouted code for quality and maintainability
2. **Static Analysis**: Run static analysis tools on sprouted code to catch potential issues
3. **Security Review**: Security analysis of sprouted functionality, especially for sensitive operations
4. **Documentation Review**: Ensure comprehensive documentation for maintenance and future development

## Success Criteria
- New functionality added without modifying any existing legacy code
- 100% test coverage achieved for all sprouted code (methods and classes)
- Integration tests validate sprouted functionality works correctly with existing system
- Feature flags enable safe deployment with instant rollback capability
- All existing characterization tests continue passing without modification
- Complete documentation created for maintenance and rollback procedures

## Integration
- Documents sprouted functionality status and implementation details
- Maintains overall 90%+ coverage requirement while achieving 100% for new code
- Provides comprehensive rollback capability through feature flags and git revert
- Establishes pattern for future safe feature additions to legacy codebase

## Rollback
Sprouted functionality can be completely disabled via feature flags or reverted via git without affecting existing functionality:
1. **Feature Flag Disable**: Immediate rollback by disabling feature flags - existing code runs unchanged
2. **Git Revert**: Complete removal of sprouted code via git revert while preserving existing functionality
3. **Validation**: Run existing characterization tests to verify rollback success and system integrity
4. **Documentation**: Clear rollback procedures documented for emergency situations