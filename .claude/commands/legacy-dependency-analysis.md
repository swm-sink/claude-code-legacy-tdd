---
allowed-tools: ["Bash", "Glob", "Grep", "LS", "Read"]
description: "Analyze dependency coupling, identify circular dependencies, and discover seam opportunities for dependency injection"
---

# Legacy Dependency Analysis - Coupling and Architecture Assessment

## Dynamic Context Gathering

!find . -name "*.py" -o -name "*.js" -o -name "*.java" -o -name "*.swift" -o -name "*.ts" -o -name "*.go" | xargs grep -l "import\|require\|#include" | head -20

!grep -r "singleton\|shared\|default\|instance" . --include="*.py" --include="*.js" --include="*.java" --include="*.swift" --include="*.ts" | head -10

!find . -name "*.py" -o -name "*.js" -o -name "*.java" -o -name "*.swift" -o -name "*.ts" | xargs grep -l "global\|static" | head -10

## File References

@package.json @requirements.txt @pom.xml @build.gradle @Gemfile @go.mod @project.pbxproj @tsconfig.json

**Command**: `/legacy-dependency-analysis`  
**Phase**: Initial Assessment  
**Coverage Requirement**: Analysis only (no changes)  
**Risk Level**: Low (read-only analysis)

## Objective

Analyze dependency coupling, identify circular dependencies, map architectural layers, and discover seam opportunities for dependency injection to make legacy code testable and maintainable.

## Context

This command provides comprehensive analysis of how components depend on each other, identifies tight coupling that makes testing difficult, and finds opportunities to introduce seams for dependency injection. Essential for planning safe transformation approaches.

## Analysis Tasks

1. **Import and Dependency Mapping**:
   - Analyze import statements and require/include patterns across all source files
   - Map direct dependencies between modules, packages, and external libraries
   - Identify most heavily used dependencies and third-party libraries
   - Calculate dependency distribution and usage patterns by architectural layers

2. **Circular Dependency Detection**:
   - Identify files and modules that reference each other creating cycles
   - Detect bidirectional dependencies that prevent clean separation
   - Map complex dependency chains that lead to circular references
   - Find subtle circular dependencies through indirect references

3. **Coupling Analysis**:
   - **Singleton Usage**: Identify files using .shared, .default, .instance patterns
   - **Global State**: Find static variables, global objects, and shared mutable state
   - **Hard-coded Dependencies**: Locate direct instantiation of external services (URLSession, FileManager, console.log, System.out)
   - **Calculate Coupling Score**: Percentage of files showing high coupling patterns

4. **Seam Identification for Dependency Injection**:
   - **Constructor Seams**: Classes/functions that could accept dependencies through parameters
   - **Method Parameter Seams**: Methods that could receive strategy objects or configuration
   - **Property/Field Seams**: Instance variables that could be injected instead of hard-coded
   - **Interface Extraction**: Opportunities to create abstractions for concrete dependencies

5. **Testability Assessment**:
   - **Untestable Patterns**: Direct filesystem access, network calls, UI dependencies without abstractions
   - **Current Test Infrastructure**: Ratio of test files to source files, existing mock infrastructure
   - **Testing Barriers**: Components that cannot be unit tested due to hard dependencies
   - **Mock Opportunities**: External dependencies that need mock implementations

6. **Architecture Layer Analysis**:
   - **Layer Structure**: Identify architectural patterns (MVC, MVVM, layered architecture)
   - **Cross-Layer Violations**: Models importing UI frameworks, Views importing business logic
   - **Dependency Direction**: Verify dependencies flow in correct direction through architectural layers
   - **Boundary Violations**: Components that violate architectural separation of concerns

## Coupling Risk Assessment

Calculate dependency injection priority based on coupling severity:
- **0-15%**: Low coupling, manageable dependency structure
- **16-30%**: Medium coupling, some dependency injection recommended  
- **31%+**: High coupling, significant dependency injection needed

## Dependency Injection Strategy

### Phase 1: Critical Dependencies (Start Here)
- Replace singletons in business-critical code (payment, authentication, security)
- Create protocol/interface abstractions for external dependencies
- Implement constructor injection for main service classes

### Phase 2: Testing Infrastructure
- Build comprehensive mock infrastructure for all external dependencies
- Set up dependency injection container/framework
- Configure test environments with mock implementations

### Phase 3: Architecture Improvement
- Implement dependency inversion principle throughout codebase
- Split god objects with many dependencies into focused services
- Remove circular dependencies through architectural refactoring

## Framework-Specific Recommendations

### iOS/Swift
- URLSession → NetworkServiceProtocol
- FileManager → FileStorageProtocol
- UserDefaults → PreferencesProtocol
- NotificationCenter → EventBusProtocol

### JavaScript/Node.js
- fs module → FileSystemInterface
- http module → HttpClientInterface  
- Database connections → DatabaseInterface
- External APIs → ApiClientInterface

### Java
- File system → FileSystemInterface
- Network operations → NetworkInterface
- Database access → RepositoryInterface

## Output Requirements

Create a comprehensive dependency analysis that includes:

### Dependency Mapping
- Complete import/dependency graph showing relationships between modules
- Most heavily used dependencies with usage counts
- Third-party vs first-party dependency breakdown
- Package/module dependency distribution

### Coupling Assessment
- Detailed list of singleton usage with file locations and business criticality
- Global state usage analysis with testability impact
- Hard-coded dependency instances with injection opportunities
- Overall coupling score with risk assessment

### Injection Opportunities
- Constructor seam identification with specific examples
- Method parameter opportunities for strategy injection
- Property/field injection possibilities
- Interface extraction recommendations for concrete dependencies

### Architecture Analysis
- Current architectural layer structure and violations
- Cross-layer dependency violations with specific examples
- Recommended architectural improvements
- Dependency flow correction strategies

Use your code analysis capabilities to provide specific examples with file names and line numbers where coupling issues and injection opportunities are identified.

## Success Criteria
- Complete mapping of all dependencies and import relationships
- Identification of circular dependencies and coupling issues
- Discovery of seam opportunities for dependency injection
- Architecture layer analysis and violation detection
- Actionable plan for implementing dependency injection

## Integration
- Provides input for seam identification and mock generation commands
- Establishes baseline for measuring coupling reduction over time
- Guides safe transformation approach based on coupling complexity

## Rollback
Dependency analysis is read-only and requires no rollback procedures.