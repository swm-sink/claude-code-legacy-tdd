---
allowed-tools: ["Bash", "Glob", "Grep", "LS", "Read"]
description: "Systematically detect code quality and LLM-specific antipatterns for prioritized improvement planning"
---

# Legacy Antipattern Scan - Code Quality and LLM Antipattern Detection

## Dynamic Context Gathering

!find . -name "*.py" -o -name "*.js" -o -name "*.java" -o -name "*.swift" -o -name "*.ts" | xargs wc -l | sort -nr | head -10

!grep -r "class\|def\|function\|method" . --include="*.py" --include="*.js" --include="*.java" --include="*.swift" --include="*.ts" | wc -l

!find . -name "*.py" -o -name "*.js" -o -name "*.java" -o -name "*.swift" -o -name "*.ts" | xargs grep -l "Manager\|Helper\|Utility\|Controller" | head -10

## File References

@.eslintrc @.pylintrc @checkstyle.xml @swiftlint.yml @sonar-project.properties

**Command**: `/legacy-antipattern-scan`  
**Phase**: Initial Assessment  
**Coverage Requirement**: Analysis only (no changes)  
**Risk Level**: Low (read-only analysis)

## Objective

Systematically detect code quality antipatterns and LLM-specific antipatterns that indicate problematic code structure, enabling prioritized improvement planning and preventing issues during AI-assisted development.

## Context

This command identifies both traditional code antipatterns (god objects, long methods, high coupling) and modern LLM antipatterns that can cause issues with AI-assisted development. Essential for understanding code quality baseline and planning systematic improvements.

## Analysis Tasks

1. **God Object Detection**:
   - Identify classes/structures with >20 methods (iOS/Java) or >15 methods (JavaScript/Python)
   - Analyze class responsibilities and look for single responsibility principle violations
   - Find controller/manager/handler classes that indicate multiple responsibilities
   - Calculate severity scores for each god object based on method count and complexity

2. **Long Method Analysis**:
   - Detect methods/functions longer than 50 lines
   - Identify complex methods with high cyclomatic complexity
   - Find deeply nested code structures (>4 levels of indentation)
   - Assess impact on readability and maintainability

3. **Parameter Count Analysis**:
   - Find methods with >5 parameters
   - Identify potential parameter object opportunities
   - Analyze method signatures for coupling issues
   - Recommend parameter grouping strategies

4. **SOLID Principle Violations**:
   - **Single Responsibility**: Classes with multiple concerns (Manager, Helper, Utility patterns)
   - **Open/Closed**: Classes with extensive conditional logic (switch/if chains)
   - **Liskov Substitution**: Override methods with empty/error implementations
   - **Interface Segregation**: Large interfaces/protocols with >10 methods
   - **Dependency Inversion**: Direct dependencies on concrete classes

5. **LLM-Specific Antipatterns**:
   - **Massive Context**: Files >1000 lines that pollute LLM context
   - **Ambiguous Naming**: Variables with unclear names (temp, data, obj, single letters)
   - **Deep Nesting**: Methods with >4 levels of indentation that confuse LLMs
   - **Mixed Abstractions**: Methods mixing system calls with business logic
   - **Implicit Dependencies**: Hidden dependencies through singletons/globals
   - **Magic Values**: Unexplained magic numbers and strings

6. **Framework-Specific Issues**:
   - **iOS/Swift**: Massive View Controllers, force unwrapping, strong reference cycles, synchronous network calls
   - **JavaScript/Node.js**: Callback hell, synchronous operations, global pollution, missing error handling
   - **Java**: Controller god objects, exception swallowing, resource leaks
   - **Python**: Bare except clauses, global overuse, missing type hints

## Scoring and Prioritization

Calculate antipattern severity scores:
- God Objects: 25 points each
- Long Methods: 15 points each  
- High Parameter Count: 10 points each
- Framework Violations: Variable points based on severity
- LLM Antipatterns: 20 points per large file

## Risk Assessment

Based on total score (0-500):
- **0-99**: Low antipattern load, minimal cleanup needed
- **100-199**: Moderate load, standard cleanup recommended
- **200-299**: High load, significant cleanup needed  
- **300+**: Critical load, immediate action required

## Priority Matrix

### Critical Priority (Fix First)
- God objects with >30 methods
- Force unwrapping in business logic
- Critical security violations

### High Priority (Fix Second)  
- Long methods >100 lines
- Large files >1000 lines
- Framework-specific critical issues

### Medium Priority (Fix Third)
- Parameter objects needed
- Dependency injection opportunities
- SOLID violations

### Low Priority (Fix Last)
- Naming improvements
- Documentation additions
- Performance optimizations

## Output Requirements

Create a comprehensive antipattern assessment that includes:

### Severity Breakdown
- Detailed list of god objects with method counts and file locations
- Long methods with line counts and complexity indicators  
- High parameter count methods with suggested parameter objects
- SOLID principle violations with specific examples
- LLM antipatterns with context pollution assessment

### Prioritized Action Plan
- Critical fixes that must be addressed before transformation
- Step-by-step improvement timeline with effort estimates
- Framework-specific recommendations
- Success metrics and targets

### Implementation Guidance
- Specific refactoring patterns for each antipattern type
- Extract Class, Extract Method, Parameter Object patterns
- Dependency injection strategies
- File decomposition approaches

Use your code analysis capabilities to provide specific examples with file names and line numbers where antipatterns are detected.

## Success Criteria
- Complete identification of all code quality antipatterns
- Detection of LLM-specific issues that could cause AI development problems  
- Prioritized action plan for systematic improvement
- Risk assessment for transformation planning
- Framework-specific antipattern identification

## Integration
- Provides priority guidance for god object splitting and method extraction
- Establishes baseline for tracking code quality improvements over time
- Informs safety net creation priorities

## Rollback
Antipattern scanning is read-only and requires no rollback procedures.