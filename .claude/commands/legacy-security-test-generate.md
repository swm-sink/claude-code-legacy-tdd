---
allowed-tools: ["Bash", "Glob", "Grep", "LS", "Read", "Write", "Edit", "MultiEdit", "WebSearch"]
description: "Generate comprehensive security tests to validate security controls and ensure transformations don't introduce vulnerabilities"
---

# Legacy Security Test Generation - Comprehensive Security Validation

## Dynamic Context Gathering

!find . -name "*.py" -o -name "*.js" -o -name "*.java" -o -name "*.swift" -o -name "*.ts" | xargs grep -l "password\|auth\|token\|encrypt\|decrypt" | head -10

!grep -r "input\|user.*data\|request\|response" . --include="*.py" --include="*.js" --include="*.java" --include="*.swift" --include="*.ts" | head -10

!ls -la security-tests/ vulnerability-tests/ || echo "No security testing directories found"

## File References

@security-baseline.json @vulnerability-analysis.json @owasp-asvs-compliance.json @authentication-flows.json

**Command**: `/legacy-security-test-generate`  
**Phase**: Quality Assurance  
**Coverage Requirement**: 90%+ coverage + security baseline established (blocks without this)  
**Risk Level**: Low (security test creation only, no production code changes)

## Objective

Generate comprehensive security tests for legacy code to validate security controls, detect vulnerabilities, and ensure that transformations don't introduce security regressions while maintaining OWASP ASVS 5.0 compliance.

## Context

Security testing is critical for legacy transformation to ensure that improvements don't introduce vulnerabilities and that existing security controls continue to function correctly. This command creates automated security tests based on the established security baseline.

## Security Test Strategy Tasks

1. **Prerequisite Validation**:
   - Verify that 90%+ test coverage requirement has been met and security baseline is established
   - Confirm that comprehensive security analysis has been completed from `/legacy-security-baseline`
   - Validate that authentication and authorization patterns have been identified and documented
   - Check that existing security controls and vulnerabilities are catalogued and understood

2. **Security Test Scope Analysis**:
   - **Authentication Testing**: Validate login, session management, password handling, and multi-factor authentication
   - **Authorization Testing**: Test access controls, role-based permissions, and privilege escalation prevention
   - **Input Validation Testing**: Validate protection against injection attacks, XSS, and malicious input
   - **Data Protection Testing**: Test encryption, secure storage, and sensitive data handling

3. **Vulnerability Test Planning**:
   - **OWASP Top 10 Coverage**: Create tests for current OWASP Top 10 security risks
   - **Legacy-Specific Vulnerabilities**: Test for common legacy code security issues
   - **Framework-Specific Security**: Test platform-specific security controls and vulnerabilities
   - **Business Logic Security**: Validate security of complex business workflows and processes

4. **Security Test Automation Strategy**:
   - **Automated Security Scanning**: Integrate SAST, DAST, and dependency scanning tools
   - **Penetration Testing Automation**: Create automated security attack simulations
   - **Security Regression Testing**: Ensure transformations don't introduce new vulnerabilities
   - **Compliance Validation**: Automate OWASP ASVS 5.0 compliance checking

## Authentication and Session Security Testing

### Authentication Mechanism Testing

1. **Password Security Validation**:
   - Test password strength requirements and validation logic
   - Validate secure password storage using appropriate hashing algorithms (bcrypt, Argon2)
   - Test password reset functionality for security vulnerabilities
   - Validate account lockout and brute force protection mechanisms

2. **Session Management Security**:
   - Test session token generation for randomness and unpredictability
   - Validate session expiration, timeout, and invalidation mechanisms
   - Test session fixation and session hijacking protection
   - Validate secure session storage and transmission (secure, httpOnly, sameSite flags)

3. **Multi-Factor Authentication Testing**:
   - Test MFA implementation for security and usability
   - Validate backup authentication methods and recovery procedures
   - Test MFA bypass attempts and fallback security
   - Validate integration with external authentication providers

4. **Authentication Flow Security**:
   - Test for authentication bypass vulnerabilities
   - Validate proper error handling without information disclosure
   - Test for timing attacks and enumeration vulnerabilities
   - Validate secure credential transmission and storage

## Authorization and Access Control Testing

### Role-Based Access Control Validation

1. **Permission System Testing**:
   - Test role assignment and permission inheritance mechanisms
   - Validate least privilege principle implementation
   - Test horizontal and vertical privilege escalation prevention
   - Validate access control matrix and permission boundaries

2. **Resource Protection Testing**:
   - Test access controls for sensitive data and functionality
   - Validate object-level authorization and data ownership
   - Test for insecure direct object references (IDOR)
   - Validate business function access controls

3. **Administrative Function Security**:
   - Test administrative interface access controls
   - Validate administrative function authorization
   - Test for administrative privilege abuse vulnerabilities
   - Validate administrative audit trails and logging

## Input Validation and Injection Testing

### Injection Attack Prevention

1. **SQL Injection Testing**:
   - Test all database query construction for SQL injection vulnerabilities
   - Validate parameterized query usage and input sanitization
   - Test stored procedure and dynamic SQL security
   - Validate database error handling and information disclosure prevention

2. **Cross-Site Scripting (XSS) Prevention**:
   - Test all user input rendering for XSS vulnerabilities
   - Validate output encoding and Content Security Policy implementation
   - Test for stored, reflected, and DOM-based XSS vulnerabilities
   - Validate JavaScript injection and HTML injection prevention

3. **Command Injection Testing**:
   - Test system command execution for command injection vulnerabilities
   - Validate input sanitization for system calls and shell execution
   - Test for file path traversal and directory listing vulnerabilities
   - Validate safe file handling and upload functionality

4. **NoSQL and LDAP Injection Testing**:
   - Test NoSQL query construction for injection vulnerabilities
   - Validate LDAP query security and input sanitization
   - Test for XML injection and XXE (XML External Entity) vulnerabilities
   - Validate API input validation and serialization security

## Data Protection and Encryption Testing

### Cryptographic Implementation Validation

1. **Encryption at Rest Testing**:
   - Test database encryption and key management
   - Validate file system encryption and secure storage
   - Test encryption key rotation and lifecycle management
   - Validate backup encryption and secure recovery procedures

2. **Encryption in Transit Testing**:
   - Test TLS/SSL implementation and configuration
   - Validate certificate management and validation
   - Test for protocol downgrade and cipher suite vulnerabilities
   - Validate secure communication channel establishment

3. **Cryptographic Algorithm Validation**:
   - Test for use of deprecated or weak cryptographic algorithms
   - Validate random number generation quality and entropy
   - Test cryptographic key strength and generation procedures
   - Validate digital signature implementation and verification

### Sensitive Data Handling

1. **Personal Information Protection**:
   - Test PII handling and privacy protection mechanisms
   - Validate data minimization and retention policies
   - Test for sensitive data exposure in logs and error messages
   - Validate data anonymization and pseudonymization implementations

2. **Financial Data Security**:
   - Test payment card data handling for PCI DSS compliance
   - Validate financial transaction security and integrity
   - Test for financial data exposure and leakage
   - Validate secure payment processing workflows

## Framework-Specific Security Testing

### iOS/Swift Security Testing
- Test iOS Keychain integration and secure storage implementation
- Validate App Transport Security (ATS) configuration and enforcement
- Test biometric authentication integration and fallback mechanisms
- Validate iOS app sandbox security and data protection classes

### JavaScript/Node.js Security Testing
- Test Node.js dependency vulnerabilities using npm audit and security scanners
- Validate Express.js security middleware configuration (helmet, cors, rate limiting)
- Test for prototype pollution and JavaScript injection vulnerabilities
- Validate JWT implementation and token security

### Python Security Testing
- Test Python-specific vulnerabilities (pickle deserialization, code injection)
- Validate Django/Flask security configurations and middleware
- Test for Python path traversal and import injection vulnerabilities
- Validate database ORM security and query construction

### Java Security Testing
- Test Java deserialization vulnerabilities and secure coding practices
- Validate Spring Security configuration and access controls
- Test for Java-specific injection vulnerabilities (EL injection, OGNL injection)
- Validate Java cryptographic API usage and security

## Automated Security Testing Implementation

### Security Scanning Integration

1. **Static Application Security Testing (SAST)**:
   - Integrate SAST tools for automated source code vulnerability scanning
   - Configure rule sets for legacy code patterns and framework-specific vulnerabilities
   - Set up automated scanning for transformation validation and regression detection
   - Create custom rules for business-specific security requirements

2. **Dynamic Application Security Testing (DAST)**:
   - Set up automated penetration testing for running applications
   - Configure security crawling and vulnerability detection for web interfaces
   - Test API security and endpoint vulnerability scanning
   - Validate runtime security behavior and configuration

3. **Dependency Vulnerability Scanning**:
   - Automate third-party dependency vulnerability scanning
   - Set up alerts for new vulnerabilities in project dependencies
   - Test for known vulnerabilities in legacy library versions
   - Validate license compliance and security update management

### Security Test Automation Framework

1. **Penetration Testing Automation**:
   - Create automated security attack simulations for common vulnerability patterns
   - Implement fuzzing tests for input validation and error handling
   - Set up automated credential testing and authentication bypass attempts
   - Create business logic security tests for complex workflows

2. **Security Regression Testing**:
   - Integrate security tests into continuous integration for transformation validation
   - Create security smoke tests for rapid security posture validation
   - Set up automated security baseline comparison for transformation impact assessment
   - Implement security monitoring and alerting for ongoing vulnerability detection

## Security Test Quality Assurance

### Security Test Effectiveness Validation

1. **Test Coverage Analysis**:
   - Ensure security tests cover all identified attack vectors and vulnerability types
   - Validate that security tests complement existing functional testing
   - Test security test effectiveness through controlled vulnerability introduction
   - Analyze security test execution and maintenance overhead

2. **False Positive and False Negative Management**:
   - Tune security scanning tools to minimize false positives while maintaining detection accuracy
   - Validate security test results through manual verification and expert review
   - Create security test review processes for ongoing accuracy improvement
   - Document and track security test exceptions and accepted risks

### Compliance and Audit Support

1. **OWASP ASVS 5.0 Compliance Testing**:
   - Create automated tests for OWASP Application Security Verification Standard requirements
   - Validate compliance levels (Level 1, 2, 3) based on application criticality
   - Generate compliance reports and evidence for audit purposes
   - Track compliance improvements through transformation activities

2. **Regulatory Compliance Testing**:
   - Create tests for industry-specific security requirements (HIPAA, SOX, PCI DSS)
   - Validate data protection regulation compliance (GDPR, CCPA)
   - Test security control effectiveness for audit evidence
   - Generate security testing documentation for compliance reporting

## Security Testing Maintenance and Evolution

### Ongoing Security Validation

1. **Threat Intelligence Integration**:
   - Update security tests based on emerging threats and vulnerability research
   - Integrate threat intelligence feeds for proactive security testing
   - Adapt security tests for new attack patterns and techniques
   - Validate security controls against evolving threat landscape

2. **Security Test Lifecycle Management**:
   - Version security tests along with application changes
   - Update security test configurations based on infrastructure changes
   - Maintain security test documentation and runbooks
   - Train development teams on security test interpretation and response

## Success Criteria

- Comprehensive security test suite covering all major vulnerability categories and attack vectors
- Automated security testing integrated into transformation and continuous integration workflows
- OWASP ASVS 5.0 compliance validated through automated testing
- Security regression testing prevents introduction of vulnerabilities during transformation
- Security baseline maintained and improved through ongoing security validation
- Complete documentation and runbooks for security test execution and maintenance

## Integration

- Documents security test generation completion status and coverage analysis
- Provides automated security validation for ongoing transformation activities
- Enables confident security posture maintenance through comprehensive testing
- Establishes security testing baseline for continuous security improvement

## Rollback

Security test generation is enhancement and validation only and requires no rollback procedures:
1. **Test Refinement**: Adjust security test scope and coverage based on validation results
2. **Tool Configuration**: Optimize security scanning tools based on false positive analysis
3. **Coverage Enhancement**: Expand security testing based on threat analysis and vulnerability research
4. **Continuous Improvement**: Integrate security testing learnings into transformation security strategy