---
allowed-tools: ["Bash", "Glob", "Grep", "LS", "Read", "WebSearch"]
description: "Analyze legacy codebase for transformation risks and prioritization using Michael Feathers' principles"
---

# Legacy Code Risk Assessment

## Dynamic Context Gathering

!pwd && echo "\n=== Project Structure ===" && find . -type f -name "*.py" -o -name "*.js" -o -name "*.java" -o -name "*.swift" -o -name "*.ts" -o -name "*.go" -o -name "*.rb" -o -name "*.php" -o -name "*.cs" | head -20

!git status --porcelain && echo "\n=== Git Status ===" && git log --oneline -5

!wc -l $(find . -name "*.py" -o -name "*.js" -o -name "*.java" -o -name "*.swift" -o -name "*.ts" -o -name "*.go" -o -name "*.rb" -o -name "*.php" -o -name "*.cs" | head -10) | sort -nr | head -10

## File References

@package.json @requirements.txt @pom.xml @build.gradle @Gemfile @composer.json @go.mod @project.pbxproj

Analyze this codebase for legacy code transformation risks and prioritization following Michael Feathers' "Working Effectively with Legacy Code" principles.

## Analysis Tasks

1. **Complexity Analysis**: 
   - Examine codebase size and structure
   - Identify largest files (>500 lines) and most complex methods (>50 lines)
   - Calculate approximate cyclomatic complexity for critical components
   - Flag any files approaching god object territory (>20 methods)

2. **Dependency Hotspots**:
   - Identify highly coupled components and dependency clusters
   - Find circular dependencies that could complicate refactoring
   - Locate hard-coded dependencies that need seam identification
   - Map out critical dependency chains

3. **Error-Prone Patterns**:
   - Detect code smells: long methods, large classes, duplicated code
   - Identify SOLID principle violations
   - Find LLM antipatterns: god objects, feature envy, shotgun surgery
   - Look for untestable code patterns (static calls, new operators, global state)

4. **Test Coverage Gaps**:
   - Assess current test coverage and identify untested critical paths
   - Find components with zero or minimal test coverage
   - Identify integration points that lack characterization tests
   - Flag areas where behavioral preservation is critical

5. **Business Criticality Assessment**:
   - Identify core business logic components
   - Find user-facing features that require careful handling
   - Locate components that handle financial, security, or data operations
   - Map out critical paths through the application

## Safety Considerations

- **High-Risk Areas**: Components requiring 100% characterization test coverage before any changes
- **Rollback Critical**: Areas where immediate rollback capability is essential
- **Security Sensitive**: Code handling authentication, authorization, or sensitive data
- **Performance Critical**: Components where performance regression would be unacceptable

## Output Requirements

Create a comprehensive risk assessment report with:

### Risk Categorization
- **HIGH RISK**: Cannot be changed without extensive safety measures
- **MEDIUM RISK**: Requires careful planning and characterization tests
- **LOW RISK**: Can be refactored with standard safety practices

### Transformation Priority
1. **Start Here**: Best candidates for initial refactoring (low risk, high impact)
2. **Second Wave**: Medium complexity components after initial success
3. **Final Phase**: High-risk components requiring maximum safety measures

### Specific Recommendations
- File names and line numbers for god objects
- Specific seam identification opportunities
- Recommended characterization test strategies
- Suggested dependency injection points

## Framework Integration

This assessment establishes the foundation for:
- 90%+ test coverage requirements before transformation
- Seam identification and dependency injection strategy
- Characterization test prioritization
- Rollback procedure planning
- Transformation phase sequencing

Use your deep codebase understanding to provide specific, actionable recommendations with concrete examples and file references.

