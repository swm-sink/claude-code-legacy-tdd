---
allowed-tools: ["Bash", "Glob", "Grep", "LS", "Read", "Write", "Edit", "MultiEdit"]
description: "Safely add new behavior to existing methods using wrap method technique, preserving all original functionality"
---

# Legacy Method Wrapping - Safe Behavior Modification Through Delegation

## Dynamic Context Gathering

!find . -name "*.py" -o -name "*.js" -o -name "*.java" -o -name "*.swift" -o -name "*.ts" | xargs grep -l "def \|function \|public \|private " | head -10

!grep -r "wrapper\|decorator\|proxy" . --include="*.py" --include="*.js" --include="*.java" --include="*.swift" --include="*.ts" | head -10

!git log --oneline -3 && echo "\n=== Recent commits ==="

## File References

@method-analysis.json @characterization-tests/ @wrapper-patterns/ @proxy-implementations/

**Command**: `/legacy-wrap-method`  
**Phase**: Transformation  
**Coverage Requirement**: 90%+ coverage + characterization tests complete (blocks without this)  
**Risk Level**: Low (adds behavior without modifying existing code)

## Objective

Safely add new behavior to existing methods using the wrap method technique, preserving all original functionality while enabling feature addition, logging, monitoring, or validation without touching legacy code.

## Context

Method wrapping is one of the safest legacy transformation techniques from Michael Feathers' toolkit. It preserves existing method behavior completely while adding new functionality through delegation, making it ideal for adding cross-cutting concerns or enhancing existing features.

## Method Wrapping Analysis Tasks

1. **Prerequisite Validation**:
   - Verify that 90%+ test coverage requirement has been met and characterization tests are complete
   - Confirm that target methods have comprehensive behavioral documentation through tests
   - Validate that rollback procedures are prepared for immediate recovery if needed
   - Check that seam identification has been completed for dependency injection opportunities

2. **Wrapping Candidate Identification**:
   - **Business Logic Enhancement**: Methods that need additional validation, logging, or monitoring
   - **Cross-Cutting Concerns**: Methods that need caching, security checks, audit trails, or performance monitoring
   - **Feature Flag Integration**: Methods that need conditional behavior or A/B testing support
   - **Error Handling Enhancement**: Methods that need improved error handling or recovery mechanisms

3. **Wrapper Design Planning**:
   - **Delegation Strategy**: Plan how wrapper will call original method while preserving exact behavior
   - **Enhancement Definition**: Define what new behavior will be added through wrapping
   - **Parameter Handling**: Ensure wrapper handles all parameter types and edge cases correctly
   - **Return Value Management**: Plan how wrapper will handle return values, exceptions, and side effects

4. **Safety and Rollback Planning**:
   - **Feature Flag Strategy**: Plan feature flags to enable/disable wrapper behavior safely
   - **Monitoring Integration**: Define metrics to track wrapper performance and correctness
   - **Rollback Criteria**: Establish clear criteria for when to rollback wrapper implementation
   - **Testing Strategy**: Plan comprehensive testing of both original behavior and new wrapper functionality

## Method Wrapping Implementation Tasks

### Wrapper Method Creation

1. **Original Method Preservation**:
   - Rename original method to preserve exact functionality (e.g., `processPayment` → `processPaymentImpl`)
   - Ensure original method signature and behavior remain completely unchanged
   - Maintain all original error handling, exceptions, and side effects exactly
   - Preserve original method's access level and documentation

2. **Wrapper Method Implementation**:
   - Create new method with original method's name and signature
   - Implement delegation to renamed original method with identical parameter passing
   - Add new functionality around the delegation call (before, after, or both)
   - Ensure wrapper preserves all return values, exceptions, and side effects from original method

3. **Enhanced Functionality Integration**:
   - Add logging, monitoring, validation, or other cross-cutting concerns as needed
   - Implement feature flag controls to enable/disable enhanced functionality
   - Handle errors in enhanced functionality without affecting original method behavior
   - Ensure enhanced functionality doesn't interfere with original method's operation

### Framework-Specific Wrapping Implementation

#### iOS/Swift Method Wrapping
- Use Swift method renaming and delegation patterns
- Handle Swift optionals and error throwing properly in wrapper methods
- Implement appropriate access control for wrapped and wrapper methods
- Use Swift attributes and annotations appropriately for wrapper functionality

#### JavaScript/Node.js Method Wrapping
- Implement JavaScript function wrapping with proper `this` binding preservation
- Handle asynchronous methods (Promises, async/await) correctly in wrappers
- Use JavaScript closures appropriately to maintain original method context
- Implement proper error handling for both synchronous and asynchronous operations

#### Python Method Wrapping
- Use Python method renaming and delegation with proper `self` parameter handling
- Implement decorators for reusable wrapping patterns where appropriate
- Handle Python exceptions and context managers correctly in wrapped methods
- Maintain proper method signatures and documentation through wrapping

#### Java Method Wrapping
- Implement Java method wrapping with proper access modifiers and exception handling
- Use Java annotations appropriately for wrapper functionality
- Handle checked exceptions correctly in wrapper delegation
- Implement proper inheritance and polymorphism support in wrapped methods

### Wrapper Validation and Testing

1. **Original Behavior Preservation**:
   - Run all existing characterization tests to verify original behavior is preserved
   - Test all parameter combinations and edge cases through wrapper delegation
   - Validate that all exceptions and error conditions are properly delegated
   - Ensure wrapper doesn't introduce any performance regressions in normal operation

2. **Enhanced Functionality Testing**:
   - Create comprehensive tests for new wrapper functionality
   - Test enhanced functionality with feature flags both enabled and disabled
   - Validate that enhanced functionality failures don't affect original method behavior
   - Test error scenarios in enhanced functionality to ensure graceful degradation

3. **Integration and End-to-End Testing**:
   - Test wrapped methods in full system context to ensure integration works correctly
   - Validate that wrapper behavior works correctly with external dependencies
   - Test performance characteristics to ensure wrapper doesn't introduce bottlenecks
   - Verify that monitoring and logging functionality works correctly in production-like environment

## Wrapper Enhancement Patterns

### Common Wrapping Use Cases

1. **Logging and Audit Trail Wrapping**:
   - Add method entry/exit logging with parameter and return value capture
   - Implement audit trail recording for business-critical operations
   - Include timing and performance monitoring for method execution
   - Add security audit logging for sensitive operations

2. **Validation and Security Wrapping**:
   - Add input validation and sanitization before delegating to original method
   - Implement authorization checks and security validation
   - Add rate limiting and throttling for high-traffic methods
   - Include data protection and privacy compliance checks

3. **Caching and Performance Wrapping**:
   - Implement result caching for expensive operations
   - Add memoization for pure functions with expensive calculations
   - Include performance monitoring and optimization hints
   - Add circuit breaker patterns for external service calls

4. **Feature Flag and A/B Testing Wrapping**:
   - Implement feature flag controls for new functionality rollout
   - Add A/B testing infrastructure for behavior comparison
   - Include gradual rollout controls for risk mitigation
   - Add experimental feature validation and monitoring

### Wrapper Safety Patterns

1. **Defensive Wrapper Implementation**:
   - Always delegate to original method even if wrapper functionality fails
   - Implement comprehensive error handling for wrapper-specific functionality
   - Use feature flags to disable wrapper behavior if issues arise
   - Include monitoring and alerting for wrapper-related problems

2. **Performance-Safe Wrapping**:
   - Minimize wrapper overhead through efficient implementation
   - Use asynchronous processing for heavyweight wrapper functionality
   - Implement timeout and circuit breaker patterns for wrapper operations
   - Monitor wrapper performance impact and adjust accordingly

## Rollback and Recovery Procedures

### Immediate Rollback Triggers
- Any characterization test failures after wrapper implementation
- Performance degradation exceeding 5% of baseline performance
- Any exceptions or errors introduced by wrapper functionality
- Monitoring alerts indicating wrapper-related system problems

### Rollback Execution
1. **Feature Flag Rollback**: Immediately disable wrapper functionality through feature flags
2. **Method Restoration**: Restore original method name and remove wrapper if needed
3. **Code Cleanup**: Remove wrapper implementation and restore original method structure
4. **Validation Testing**: Run comprehensive tests to ensure successful rollback

## Success Criteria

- Enhanced functionality successfully added without modifying original method behavior
- All existing behavior preserved with 100% characterization test validation
- New wrapper functionality thoroughly tested and validated
- Feature flag controls enable safe deployment and rollback
- Performance characteristics maintained or improved through wrapping
- Complete monitoring and observability for wrapper functionality

## Integration

- Documents method wrapping completion status and enhancement details
- Provides foundation for adding cross-cutting concerns to legacy methods
- Enables gradual feature rollout through feature flag integration
- Establishes safe pattern for enhancing legacy functionality without modification

## Rollback

Method wrapping can be immediately disabled or removed if issues arise:
1. **Feature Flag Disable**: Instant rollback by disabling wrapper functionality
2. **Method Restoration**: Complete removal of wrapper and restoration of original method
3. **Behavior Validation**: Verify original functionality works correctly after rollback
4. **Enhancement Analysis**: Document wrapper issues for future improvement attempts