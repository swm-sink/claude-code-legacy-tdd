---
allowed-tools: ["Bash", "Glob", "Grep", "LS", "Read", "Write", "Edit", "MultiEdit"]
description: "Implement large-scale changes safely using parallel change technique with new implementation alongside legacy code"
---

# Legacy Parallel Change - Safe Migration Through Dual Implementation

## Dynamic Context Gathering

!find . -name "*.py" -o -name "*.js" -o -name "*.java" -o -name "*.swift" -o -name "*.ts" | xargs grep -l "feature.*flag\|toggle\|config" | head -10

!ls -la new-implementation/ parallel-change/ migration/ || echo "No parallel change directories found"

!git status --porcelain && git log --oneline -3

## File References

@feature-flags.json @parallel-implementation/ @migration-plan.json @characterization-tests/

**Command**: `/legacy-parallel-change`  
**Phase**: Transformation  
**Coverage Requirement**: 90%+ coverage + comprehensive safety net (blocks without this)  
**Risk Level**: Low (implements new alongside old, zero modification to existing code)

## Objective

Implement large-scale changes safely using the parallel change technique, where new implementation runs alongside existing legacy code, enabling gradual migration, comprehensive validation, and instant rollback without touching legacy functionality.

## Context

Parallel change is the safest technique for major architectural changes in legacy systems. This command implements new functionality completely separate from legacy code, validates it thoroughly, and provides seamless migration with instant rollback capability.

## Parallel Change Strategy Tasks

1. **Prerequisite Validation**:
   - Verify that 90%+ test coverage requirement has been met and safety net is complete
   - Confirm that comprehensive characterization tests document current legacy behavior
   - Validate that feature flag infrastructure is ready for safe parallel implementation deployment
   - Check that monitoring and alerting systems can track parallel implementation performance

2. **Migration Scope Analysis**:
   - **Legacy Component Analysis**: Thoroughly understand current implementation behavior, interfaces, and dependencies
   - **New Implementation Planning**: Design improved implementation that addresses legacy limitations
   - **Migration Strategy Definition**: Plan gradual migration approach with validation checkpoints
   - **Rollback Criteria**: Define clear criteria for when to fall back to legacy implementation

3. **Parallel Implementation Design**:
   - **Interface Compatibility**: Ensure new implementation can serve as drop-in replacement for legacy
   - **Feature Parity**: Plan complete feature parity between legacy and new implementations
   - **Performance Requirements**: Define performance targets that meet or exceed legacy implementation
   - **Data Consistency**: Plan data synchronization between legacy and new implementations if needed

4. **Validation and Migration Planning**:
   - **Comparative Testing**: Plan comprehensive testing to validate new implementation against legacy
   - **Gradual Rollout Strategy**: Design phased migration with increasing traffic percentages
   - **Monitoring Strategy**: Plan comprehensive monitoring to compare implementations in real-time
   - **Migration Checkpoints**: Define validation gates that must pass before increasing migration percentage

## Parallel Implementation Development

### New Implementation Creation

1. **Clean Implementation Development**:
   - Develop new implementation using modern patterns, proper testing, and clean architecture
   - Apply all lessons learned from legacy code analysis and antipattern identification
   - Implement comprehensive unit testing, integration testing, and characterization testing
   - Use dependency injection, interface-based design, and proper separation of concerns

2. **Legacy Interface Compatibility**:
   - Ensure new implementation exposes identical interfaces to legacy implementation
   - Implement adapter patterns if necessary to bridge interface differences
   - Validate that all existing consumers can use new implementation without modification
   - Handle all edge cases, error conditions, and exceptional scenarios identically

3. **Enhanced Functionality Integration**:
   - Add improvements and new features that weren't possible in legacy implementation
   - Implement better error handling, logging, monitoring, and performance optimization
   - Add security enhancements and compliance features
   - Include comprehensive documentation and maintainability improvements

### Parallel Execution Infrastructure

1. **Feature Flag Integration**:
   - Implement sophisticated feature flag system to control migration percentage
   - Add user-based, request-based, or time-based routing between implementations
   - Include emergency killswitch to instantly revert to legacy implementation
   - Add granular control for different features or user segments

2. **Router and Dispatcher Setup**:
   - Create routing logic that directs traffic between legacy and new implementations
   - Implement load balancing and traffic splitting with configurable percentages
   - Add intelligent routing based on user characteristics, request types, or business rules
   - Include comprehensive logging and monitoring of routing decisions

3. **Data Synchronization Strategy**:
   - Plan data consistency between legacy and new implementations during parallel execution
   - Implement data replication, synchronization, or shared storage strategies as appropriate
   - Add data validation and consistency checking between implementations
   - Plan for data migration strategy when fully switching to new implementation

## Framework-Specific Parallel Change Implementation

### iOS/Swift Parallel Change
- Implement parallel view controllers or service implementations with protocol-based switching
- Use iOS feature flags and A/B testing frameworks for gradual rollout
- Handle iOS app lifecycle and memory management in both implementations
- Implement proper data persistence strategy for parallel implementations

### JavaScript/Node.js Parallel Change
- Create parallel modules or services with identical exports and interfaces
- Use feature flag libraries (LaunchDarkly, Unleash) for traffic routing
- Implement proper asynchronous handling in both legacy and new implementations
- Handle Node.js clustering and load balancing for parallel execution

### Python Parallel Change
- Implement parallel classes or modules with identical interfaces
- Use Python decorators for intelligent routing between implementations
- Handle Python-specific concerns (GIL, memory management) in both implementations
- Implement proper logging and monitoring for parallel execution

### Java Parallel Change
- Create parallel service implementations with identical interfaces
- Use Spring profiles or dependency injection for implementation switching
- Handle Java enterprise concerns (transactions, security) consistently
- Implement proper lifecycle management for both implementations

## Validation and Migration Execution

### Comprehensive Validation Strategy

1. **Shadow Mode Testing**:
   - Run new implementation in shadow mode, comparing results with legacy implementation
   - Log differences and analyze discrepancies without affecting user experience
   - Build confidence in new implementation through extensive shadow testing
   - Identify and fix edge cases discovered through real-world shadow execution

2. **Comparative Performance Testing**:
   - Monitor performance characteristics of both implementations under real load
   - Compare response times, memory usage, CPU utilization, and error rates
   - Validate that new implementation meets or exceeds legacy performance
   - Identify performance bottlenecks and optimize before increasing migration percentage

3. **Business Logic Validation**:
   - Compare business outcomes between implementations to ensure identical results
   - Validate that all business rules, calculations, and workflows produce same outputs
   - Test edge cases, error conditions, and exceptional scenarios in both implementations
   - Ensure data integrity and consistency throughout parallel execution period

### Gradual Migration Execution

1. **Phased Rollout Strategy**:
   - Start with 1% traffic to new implementation for initial validation
   - Gradually increase percentage (5%, 10%, 25%, 50%, 75%, 100%) based on success criteria
   - Include checkpoints at each phase to validate success before proceeding
   - Implement automatic rollback if success criteria are not met

2. **User Segment Testing**:
   - Test new implementation with specific user segments (internal users, beta users, low-risk users)
   - Gradually expand to larger user populations based on validation results
   - Include different geographical regions, user types, and usage patterns
   - Monitor user experience and satisfaction throughout migration process

3. **Feature-by-Feature Migration**:
   - Migrate individual features or components rather than entire system at once
   - Validate each feature migration independently before proceeding to next
   - Allow partial migration where some features use new implementation while others use legacy
   - Plan dependency order for feature migration to minimize integration issues

## Monitoring and Validation

### Real-Time Monitoring Strategy

1. **Performance Monitoring**:
   - Track response times, throughput, error rates, and resource utilization for both implementations
   - Set up alerts for performance degradation or anomalies in either implementation
   - Monitor business metrics and KPIs to ensure new implementation meets business requirements
   - Track user experience metrics and customer satisfaction during migration

2. **Error and Exception Monitoring**:
   - Monitor error rates and exception types in both implementations
   - Set up automated alerting for error rate increases or new error types
   - Track error patterns and investigate discrepancies between implementations
   - Implement automatic rollback triggers based on error rate thresholds

3. **Business Impact Monitoring**:
   - Monitor revenue, conversion rates, and other business metrics during migration
   - Track user behavior changes and engagement metrics
   - Validate that business outcomes are maintained or improved with new implementation
   - Set up executive dashboards for migration progress and impact visibility

## Rollback and Recovery Procedures

### Instant Rollback Capability

1. **Emergency Rollback Triggers**:
   - Error rate increases above defined thresholds
   - Performance degradation below acceptable levels
   - Business metric impacts (revenue loss, conversion rate drops)
   - User experience degradation or customer complaints

2. **Rollback Execution**:
   - **Feature Flag Rollback**: Instant rollback by adjusting feature flags to route 100% traffic to legacy
   - **Load Balancer Rollback**: Immediate traffic routing changes at infrastructure level
   - **Application-Level Rollback**: Code-based routing changes if feature flags fail
   - **Data Rollback**: Restore data consistency if data synchronization issues occur

### Recovery and Analysis

1. **Post-Rollback Analysis**:
   - Comprehensive analysis of rollback triggers and root causes
   - Performance comparison and gap analysis between implementations
   - User impact assessment and customer communication plan
   - Technical debt and improvement planning for future migration attempts

2. **Continuous Improvement**:
   - Update new implementation based on learnings from parallel execution
   - Improve monitoring, alerting, and rollback procedures
   - Enhance testing strategies based on real-world validation results
   - Plan for future migration attempts with improved approach

## Success Criteria

- New implementation successfully developed with comprehensive testing and validation
- Parallel execution infrastructure enables safe traffic splitting and gradual migration
- All validation checkpoints passed with new implementation meeting or exceeding legacy performance
- Successful migration to new implementation with improved functionality and maintainability
- Comprehensive rollback capability maintained throughout entire migration process
- Legacy implementation safely deprecated after successful migration validation

## Integration

- Documents parallel change completion status and migration success
- Provides foundation for future major architectural changes using parallel change technique
- Establishes patterns for safe large-scale system evolution and modernization
- Enables confident major system improvements through risk-free parallel implementation

## Rollback

Parallel change provides ultimate rollback capability:
1. **Instant Traffic Routing**: Immediate return to legacy implementation via feature flags
2. **Zero Downtime Rollback**: Seamless rollback without system interruption
3. **Complete Validation**: Comprehensive testing of rollback procedures before migration
4. **Legacy Preservation**: Original legacy implementation preserved until migration is fully validated