# Legacy Code Assessment - Comprehensive Analysis

**Command**: `/legacy-assess`  
**Phase**: Initial Assessment  
**Coverage Requirement**: Current state analysis + 90% minimum target establishment  
**Risk Level**: Low (read-only analysis)

## Objective

Perform complete legacy codebase analysis combining risk assessment, test coverage analysis, dependency mapping, antipattern detection, and security baseline in a single comprehensive command that establishes the foundation for all subsequent transformation work.

## Context

This is the MANDATORY first command that must be run before any legacy code work. It establishes the complete picture of the codebase state and sets the 90%+ coverage requirements for all future work. This command integrates all assessment activities into a unified analysis.

## Comprehensive Assessment Tasks

1. **Project Type Detection and Baseline Setup**:
   - Detect project type (iOS/Swift, JavaScript/Node.js, Java, Python, other) based on file extensions and project structure
   - Identify build system (Xcode, npm/yarn, Maven/Gradle, pip/conda) and testing frameworks in use
   - Establish technology-specific analysis patterns appropriate for the detected environment
   - Configure baseline metrics collection appropriate for the project type

2. **Codebase Structure and Complexity Analysis**:
   - Analyze overall codebase size, file count, and directory structure organization
   - Identify largest files (>500 lines) and calculate approximate complexity metrics
   - Find potential god objects by counting methods per class/module (>20 methods flagged)
   - Assess architectural patterns and identify potential structural issues

3. **Risk Assessment and Critical Component Identification**:
   - Identify business-critical components (authentication, payment, data processing, user-facing features)
   - Locate high-risk patterns (force unwrapping, unhandled exceptions, unsafe operations, hardcoded values)
   - Find complex logic that requires careful handling (algorithms, state machines, validation logic)
   - Assess transformation difficulty based on coupling, complexity, and business criticality

4. **Current Test Coverage Assessment**:
   - Analyze existing test suite structure and organization (unit tests, integration tests, end-to-end tests)
   - Evaluate current test coverage using project-appropriate tools and methods
   - Identify components with zero or minimal test coverage, especially business-critical ones
   - Calculate coverage gaps needed to reach 90% minimum requirement

5. **Dependency and Coupling Analysis**:
   - Map external dependencies (third-party libraries, frameworks, system services)
   - Identify internal coupling patterns (singleton usage, static dependencies, global state)
   - Find circular dependencies and architectural violations that complicate refactoring
   - Assess dependency injection opportunities and seam identification potential

6. **Code Quality and Antipattern Detection**:
   - Detect traditional antipatterns (god objects, long methods, high parameter counts)
   - Identify LLM-specific antipatterns (massive files >1000 lines, deep nesting, ambiguous naming)
   - Find SOLID principle violations and architectural boundary violations
   - Assess code maintainability and readability for AI-assisted development

7. **Security Baseline Establishment**:
   - Scan for obvious security vulnerabilities (hardcoded secrets, insecure communications, injection risks)
   - Identify authentication and authorization patterns that need careful handling
   - Find data protection and encryption implementations that require validation
   - Establish security baseline for tracking improvements during transformation

8. **Transformation Readiness Assessment**:
   - Calculate overall readiness score based on coverage, complexity, and risk factors
   - Identify immediate blockers that must be addressed before transformation can begin
   - Prioritize components for initial characterization testing and safety net creation
   - Establish recommended transformation sequence based on risk and business impact

## Assessment Integration and Reporting

### Comprehensive Risk and Readiness Scoring

Create an overall assessment that combines multiple factors:

**Coverage Readiness (0-100 points)**:
- Current test coverage percentage and quality assessment
- Gap analysis for reaching 90% minimum requirement
- Test infrastructure maturity and framework suitability

**Complexity Assessment (0-100 points)**:
- Codebase size and structural complexity evaluation
- God object and antipattern density scoring
- Architectural quality and coupling assessment

**Security Posture (0-100 points)**:
- Security vulnerability assessment and baseline establishment
- Authentication/authorization implementation quality
- Data protection and encryption usage evaluation

**Transformation Readiness (0-100 points)**:
- Overall readiness for safe legacy transformation
- Immediate blocker identification and resolution requirements
- Recommended transformation approach and sequencing

### Assessment Report Requirements

Create a comprehensive assessment report that includes:

**Executive Summary**:
- Overall transformation readiness score and recommendation (GO/NO-GO decision)
- Critical issues that must be addressed before transformation can begin
- Estimated effort required to achieve transformation readiness

**Detailed Analysis Results**:
- Complete breakdown of coverage gaps with specific file and component identification
- Risk assessment with prioritized list of high-risk components requiring careful handling
- Antipattern inventory with specific examples and remediation recommendations
- Security baseline with vulnerability assessment and improvement recommendations

**Transformation Roadmap**:
- Recommended sequence for achieving 90% coverage requirement
- Priority order for characterization testing based on business criticality and risk
- Suggested approach for dependency injection and seam identification
- Timeline estimates for reaching transformation readiness

**Technology-Specific Recommendations**:
- Framework-appropriate testing strategies and tool recommendations
- Platform-specific best practices for coverage improvement and safety net creation
- Recommended patterns for mock generation and dependency injection
- Security considerations specific to the detected technology stack

## Success Criteria

- Complete codebase analysis performed with technology-appropriate methods
- 90% coverage target established with clear gap analysis and remediation plan
- Critical risks identified and prioritized with specific component-level recommendations
- Security baseline documented with comprehensive vulnerability assessment
- Clear go/no-go decision provided with actionable next steps for transformation readiness

## Integration

- Establishes assessment results and readiness status for subsequent analysis
- Establishes coverage baseline and gap analysis for all subsequent safety infrastructure commands
- Provides risk-based prioritization for characterization testing and mock generation
- Blocks unsafe operations until coverage requirements are met and critical issues are resolved

## Rollback

Assessment is read-only analysis and requires no rollback procedures. If assessment reveals critical issues, address them through the appropriate safety infrastructure commands before proceeding with transformation.