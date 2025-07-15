---
allowed-tools: ["Bash", "Glob", "Grep", "LS", "Read", "Write", "Edit", "MultiEdit"]
description: "Implement dependency injection at identified seams to break hard dependencies and improve testability"
---

# Legacy Dependency Injection - Breaking Hard Dependencies for Testability

## Dynamic Context Gathering

!grep -r "new \|singleton\|shared\|getInstance" . --include="*.py" --include="*.js" --include="*.java" --include="*.swift" --include="*.ts" | head -10

!find . -name "*.py" -o -name "*.js" -o -name "*.java" -o -name "*.swift" -o -name "*.ts" | xargs grep -l "__init__\|constructor\|@inject" | head -10

!ls -la interfaces/ protocols/ abstractions/ || echo "No abstraction directories found"

## File References

@seam-analysis.json @interfaces/ @abstractions/ @dependency-container.json @mocks/

**Command**: `/legacy-dependency-inject`  
**Phase**: Transformation  
**Coverage Requirement**: 90% coverage + seam analysis + interface extraction complete (Google exemplary standard - blocks without this)  
**Risk Level**: Medium (modifies dependency relationships with comprehensive safety net)

## Objective

Implement dependency injection at identified seams to break hard dependencies, improve testability, and enable comprehensive mocking while preserving all existing functionality through rigorous safety measures.

## Context

Dependency injection is crucial for making legacy code testable by replacing hard-coded dependencies with injected abstractions. This command uses previously identified seams and extracted interfaces to implement safe dependency injection without changing existing behavior.

## Dependency Injection Implementation Tasks

1. **Prerequisite Validation**:
   - Verify that 90%+ test coverage requirement has been met and seam analysis is complete
   - Confirm that interface extraction has been completed for target dependencies
   - Validate that mock infrastructure is ready to support dependency injection
   - Check that characterization tests are comprehensive for components receiving injection

2. **Injection Strategy Analysis**:
   - **Seam Utilization**: Use previously identified seams for dependency injection implementation
   - **Interface Integration**: Leverage extracted interfaces for clean dependency abstraction
   - **Injection Pattern Selection**: Choose appropriate injection patterns (constructor, property, method parameter)
   - **Lifecycle Management**: Plan dependency lifecycle and scope management

3. **Injection Point Implementation**:
   - **Constructor Injection**: Modify constructors to accept interface dependencies
   - **Property Injection**: Add settable properties for dependency injection
   - **Method Parameter Injection**: Modify methods to accept strategy or configuration dependencies
   - **Factory Integration**: Implement factory patterns for complex dependency creation

4. **Production Configuration Setup**:
   - **Dependency Container**: Set up dependency injection container or service locator
   - **Configuration Management**: Create configuration for production dependency wiring
   - **Default Implementation**: Ensure existing concrete implementations are properly configured
   - **Environment-Specific Setup**: Configure different dependencies for different environments

## Injection Implementation by Pattern

### Constructor Injection Implementation

1. **Constructor Modification**:
   - Add interface parameters to existing constructors while maintaining backward compatibility
   - Provide default constructor overloads that use original concrete dependencies
   - Implement proper parameter validation and null checking for injected dependencies
   - Maintain existing object construction patterns throughout the codebase

2. **Backward Compatibility Preservation**:
   - Create constructor overloads that maintain existing instantiation patterns
   - Implement factory methods that provide default dependency injection
   - Ensure that existing code can continue to work without modification
   - Provide migration path for gradual adoption of dependency injection

3. **Dependency Container Integration**:
   - Configure dependency injection container to provide appropriate implementations
   - Set up dependency resolution rules and lifetime management
   - Implement proper error handling for missing or misconfigured dependencies
   - Create validation mechanisms to ensure all dependencies are properly resolved

### Property Injection Implementation

1. **Property-Based Injection Setup**:
   - Add properties for dependencies with appropriate access levels and validation
   - Implement lazy initialization for dependencies that may be injected after construction
   - Provide default implementations that maintain existing behavior when not injected
   - Include proper error handling for missing dependencies when needed

2. **Setter Method Enhancement**:
   - Create setter methods with appropriate validation and type checking
   - Implement fluent interface patterns where appropriate for dependency configuration
   - Add thread safety considerations for property injection in concurrent environments
   - Ensure that property injection doesn't interfere with existing object lifecycle

### Method Parameter Injection

1. **Strategy Pattern Implementation**:
   - Modify methods to accept strategy objects or configuration parameters
   - Provide default strategy implementations that maintain existing behavior
   - Implement method overloads that use default strategies for backward compatibility
   - Add comprehensive validation for injected strategy implementations

2. **Configuration Parameter Injection**:
   - Accept configuration objects that control method behavior
   - Provide default configurations that preserve existing functionality
   - Implement configuration validation and error handling
   - Add flexibility for runtime configuration changes where appropriate

## Framework-Specific Dependency Injection

### iOS/Swift Dependency Injection
- Use Swift protocols for dependency abstraction and injection
- Implement property injection with proper Swift optionals handling
- Use Swift dependency injection frameworks (Resolver, Swinject) where appropriate
- Handle Swift value types and reference types correctly in dependency injection

### JavaScript/Node.js Dependency Injection
- Implement module-based dependency injection using require/import patterns
- Use JavaScript dependency injection libraries (Inversify, Awilix) for complex scenarios
- Handle asynchronous dependency resolution using Promises or async/await
- Implement proper module lifecycle management for dependency injection

### Python Dependency Injection
- Use Python dependency injection frameworks (dependency-injector, injector) where appropriate
- Implement constructor injection with proper type hints and validation
- Handle Python decorators and context managers in dependency injection
- Use Python's dynamic nature appropriately for flexible dependency resolution

### Java Dependency Injection
- Use established Java DI frameworks (Spring, Guice, CDI) for enterprise applications
- Implement annotation-based dependency injection with proper lifecycle management
- Handle Java generics and type safety in dependency injection configuration
- Use proper exception handling and validation for dependency resolution

## Testing and Validation

### Mock Integration Testing

1. **Mock Implementation Validation**:
   - Test all dependency injection points with mock implementations
   - Validate that mock behavior accurately represents real dependency contracts
   - Test error scenarios and edge cases using controllable mock implementations
   - Ensure that dependency injection doesn't interfere with existing test infrastructure

2. **Test Environment Configuration**:
   - Set up test-specific dependency injection configuration
   - Create test doubles and fakes for different testing scenarios
   - Implement test data factories for consistent test dependency setup
   - Validate that test configuration is isolated from production configuration

### Production Validation

1. **Behavioral Preservation Testing**:
   - Run comprehensive characterization tests with dependency injection enabled
   - Validate that all existing functionality works correctly with injected dependencies
   - Test edge cases and error conditions with production dependency configuration
   - Ensure that dependency injection doesn't introduce performance regressions

2. **Configuration Validation**:
   - Test dependency injection configuration in staging environment
   - Validate that all dependencies are properly resolved and configured
   - Test application startup and shutdown with dependency injection enabled
   - Ensure that dependency injection doesn't introduce memory leaks or resource issues

## Dependency Injection Quality Assurance

### Design Quality Validation

1. **SOLID Principles Compliance**: Ensure dependency injection supports Single Responsibility and Dependency Inversion
2. **Coupling Reduction**: Validate that dependency injection reduces coupling between components
3. **Testability Improvement**: Verify that dependency injection improves unit test isolation and mocking
4. **Maintainability Enhancement**: Ensure that dependency injection makes code more maintainable and flexible

### Performance and Security Considerations

1. **Performance Impact Assessment**: Measure dependency injection overhead and optimize if necessary
2. **Security Validation**: Ensure dependency injection doesn't introduce security vulnerabilities
3. **Memory Management**: Validate that dependency injection doesn't cause memory leaks or excessive allocation
4. **Thread Safety**: For concurrent applications, ensure dependency injection is thread-safe

## Rollback and Recovery Procedures

### Immediate Rollback Triggers
- Any characterization test failures after dependency injection implementation
- Performance degradation or memory issues introduced by dependency injection
- Configuration errors or missing dependencies in production environment
- Integration failures with existing systems or external dependencies

### Rollback Execution
1. **Configuration Rollback**: Disable dependency injection and restore original concrete dependencies
2. **Code Restoration**: Remove dependency injection modifications and restore original dependency patterns
3. **Container Cleanup**: Remove dependency injection container configuration and related infrastructure
4. **Validation Testing**: Comprehensive testing to ensure successful rollback and system integrity

## Success Criteria

- Hard dependencies successfully replaced with injected interface dependencies
- Comprehensive mock infrastructure integrated with dependency injection
- All existing behavior preserved with 100% characterization test validation
- Improved testability through controllable dependency injection
- Production configuration properly established with appropriate dependency wiring
- Complete rollback capability maintained throughout dependency injection implementation

## Integration

- Documents dependency injection completion status and architectural improvements
- Provides foundation for comprehensive testing through injected mock dependencies
- Enables further refactoring by reducing coupling to concrete implementations
- Establishes clean dependency management patterns for future development

## Rollback

Dependency injection can be completely reversed if issues arise:
1. **Dependency Restoration**: Remove injection infrastructure and restore original concrete dependencies
2. **Configuration Cleanup**: Remove dependency injection configuration and container setup
3. **Code Cleanup**: Restore original constructor and method signatures
4. **System Validation**: Verify that original functionality works correctly without dependency injection