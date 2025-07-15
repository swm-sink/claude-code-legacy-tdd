# Legacy Mock Generator - Test Double Creation for Identified Seams

**Command**: `/legacy-mock-generator`  
**Phase**: Safety Infrastructure Creation  
**Coverage Requirement**: 90%+ coverage + seam analysis complete (blocks without this)  
**Risk Level**: Low (test infrastructure only, no production code changes)

## Objective

Generate comprehensive test doubles (mocks, stubs, fakes) for all identified seams, enabling safe testing and transformation of legacy code without modifying production behavior or requiring external dependencies.

## Context

Test doubles are essential for isolating legacy code during testing. This command creates mocks for external dependencies, stubs for complex internal components, and fakes for resource-intensive operations, based on the seam analysis results.

## Mock Generation Tasks

1. **Prerequisite Validation**:
   - Verify that 90%+ test coverage requirement has been met from `/legacy-coverage-report`
   - Confirm that seam analysis has been completed from `/legacy-seam-identify`
   - Validate that dependency analysis results are available
   - Check that the codebase is ready for comprehensive mock generation

2. **Seam Analysis Integration**:
   - **Load Seam Identification Results**: Import seam analysis data to understand dependency injection points
   - **External Dependency Mapping**: Identify all external systems, APIs, databases, and third-party services
   - **Internal Coupling Analysis**: Map internal dependencies that need isolation for testing
   - **Mock Priority Assessment**: Prioritize mocks based on business criticality and testing complexity

3. **External Dependency Mock Generation**:
   - **Network Service Mocks**: Create mocks for HTTP clients, REST APIs, SOAP services, and external web services
   - **Database Access Mocks**: Generate test doubles for database connections, ORM objects, and data access layers
   - **File System Mocks**: Create mocks for file operations, directory access, and I/O operations
   - **Third-Party Library Mocks**: Generate test doubles for external libraries and framework dependencies

4. **Internal Component Mock Generation**:
   - **Service Layer Mocks**: Create mocks for business service objects and internal API layers
   - **Repository Pattern Mocks**: Generate test doubles for data repository and persistence abstractions
   - **Configuration Mocks**: Create mocks for configuration providers and settings management
   - **Event System Mocks**: Generate test doubles for event publishers, subscribers, and messaging systems

5. **Framework-Specific Mock Implementation**:
   - **iOS/Swift Projects**: Generate XCTest-compatible mock objects using protocols and test doubles
   - **Node.js/JavaScript Projects**: Create Jest-compatible mocks with spy functionality and return value control
   - **Python Projects**: Implement pytest-compatible mocks using unittest.mock and fixture management
   - **Java Projects**: Generate Mockito-compatible test doubles with annotation-based configuration
   - **Generic Projects**: Create basic mock implementations with manual verification and setup procedures

## Test Double Categories and Patterns

### Mock Objects (Behavior Verification)
- **Service Layer Mocks**: Verify that methods are called with correct parameters and in proper sequence
- **API Client Mocks**: Ensure external service calls are made with proper authentication and data
- **Event Publisher Mocks**: Validate that events are triggered at appropriate times with correct data
- **Notification System Mocks**: Verify notification delivery and subscription management

### Stub Objects (State Verification)
- **Configuration Stubs**: Provide consistent configuration values for testing scenarios
- **Data Provider Stubs**: Return predictable data sets for business logic testing
- **Authentication Stubs**: Provide controlled authentication states and user contexts
- **Feature Flag Stubs**: Control feature enablement for testing different code paths

### Fake Objects (Working Implementations)
- **In-Memory Databases**: Fast, isolated data storage for integration testing
- **File System Fakes**: Memory-based file operations for I/O testing
- **Message Queue Fakes**: Local message handling without external queue systems
- **Time Provider Fakes**: Controlled time advancement for date/time dependent testing

## Mock Generation Strategy

### External Dependencies
1. **Network Services**: HTTP clients, REST API consumers, WebSocket connections
2. **Database Access**: ORM objects, connection pools, query builders, data access layers
3. **File System Operations**: File readers, directory scanners, configuration file processors
4. **Third-Party Libraries**: External SDK clients, analytics services, payment processors

### Internal Dependencies
1. **Business Services**: Core business logic services that other components depend on
2. **Repository Patterns**: Data access abstractions and persistence layer interfaces
3. **Configuration Providers**: Settings management and environment configuration access
4. **Event Systems**: Internal messaging, event publishing, and subscription management

### Framework-Specific Mock Libraries and Patterns
- **iOS/Swift**: Use protocols for mockability, XCTest expectations, and dependency injection
- **Node.js/JavaScript**: Leverage Jest mocking, sinon spies, and module replacement patterns
- **Python**: Utilize unittest.mock, pytest fixtures, and context manager patterns
- **Java**: Implement Mockito annotations, argument matchers, and verification patterns

## Mock Infrastructure Setup

### Directory Structure Organization
- **External Mocks**: Test doubles for third-party services and external dependencies
- **Internal Mocks**: Test doubles for internal components and business services
- **Test Fixtures**: Shared test data and configuration for consistent mock behavior
- **Mock Utilities**: Helper functions and base classes for mock creation and management

### Mock Registry and Management
1. **Mock Registry Creation**: Central registration system for all generated test doubles
2. **Mock Configuration Management**: Standardized configuration for mock behavior and responses
3. **Mock Lifecycle Management**: Setup, teardown, and reset procedures for test isolation
4. **Mock Verification Utilities**: Helper methods for asserting mock interactions and state

### Integration with Testing Framework
- **Test Suite Integration**: Seamless integration with existing test infrastructure
- **Mock Injection Points**: Automatic mock injection at identified seam locations
- **Test Data Management**: Coordinated test data setup for mock objects and real components
- **Assertion Helpers**: Framework-specific assertion methods for mock verification

## Mock Validation and Quality Assurance

### Mock Behavior Validation
1. **Mock-Reality Alignment**: Ensure mocks accurately represent real dependency behavior
2. **Contract Testing**: Validate that mocks implement the same contracts as real dependencies
3. **Behavior Consistency**: Verify that mock responses are realistic and business-appropriate
4. **Error Scenario Coverage**: Include comprehensive error and edge case scenarios in mocks

### Mock Maintenance and Evolution
- **Mock Update Procedures**: Process for updating mocks when real dependencies change
- **Version Compatibility**: Ensure mocks remain compatible with dependency version changes
- **Mock Documentation**: Clear documentation of mock capabilities and intended usage
- **Mock Testing**: Tests for the mocks themselves to ensure they function correctly

## Success Criteria
- Comprehensive test doubles generated for all identified external dependencies
- Internal component mocks created for critical business services and integration points
- Mock registry established with centralized management and configuration
- Test framework integration completed with automatic mock injection capabilities
- Complete documentation and maintenance procedures for long-term mock management

## Integration
- Documents mock generation completion status and test infrastructure readiness
- Provides test isolation infrastructure for all subsequent transformation commands
- Enables comprehensive testing without external dependencies or complex setup requirements
- Establishes foundation for safe refactoring with reliable test double infrastructure

## Rollback
Mock generation is test infrastructure creation and requires no rollback procedures. If mocks are problematic:
1. Delete generated mock files and regenerate with corrected configuration
2. Review seam analysis results and update mock interfaces as needed
3. Validate mock behavior against real dependency contracts before proceeding
