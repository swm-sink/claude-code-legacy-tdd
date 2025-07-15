---
allowed-tools: ["Bash", "Glob", "Grep", "LS", "Read", "WebSearch"]
description: "Establish comprehensive security baseline with vulnerability analysis and OWASP ASVS 5.0 compliance assessment"
---

# Legacy Security Baseline - Comprehensive Security Assessment

## Dynamic Context Gathering

!find . -name "*.py" -o -name "*.js" -o -name "*.java" -o -name "*.swift" -o -name "*.ts" | xargs grep -l "password\|secret\|key\|token" | head -10

!grep -r "http://\|localhost\|127\.0\.0\.1" . --include="*.py" --include="*.js" --include="*.java" --include="*.swift" --include="*.ts" --include="*.json" | head -10

!find . -name "*.pem" -o -name "*.key" -o -name "*.crt" -o -name "*.p12" | head -10

## File References

@.env @config.json @settings.py @application.properties @Info.plist @package.json

**Command**: `/legacy-security-baseline`  
**Phase**: Initial Assessment  
**Coverage Requirement**: Security analysis only (no changes)  
**Risk Level**: Low (read-only analysis)

## Objective

Establish a comprehensive security baseline for the legacy codebase, identifying vulnerabilities, documenting current security posture, and providing OWASP ASVS 5.0 compliance assessment to guide security-focused transformation.

## Context

This command performs thorough security analysis including vulnerability scanning, authentication/authorization assessment, data protection review, and compliance checking. Essential for understanding security risks before transformation and ensuring security improvements during refactoring.

## Security Analysis Tasks

1. **Vulnerability Detection**:
   - Scan dependencies for known security vulnerabilities using automated tools
   - Identify hardcoded secrets, API keys, passwords, and tokens in source code
   - Detect insecure communication patterns (HTTP usage, disabled SSL verification)
   - Find injection vulnerabilities (SQL injection, XSS, command injection)

2. **Authentication and Authorization Analysis**:
   - **Password Security**: Analyze password hashing algorithms, storage methods, strength requirements
   - **Session Management**: Review session token generation, storage, expiration, and invalidation
   - **Authorization Controls**: Identify access control patterns, role-based permissions, privilege escalation risks
   - **Biometric/MFA**: Assess multi-factor authentication implementation and security

3. **Input Validation and Injection Protection**:
   - **SQL Injection**: Identify dynamic query construction, missing parameterization
   - **Cross-Site Scripting (XSS)**: Find unsafe HTML rendering, innerHTML usage, missing escaping
   - **Cross-Site Request Forgery (CSRF)**: Check for CSRF token implementation
   - **Input Sanitization**: Analyze user input validation, encoding, and filtering mechanisms

4. **Data Protection and Encryption**:
   - **Encryption Implementation**: Review cryptographic algorithms, key management, secure storage
   - **Weak Cryptography**: Identify MD5, SHA1, deprecated algorithms, insecure implementations
   - **PII Handling**: Find personally identifiable information, logging of sensitive data
   - **Data Storage**: Analyze secure storage patterns (Keychain, encrypted databases)

5. **Network Security Analysis**:
   - **HTTPS/TLS Configuration**: Check SSL/TLS implementation, certificate validation, pinning
   - **API Security**: Review API authentication, rate limiting, security headers
   - **CORS Configuration**: Analyze cross-origin resource sharing settings
   - **Network Communication**: Identify insecure protocols and configurations

6. **OWASP ASVS 5.0 Compliance Assessment**:
   - **V2 Authentication**: Evaluate authentication mechanism security (0-100 score)
   - **V3 Session Management**: Assess session handling security (0-100 score)
   - **V4 Access Control**: Review authorization implementation (0-100 score)
   - **V5 Input Validation**: Analyze input validation effectiveness (0-100 score)
   - **V6 Cryptography**: Evaluate cryptographic implementation strength (0-100 score)
   - **V7 Error Handling**: Review error handling and logging security (0-100 score)
   - **V8 Data Protection**: Assess data protection mechanisms (0-100 score)
   - **V9 Communication**: Evaluate network communication security (0-100 score)

## Security Risk Scoring

Calculate overall security baseline score (0-100) based on OWASP ASVS compliance:
- **80-100**: OWASP ASVS Level 1 Compliance achieved
- **60-79**: Partial compliance, good security foundation
- **40-59**: Basic compliance, minimal security controls
- **0-39**: Non-compliant, major security gaps

## Critical Vulnerability Categories

### Critical Priority (Fix Immediately)
- Hardcoded secrets and credentials in source code
- SQL injection and command injection vulnerabilities
- Insecure communication (HTTP usage, disabled SSL verification)
- Authentication bypass vulnerabilities

### High Priority (Fix This Sprint)
- Weak authentication mechanisms (insufficient password hashing)
- Insecure session management (missing secure flags, no CSRF protection)
- Missing authorization controls (unprotected endpoints)
- Cross-site scripting (XSS) vulnerabilities

### Medium Priority (Fix Next Sprint)
- Weak cryptographic implementations (deprecated algorithms)
- Insufficient error handling (information disclosure)
- Data protection gaps (insecure storage, missing encryption)
- Missing security headers and configurations

## Framework-Specific Security Patterns

### iOS/Swift Security
- Keychain usage for credential storage
- App Transport Security (ATS) configuration
- Biometric authentication implementation
- Certificate pinning for network security
- Data protection attributes for file security

### JavaScript/Node.js Security
- Environment variable usage for secrets
- JWT token handling and validation
- Express.js security middleware implementation
- CORS configuration security
- Input validation library usage

### Python Security
- Password hashing with bcrypt/argon2
- Django/Flask security configurations
- SQL injection prevention with ORMs
- Secret management best practices

### Java Security
- Spring Security configuration
- OWASP dependency checking
- Exception handling security
- Resource leak prevention

## Output Requirements

Create a comprehensive security baseline assessment that includes:

### Vulnerability Assessment
- Complete list of identified security vulnerabilities with severity ratings
- Hardcoded secrets inventory with locations and remediation steps
- Injection vulnerability analysis with specific examples
- Network security configuration review

### OWASP ASVS Compliance Report
- Detailed scoring for each verification category (V2-V9)
- Overall compliance level determination
- Gap analysis with specific recommendations
- Compliance roadmap with implementation timeline

### Security Improvement Roadmap
- Critical priority fixes requiring immediate attention
- High-priority security controls for current sprint
- Medium-priority improvements for future sprints
- Long-term security enhancement recommendations

### Implementation Guidance
- Specific remediation steps for each vulnerability type
- Secure coding patterns and best practices
- Security testing requirements and validation approaches
- Compliance monitoring and maintenance procedures

Use your security analysis capabilities to provide specific examples with file names and line numbers where security issues are identified.

## Success Criteria
- Complete security vulnerability assessment performed
- OWASP ASVS 5.0 compliance level established
- Critical security issues identified and prioritized
- Comprehensive security improvement roadmap created
- Security baseline documented for transformation planning

## Integration
- Provides security requirements for safety net creation
- Establishes security monitoring requirements for transformation
- Guides security-focused characterization testing

## Rollback
Security baseline assessment is read-only and requires no rollback procedures.