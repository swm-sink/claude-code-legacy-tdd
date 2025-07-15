# Legacy Property Testing - Mathematical Properties and Invariant Validation

**Command**: `/legacy-property-test`  
**Phase**: Quality Assurance  
**Coverage Requirement**: 90%+ coverage + complex algorithms identified (blocks without this)  
**Risk Level**: Low (test enhancement only, no production code changes)

## Objective

Implement property-based testing for complex algorithms and business logic in legacy code to validate mathematical properties, invariants, and behavioral contracts that are difficult to test with traditional example-based tests.

## Context

Property-based testing complements characterization tests by validating that algorithms maintain mathematical properties and business invariants across wide ranges of inputs. This is crucial for legacy systems with complex calculations, data transformations, and business rules.

## Property Testing Strategy Tasks

1. **Prerequisite Validation**:
   - Verify that 90%+ test coverage requirement has been met and characterization tests are complete
   - Confirm that complex algorithms and business logic components have been identified
   - Validate that existing test infrastructure can accommodate property-based testing frameworks
   - Check that algorithm behavior is well-understood through characterization testing

2. **Property Identification and Analysis**:
   - **Mathematical Properties**: Identify algebraic properties (commutativity, associativity, distributivity) in calculations
   - **Business Invariants**: Find business rules that must hold regardless of input (balance preservation, data consistency)
   - **Transformation Properties**: Validate that data transformations preserve essential characteristics
   - **Boundary Conditions**: Test that algorithms handle edge cases and boundary conditions correctly

3. **Algorithm Complexity Assessment**:
   - **Calculation Engines**: Focus on financial calculations, mathematical computations, statistical analysis
   - **Data Processing Pipelines**: Test data transformation, validation, and aggregation algorithms
   - **Business Rule Engines**: Validate complex conditional logic and decision-making algorithms
   - **State Machines**: Test state transition properties and invariants in workflow systems

4. **Property Test Design Strategy**:
   - **Generator Design**: Plan appropriate input generators for realistic and edge-case testing
   - **Property Specification**: Define clear, testable properties that capture algorithm essence
   - **Shrinking Strategy**: Design input reduction strategies for effective counterexample identification
   - **Oracle Functions**: Create reference implementations or mathematical proofs for property validation

## Property Testing Implementation Tasks

### Mathematical Property Testing

1. **Algebraic Property Validation**:
   - **Commutativity**: Test that `f(a, b) = f(b, a)` for symmetric operations
   - **Associativity**: Validate that `f(f(a, b), c) = f(a, f(b, c))` for grouping operations
   - **Distributivity**: Test that `f(a, g(b, c)) = g(f(a, b), f(a, c))` for distributed operations
   - **Identity Elements**: Verify that operations have proper identity elements (zero, one, empty set)

2. **Inverse and Reversibility Properties**:
   - **Roundtrip Properties**: Test that `decode(encode(x)) = x` for serialization/parsing operations
   - **Inverse Operations**: Validate that operations and their inverses cancel each other out
   - **Data Preservation**: Ensure that transformations preserve essential data characteristics
   - **Lossless Conversions**: Test that data conversions don't lose information

3. **Monotonicity and Ordering Properties**:
   - **Monotonic Functions**: Test that `f(a) ≤ f(b)` when `a ≤ b` for ordering-preserving functions
   - **Sorting Properties**: Validate that sorting algorithms produce correctly ordered results
   - **Comparison Consistency**: Test that comparison operations are transitive and consistent
   - **Range Preservation**: Ensure that functions map valid inputs to valid outputs

### Business Logic Property Testing

1. **Financial and Calculation Properties**:
   - **Balance Preservation**: Test that financial transactions preserve total balance across accounts
   - **Currency Conversion Consistency**: Validate that currency conversions round-trip correctly
   - **Interest Calculation Properties**: Test compound interest and amortization calculations
   - **Tax and Fee Calculation Invariants**: Validate that calculations follow business rules consistently

2. **Data Validation and Integrity Properties**:
   - **Data Format Preservation**: Test that data validation accepts valid inputs and rejects invalid ones
   - **Range and Boundary Validation**: Ensure that inputs are properly validated against business constraints
   - **Referential Integrity**: Test that relationships between data entities are maintained
   - **Audit Trail Properties**: Validate that changes preserve audit trail consistency

3. **Workflow and State Machine Properties**:
   - **State Transition Validity**: Test that all state transitions follow defined business rules
   - **Workflow Invariants**: Validate that workflow states maintain required business properties
   - **Permission and Authorization Properties**: Test that access control maintains security invariants
   - **Process Completion Properties**: Ensure that workflows reach completion states correctly

### Framework-Specific Property Testing

#### iOS/Swift Property Testing
- Use Swift property testing frameworks (SwiftCheck, SwiftPropTest) for iOS-specific algorithm validation
- Test Core Data model properties and persistence invariants
- Validate UI state consistency and view controller lifecycle properties
- Test iOS-specific algorithms (image processing, location services, device orientation)

#### JavaScript/Node.js Property Testing
- Use JavaScript property testing libraries (JSVerify, fast-check) for algorithm validation
- Test asynchronous operation properties and Promise chain invariants
- Validate JSON serialization/deserialization roundtrip properties
- Test Node.js stream processing and event handling properties

#### Python Property Testing
- Use Python property testing frameworks (Hypothesis, property-based-testing) for comprehensive validation
- Test NumPy and data science algorithm properties
- Validate Python-specific features (generator functions, decorator behavior)
- Test web framework request/response processing properties

#### Java Property Testing
- Use Java property testing libraries (jqwik, QuickTheories, junit-quickcheck) for enterprise validation
- Test Spring framework bean lifecycle and dependency injection properties
- Validate Java collection and stream processing properties
- Test enterprise integration pattern properties

## Property Test Implementation Strategy

### Input Generation and Test Case Design

1. **Smart Input Generation**:
   - Design generators that produce realistic business data within valid ranges
   - Create generators for edge cases, boundary conditions, and error scenarios
   - Implement composite generators for complex data structures and business objects
   - Use domain-specific generators that understand business constraints and relationships

2. **Property Specification Best Practices**:
   - Write properties that are simple, clear, and directly testable
   - Focus on essential algorithm characteristics rather than implementation details
   - Create properties that are resilient to minor implementation changes
   - Design properties that complement rather than duplicate existing characterization tests

3. **Shrinking and Counterexample Analysis**:
   - Implement effective shrinking strategies to find minimal counterexamples
   - Design shrinking that preserves relevant characteristics of failing inputs
   - Create analysis tools to understand why properties fail and how to fix them
   - Integrate shrinking results with debugging and development workflows

### Property Testing Quality Assurance

1. **Property Coverage and Completeness**:
   - Ensure property tests cover all critical algorithm paths and business scenarios
   - Validate that properties test both normal operation and edge cases
   - Create properties for error handling and exception scenarios
   - Test that properties themselves are correct and meaningful

2. **Performance and Scalability**:
   - Optimize property test execution time for practical continuous integration use
   - Balance thorough testing with reasonable execution times
   - Use statistical sampling and intelligent test case selection
   - Implement parallel execution for independent property validation

## Legacy Code Property Testing Challenges

### Legacy Algorithm Analysis

1. **Reverse Engineering Properties**:
   - Analyze legacy algorithms to understand their intended mathematical properties
   - Use characterization testing results to infer algorithm invariants
   - Study business documentation to understand intended behavior properties
   - Interview domain experts to understand business rule properties

2. **Dealing with Legacy Quirks**:
   - Handle legacy algorithms that don't follow strict mathematical properties
   - Test intended behavior while documenting known quirks and exceptions
   - Create properties that validate "correct" behavior while allowing for legacy oddities
   - Plan property evolution as legacy code is gradually improved

### Integration with Characterization Testing

1. **Complementary Testing Strategy**:
   - Use characterization tests to document specific behavior examples
   - Use property tests to validate general behavior patterns and invariants
   - Combine both approaches for comprehensive behavior validation
   - Ensure property tests don't conflict with documented legacy behavior quirks

2. **Migration and Evolution Support**:
   - Use property tests to validate that transformations preserve essential algorithm properties
   - Create properties that can guide refactoring by specifying required behavior
   - Use property testing to validate that improvements don't break essential characteristics
   - Support gradual migration by testing both legacy and new implementations against same properties

## Property Testing Automation and Integration

### Continuous Property Validation

1. **CI/CD Integration**:
   - Integrate property testing into continuous integration for ongoing validation
   - Set up property test execution as part of transformation validation process
   - Create reporting and analysis tools for property test results
   - Automate property test execution for code changes affecting algorithms

2. **Property Test Maintenance**:
   - Update property tests as algorithms evolve and business rules change
   - Version property specifications along with code changes
   - Create property test review processes for business rule validation
   - Document property rationale and business justification

## Success Criteria

- Comprehensive property tests implemented for all complex algorithms and business logic
- Mathematical properties and business invariants validated through automated testing
- Property testing integrated with existing characterization testing for comprehensive coverage
- Algorithm transformation safety enhanced through property preservation validation
- Continuous property testing established for ongoing algorithm quality assurance
- Business rule compliance validated through property-based testing automation

## Integration

- Documents property testing completion status and algorithm validation results
- Provides mathematical validation that complements characterization testing
- Enables confident algorithm transformation through property preservation validation
- Establishes ongoing property testing for continuous algorithm quality assurance

## Rollback

Property testing is enhancement and validation only and requires no rollback procedures:
1. **Property Refinement**: Adjust property specifications based on validation results
2. **Generator Improvement**: Enhance input generators based on test effectiveness analysis
3. **Algorithm Understanding**: Use property testing results to better understand legacy behavior
4. **Continuous Improvement**: Integrate property testing learnings into transformation strategy