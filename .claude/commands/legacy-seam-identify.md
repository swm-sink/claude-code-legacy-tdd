---
allowed-tools: ["Bash", "Glob", "Grep", "LS", "Read"]
description: "Identify and catalog specific seams (dependency injection points) in legacy code for safe testing"
---

# Legacy Seam Identification - Dependency Injection Points Discovery

## Dynamic Context Gathering

!grep -r "new \|import \|require(\|#include" . --include="*.py" --include="*.js" --include="*.java" --include="*.swift" --include="*.ts" | head -20

!grep -r "singleton\|shared\|default\|getInstance" . --include="*.py" --include="*.js" --include="*.java" --include="*.swift" --include="*.ts" | head -10

!find . -name "*.py" -o -name "*.js" -o -name "*.java" -o -name "*.swift" -o -name "*.ts" | xargs grep -l "__init__\|constructor\|init" | head -10

## File References

@dependency-analysis.json @coupling-report.json @package.json @requirements.txt @pom.xml

**Command**: `/legacy-seam-identify`  
**Phase**: Safety Infrastructure Creation  
**Coverage Requirement**: 90%+ coverage established (blocks without this)  
**Risk Level**: Low (analysis only, no code changes)

## Objective

Identify and catalog specific "seams" (dependency injection points) in legacy code where external dependencies can be intercepted and replaced with test doubles, enabling safe testing and transformation without modifying production code.

## Context

A "seam" is a place where you can alter behavior in your program without editing code in that place. Seams are critical for making legacy code testable by allowing dependency injection. This command builds on dependency analysis to provide specific, actionable injection points.

## Seam Identification Tasks

1. **Prerequisite Validation**:
   - Verify that 90%+ test coverage requirement has been met from `/legacy-coverage-report`
   - Confirm that dependency analysis has been completed from `/legacy-dependency-analysis`
   - Validate that risk assessment results are available for prioritization
   - Check that the codebase is ready for seam analysis and dependency injection planning

2. **Seam Discovery and Classification**:
   - **Constructor Seams**: Identify classes that can accept dependencies through constructor parameters
   - **Method Parameter Seams**: Find methods that can receive strategy objects or configuration parameters
   - **Property/Field Seams**: Locate instance variables that can be injected instead of hard-coded
   - **Interface Extraction Opportunities**: Identify concrete dependencies that can be abstracted behind interfaces

3. **External Dependency Seam Analysis**:
   - **Network Service Seams**: Find HTTP clients, API consumers, and external service connections
   - **Database Access Seams**: Identify database connections, ORM objects, and data access layers
   - **File System Seams**: Locate file operations, directory access, and I/O dependencies
   - **Third-Party Library Seams**: Find external library dependencies and SDK integrations

4. **Internal Dependency Seam Analysis**:
   - **Service Layer Seams**: Identify internal service dependencies and business logic components
   - **Configuration Seams**: Find configuration providers and settings management dependencies
   - **Event System Seams**: Locate event publishers, subscribers, and messaging dependencies
   - **Utility Seams**: Identify utility class dependencies and helper function usage

5. **Seam Quality Assessment**:
   - **Seam Accessibility**: Evaluate how easily each seam can be accessed for dependency injection
   - **Injection Complexity**: Assess the complexity of implementing dependency injection at each seam
   - **Test Impact**: Determine how each seam will improve testability and test isolation
   - **Refactoring Safety**: Evaluate the safety of modifying each seam for dependency injection

6. **Framework-Specific Seam Identification**:
   - **iOS/Swift Projects**: Identify protocol-based seams, singleton replacements, and dependency injection points in UIKit/SwiftUI
   - **Node.js/JavaScript Projects**: Find module-level seams, require/import injection points, and middleware seams
   - **Python Projects**: Identify import-level seams, class-based injection points, and module replacement opportunities
   - **Java Projects**: Find interface-based seams, Spring dependency injection points, and constructor injection opportunities
   - **Generic Projects**: Establish manual seam identification procedures and dependency injection strategies

## Seam Types and Implementation Strategies

### Constructor Injection Seams
- **Primary Constructor Seams**: Classes that can be modified to accept dependencies through their main constructor
- **Factory Method Seams**: Factory methods that can be modified to inject dependencies during object creation
- **Builder Pattern Seams**: Builder classes that can accept dependencies and inject them into constructed objects
- **Dependency Container Seams**: Integration points with dependency injection containers and service locators

### Property/Field Injection Seams  
- **Public Property Seams**: Properties that can be set externally for dependency injection
- **Protected Field Seams**: Protected fields that can be modified in test subclasses
- **Setter Method Seams**: Setter methods that can be used to inject dependencies after object construction
- **Configuration Property Seams**: Configuration objects that can be injected to control behavior

### Method Parameter Seams
- **Strategy Parameter Seams**: Methods that can accept strategy objects to alter behavior
- **Configuration Parameter Seams**: Methods that can accept configuration objects to control execution
- **Callback Parameter Seams**: Methods that can accept callback functions or delegates for behavior modification
- **Context Parameter Seams**: Methods that can accept context objects containing multiple dependencies

### Interface Extraction Seams
- **Concrete Class Abstraction**: Concrete classes that can be abstracted behind interfaces
- **Static Method Abstraction**: Static method calls that can be wrapped behind instance interfaces
- **Library Facade Seams**: Third-party library usage that can be wrapped behind custom interfaces
- **System Resource Seams**: System resource access that can be abstracted behind testable interfaces

## Seam Prioritization and Risk Assessment

### High Priority Seams (Implement First)
- **Business Critical Dependencies**: Seams in payment processing, authentication, and core business logic
- **External Service Dependencies**: Network calls, database access, and third-party API integrations
- **Hard-to-Test Dependencies**: File system access, system time, random number generation
- **Frequently Changing Dependencies**: Components that change often and need stable test isolation

### Medium Priority Seams (Implement Second)
- **Internal Service Dependencies**: Business service dependencies that complicate testing
- **Configuration Dependencies**: Settings and configuration access that needs test control
- **Event System Dependencies**: Event publishing and subscription that needs test isolation
- **Utility Dependencies**: Utility and helper dependencies that affect test determinism

### Low Priority Seams (Implement Last)
- **Stable Internal Dependencies**: Rarely changing internal dependencies with low testing impact
- **Simple Utility Dependencies**: Basic utility functions with minimal testing complications
- **Legacy Compatibility Seams**: Dependencies maintained for legacy compatibility
- **Performance-Critical Seams**: Dependencies where injection might impact performance

## Seam Implementation Planning

### Seam Modification Safety Assessment
1. **Change Impact Analysis**: Assess the risk and scope of modifying each identified seam
2. **Backward Compatibility**: Ensure seam modifications maintain existing functionality
3. **Performance Impact**: Evaluate performance implications of dependency injection
4. **Code Complexity**: Assess whether seam modifications increase or decrease code complexity

### Dependency Injection Strategy
- **Constructor Injection Strategy**: Plan for constructor-based dependency injection implementation
- **Interface Abstraction Strategy**: Design interfaces and abstractions for concrete dependencies
- **Mock Integration Strategy**: Plan integration with mock generation and test double creation
- **Gradual Implementation Strategy**: Phased approach to implementing dependency injection across seams

### Testing Integration Planning
- **Test Double Integration**: Plan how mocks and test doubles will be injected at identified seams
- **Test Setup Automation**: Design automated test setup that leverages dependency injection
- **Test Isolation Strategy**: Ensure proper test isolation through effective seam utilization
- **Test Maintenance Strategy**: Plan for maintaining tests as seams evolve and change

## Seam Documentation and Tracking

### Seam Registry Creation
1. **Seam Catalog**: Comprehensive catalog of all identified seams with metadata and classification
2. **Seam Prioritization**: Documented prioritization of seams based on business impact and implementation complexity
3. **Implementation Status**: Tracking system for seam implementation progress and completion
4. **Seam Dependencies**: Documentation of dependencies between different seams and injection points

### Seam Analysis Results
- **Seam Count and Distribution**: Statistical analysis of identified seams by type and priority
- **Implementation Complexity Assessment**: Detailed analysis of implementation complexity for each seam
- **Test Impact Projection**: Projected improvement in testability and test coverage from seam implementation
- **Refactoring Risk Assessment**: Risk analysis for implementing dependency injection at each seam

## Success Criteria
- Comprehensive catalog of all dependency injection seams identified and classified
- Seam prioritization completed based on business impact and implementation complexity
- Detailed implementation strategy developed for high-priority seams
- Integration plan established for mock generation and test double injection
- Complete documentation created for seam maintenance and evolution

## Integration
- Documents seam identification completion status and analysis results
- Provides seam catalog for mock generation and dependency injection implementation
- Establishes foundation for safe dependency injection and test isolation
- Enables targeted refactoring efforts focused on high-impact dependency seams

## Rollback
Seam identification is analysis-only and requires no rollback procedures. If seam analysis needs revision:
1. Update seam classification criteria and re-analyze with corrected parameters
2. Revise prioritization based on new business requirements or technical constraints
3. Refine seam implementation strategies based on architectural changes or new insights