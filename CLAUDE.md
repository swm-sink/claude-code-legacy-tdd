# CLAUDE.md - Legacy Code TDD Framework for Agentic Coding

This file provides guidance to Claude Code when working with the Legacy Code TDD Framework - a comprehensive system for safely transforming legacy codebases using Test-Driven Development principles enhanced for agentic coding.

## 🎯 Framework Mission

**SAFETY FIRST**: Build test infrastructure BEFORE any refactoring. Follow Michael Feathers' principles while integrating cutting-edge 2025 practices for agentic coding, security-first development, and LLM antipattern prevention.

## 🧠 Enhanced Claude 4 Behavior Patterns

<claude_4_behavior interpretation="STRICT_ENFORCEMENT">
  <legacy_code_mode enforcement="MANDATORY">
    <safety_first>NEVER modify legacy code without 70%+ characterization test coverage</safety_first>
    <characterization_principle>Document actual behavior, not intended behavior</characterization_principle>
    <rollback_ready>Every change must have immediate rollback capability</rollback_ready>
    <security_baseline>Establish security state before any modifications</security_baseline>
  </legacy_code_mode>
  
  <thinking_modes>
    <ultrathink trigger="complex legacy analysis, architectural decisions, security assessments">
      Deploy maximum thinking budget for legacy code analysis, dependency mapping, and risk assessment
    </ultrathink>
    <think_hard trigger="command execution planning, safety validation">
      Extended analysis for multi-step command sequences and safety verification
    </think_hard>
    <think trigger="standard legacy code tasks">
      Standard thinking for routine characterization and test creation
    </think>
  </thinking_modes>
  
  <parallel_execution_requirements>
    <assessment_phase>Batch all analysis commands: /legacy-assess-risk, /legacy-coverage-report, /legacy-dependency-analysis</assessment_phase>
    <safety_creation>Parallel execution of characterization tests across multiple modules</safety_creation>
    <validation_phase>Concurrent mutation testing, property testing, and security validation</validation_phase>
  </parallel_execution_requirements>
</claude_4_behavior>

## 📋 Mandatory Command Execution Workflow

<workflow_enforcement>
  <phase_1_assessment prerequisite="none" blocking="true">
    <mandatory_sequence>
      1. /legacy-assess-risk
      2. /legacy-coverage-report  
      3. /legacy-dependency-analysis
      4. /legacy-antipattern-scan
      5. /legacy-security-baseline
    </mandatory_sequence>
    <completion_criteria>All risks documented, baseline established, priorities clear</completion_criteria>
    <blocks_until_complete>Phase 2 commands are BLOCKED until assessment is 100% complete</blocks_until_complete>
  </phase_1_assessment>

  <phase_2_safety_net prerequisite="assessment_complete" blocking="true">
    <mandatory_sequence>
      1. /legacy-characterize-behavior (for all critical components)
      2. /legacy-safety-net-create
      3. /legacy-seam-identify
      4. /legacy-rollback-prepare
    </mandatory_sequence>
    <coverage_requirement>70% minimum characterization test coverage</coverage_requirement>
    <blocks_until_complete>Transformation commands BLOCKED until safety net complete</blocks_until_complete>
  </phase_2_safety_net>

  <phase_3_preparation prerequisite="safety_net_complete">
    <dependency_breaking>
      1. /legacy-mock-generator
      2. /legacy-dependency-inject  
      3. /legacy-extract-interface
    </dependency_breaking>
    <testability_enhancement>Make legacy code testable through seams and injection</testability_enhancement>
  </phase_3_preparation>

  <phase_4_transformation prerequisite="preparation_complete">
    <safe_modification>
      1. /legacy-sprout-method (preferred for new features)
      2. /legacy-sprout-class (for significant new functionality)
      3. /legacy-god-object-split (with comprehensive tests)
      4. /legacy-method-extract (incremental refactoring)
      5. /legacy-antipattern-fix (systematic improvement)
    </safe_modification>
    <validation_requirement>Every change must validate against characterization tests</validation_requirement>
  </phase_4_transformation>

  <phase_5_validation prerequisite="transformation_in_progress">
    <quality_assurance>
      1. /legacy-mutation-test (validate test effectiveness)
      2. /legacy-property-test (verify algorithmic properties)  
      3. /legacy-security-test-generate (security regression testing)
    </quality_assurance>
  </phase_5_validation>
</workflow_enforcement>

## 🛡️ LLM Antipattern Prevention System

<antipattern_enforcement enforcement="MANDATORY">
  <god_object_prevention>
    <max_methods_per_class>20</max_methods_per_class>
    <auto_detection>Scan for classes exceeding limits during any modification</auto_detection>
    <blocking_behavior>REFUSE to create or modify classes that violate limits</blocking_behavior>
    <alternative_suggestion>Suggest /legacy-god-object-split when limits approached</alternative_suggestion>
  </god_object_prevention>
  
  <method_complexity_limits>
    <max_lines_per_method>50</max_lines_per_method>
    <max_parameters>5</max_parameters>
    <max_nesting_depth>4</max_nesting_depth>
    <cyclomatic_complexity>10</cyclomatic_complexity>
  </method_complexity_limits>
  
  <solid_principle_enforcement>
    <single_responsibility>Each class must have one clear responsibility</single_responsibility>
    <open_closed>Prefer extension over modification</open_closed>
    <liskov_substitution>Maintain behavioral substitutability</liskov_substitution>
    <interface_segregation>Create focused, cohesive interfaces</interface_segregation>
    <dependency_inversion>Depend on abstractions, not concretions</dependency_inversion>
  </solid_principle_enforcement>
</antipattern_enforcement>

## 🔐 Security-First TDD (Test Driven Security)

<security_requirements enforcement="MANDATORY">
  <security_tests_first>
    <vulnerability_baseline>Document current security state before changes</vulnerability_baseline>
    <security_characterization>Create tests for existing security behavior (even if flawed)</security_characterization>
    <threat_modeling>Identify security requirements before implementation</threat_modeling>
    <owasp_compliance>Follow OWASP ASVS 5.0 guidelines</owasp_compliance>
  </security_tests_first>
  
  <security_patterns>
    <input_validation>All external input must be validated and tested</input_validation>
    <authentication>All auth flows require comprehensive test coverage</authentication>
    <authorization>Access control logic must be thoroughly tested</authorization>
    <cryptography>Crypto usage must follow current best practices</cryptography>
    <secrets_management>No hardcoded secrets, secure storage patterns</secrets_management>
  </security_patterns>
  
  <security_testing>
    <sast_integration>Static analysis security testing</sast_integration>
    <dast_validation>Dynamic security testing for running systems</dast_validation>
    <penetration_testing>Security testing for critical components</penetration_testing>
    <compliance_validation>Automated compliance checking</compliance_validation>
  </security_testing>
</security_requirements>

## 📊 Coverage and Quality Requirements

<quality_gates enforcement="BLOCKING">
  <test_coverage>
    <minimum_before_changes>70%</minimum_before_changes>
    <target_for_new_code>95%</target_for_new_code>
    <critical_paths>100%</critical_paths>
    <security_components>100%</security_components>
  </test_coverage>
  
  <test_effectiveness>
    <mutation_testing_score>90%+</mutation_testing_score>
    <characterization_coverage>All legacy behaviors documented</characterization_coverage>
    <property_testing>Complex algorithms have property-based tests</property_testing>
    <approval_testing>Complex outputs have golden master tests</approval_testing>
  </test_effectiveness>
  
  <safety_validation>
    <rollback_capability>Every change must be immediately reversible</rollback_capability>
    <behavioral_regression>Characterization tests must continue passing</behavioral_regression>
    <performance_regression>Performance must not degrade</performance_regression>
    <security_regression>Security baseline must not be violated</security_regression>
  </safety_validation>
</quality_gates>

## 🤖 Agent Coordination Patterns

<agent_coordination>
  <coordination_file>/Users/smenssink/Documents/Github/legacy-code-tdd/AGENTS-COMMS/coordination.json</coordination_file>
  
  <status_updates>
    <after_command_execution>Update coordination.json with results and next steps</after_command_execution>
    <before_phase_transition>Validate all phase requirements met</before_phase_transition>
    <on_blocker_detection>Log blockers and recommended resolution</on_blocker_detection>
  </status_updates>
  
  <parallel_agent_patterns>
    <research_continuous>Research agent provides ongoing intelligence</research_continuous>
    <development_coordination>Development agents coordinate through central hub</development_coordination>
    <validation_concurrent>QA and testing agents work in parallel with development</validation_concurrent>
  </parallel_agent_patterns>
</agent_coordination>

## 🧪 Testing Infrastructure Patterns

<testing_infrastructure>
  <characterization_testing>
    <golden_master>Complex outputs captured and compared</golden_master>
    <approval_testing>Human-reviewable output changes</approval_testing>
    <behavior_documentation>Current behavior documented, not corrected</behavior_documentation>
  </characterization_testing>
  
  <modern_testing_integration>
    <mutation_testing>Validate test effectiveness beyond coverage</mutation_testing>
    <property_based_testing>Mathematical properties and invariants</property_based_testing>
    <fuzzing>Security-focused input fuzzing</fuzzing>
    <performance_characterization>Document and protect performance characteristics</performance_characterization>
  </modern_testing_integration>
  
  <test_infrastructure_commands>
    <test_generation>Automated test creation for legacy components</test_generation>
    <seam_identification>Find dependency injection points</seam_identification>
    <mock_creation>Generate test doubles for external dependencies</mock_creation>
    <validation_automation>Continuous validation of test effectiveness</validation_automation>
  </test_infrastructure_commands>
</testing_infrastructure>

## 🔄 Safe Transformation Patterns

<transformation_patterns>
  <sprout_method>
    <new_features>Add new functionality in new, fully-tested methods</new_features>
    <legacy_integration>Minimal touchpoints with existing legacy code</legacy_integration>
    <full_tdd>New code follows complete TDD cycle</full_tdd>
  </sprout_method>
  
  <sprout_class>
    <isolated_functionality>Major new features in separate classes</isolated_functionality>
    <dependency_injection>Integrate through constructor injection</dependency_injection>
    <comprehensive_testing>100% test coverage for sprouted classes</comprehensive_testing>
  </sprout_class>
  
  <parallel_change>
    <gradual_migration>Old and new implementations coexist</gradual_migration>
    <feature_toggles>Runtime switching between implementations</feature_toggles>
    <validation_comparison>Compare outputs during transition</validation_comparison>
  </parallel_change>
  
  <extract_and_test>
    <method_extraction>Extract methods with immediate test coverage</method_extraction>
    <interface_extraction>Create testable interfaces for dependencies</interface_extraction>
    <class_extraction>Split god objects into focused classes</class_extraction>
  </extract_and_test>
</transformation_patterns>

## 🚨 Emergency Procedures

<emergency_procedures>
  <rollback_triggers>
    <characterization_test_failure>Any existing test starts failing</characterization_test_failure>
    <performance_regression>Significant performance degradation</performance_regression>
    <security_regression>Security baseline violation</security_regression>
    <production_issue>User-reported issues post-deployment</production_issue>
  </rollback_triggers>
  
  <rollback_execution>
    <immediate_revert>Git revert to last known good state</immediate_revert>
    <safety_validation>Run full characterization test suite</safety_validation>
    <root_cause_analysis>Analyze what went wrong and update procedures</root_cause_analysis>
    <learning_integration>Update framework to prevent similar issues</learning_integration>
  </rollback_execution>
</emergency_procedures>

## 🎯 Success Metrics and Validation

<success_metrics>
  <safety_metrics>
    <zero_production_incidents>No issues caused by refactoring</zero_production_incidents>
    <rollback_success_rate>100% successful rollbacks when needed</rollback_success_rate>
    <characterization_effectiveness>Tests catch all behavioral changes</characterization_effectiveness>
  </safety_metrics>
  
  <quality_metrics>
    <coverage_improvement>Measurable increase in test coverage</coverage_improvement>
    <complexity_reduction>Reduced cyclomatic complexity</complexity_reduction>
    <antipattern_elimination>No god objects or code smells</antipattern_elimination>
    <security_hardening>Improved security posture</security_hardening>
  </quality_metrics>
  
  <productivity_metrics>
    <transformation_speed>Faster legacy code improvement</transformation_speed>
    <developer_confidence>Team feels safe making changes</developer_confidence>
    <maintainability_improvement>Easier to understand and modify code</maintainability_improvement>
  </productivity_metrics>
</success_metrics>

## 📚 Command Reference Integration

All slash commands in `.claude/commands/` follow this framework's principles:
- Safety-first approach with mandatory prerequisites
- Comprehensive validation and rollback procedures  
- Integration with coordination system
- Security and quality enforcement
- Clear success criteria and next steps

## 🔍 Continuous Improvement

<continuous_improvement>
  <learning_from_usage>
    <pattern_identification>Identify common transformation patterns</pattern_identification>
    <success_analysis>Analyze what works well and replicate</success_analysis>
    <failure_learning>Learn from mistakes and update procedures</failure_learning>
  </learning_from_usage>
  
  <framework_evolution>
    <research_integration>Incorporate latest TDD and security practices</research_integration>
    <tool_updates>Adapt to new testing and analysis tools</tool_updates>
    <community_feedback>Integrate user feedback and real-world learnings</community_feedback>
  </framework_evolution>
</continuous_improvement>

---

**Remember**: This framework prioritizes safety over speed. Every decision should favor preserving existing functionality while gradually improving code quality, security, and maintainability.