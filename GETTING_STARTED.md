# 🚀 Getting Started - Legacy Code TDD Framework

*Transform your legacy codebase safely in 15 minutes*

**Goal:** Complete setup, run first assessment, and successfully transform a piece of legacy code using the safety-first approach.

---

## ⚡ Quick Start (5 Minutes)

### Prerequisites
- Legacy codebase in a Git repository
- Basic command line access
- Claude Code available for execution

### Instant Setup
```bash
# 1. Navigate to your legacy codebase
cd /path/to/your/legacy/project

# 2. Verify you're in the right place
ls -la
# You should see your source code files

# 3. Verify Git repository
git status
# Should show current branch and status

# 4. Start with framework overview
/legacy-assess-risk --dry-run
# This gives you a preview without making changes
```

**✅ Success Indicator:** You see an analysis of your codebase risks and complexity hotspots.

---

## 🎯 First Successful Transformation (10 Minutes)

### Step 1: Understand Your Codebase (3 minutes)

Run the assessment phase to understand what you're working with:

```bash
# Get overall risk assessment
/legacy-assess-risk

# Check current test coverage
/legacy-coverage-report

# Understand dependencies
/legacy-dependency-analysis
```

**What You'll See:**
- Complexity hotspots and risky areas
- Current test coverage levels
- Dependency coupling analysis
- Recommendations for improvement

### Step 2: Build Safety Infrastructure (4 minutes)

Before changing ANY code, establish comprehensive safety measures:

```bash
# Create characterization tests for existing behavior
/legacy-safety-net-create

# Identify where dependencies can be injected
/legacy-seam-identify

# Generate test doubles for external dependencies
/legacy-mock-generator

# Ensure rollback capability for all changes
/legacy-rollback-prepare
```

**Safety Checkpoint:** You now have:
- ✅ Tests that capture current behavior (including bugs)
- ✅ Test doubles for external dependencies  
- ✅ Rollback procedures ready
- ✅ Seams identified for safe modification

### Step 3: Make Your First Safe Change (3 minutes)

Choose the safest transformation technique - adding new functionality:

```bash
# Add new functionality without touching existing code
/legacy-sprout-method --target="ClassName.methodName" --feature="logging"

# OR create a new class for substantial functionality
/legacy-sprout-class --feature="analytics" --integration-point="PaymentProcessor"
```

**What Happens:**
- New functionality is added in isolated, fully-tested code
- Existing legacy code remains completely unchanged
- Integration is minimal and reversible
- All changes are protected by characterization tests

**✅ Success Indicator:** You've safely added new functionality without breaking existing behavior.

---

## 🛡️ Safety Verification

### Verify Nothing Broke
```bash
# Run your existing test suite
npm test  # or whatever your test command is

# Check that characterization tests pass
/legacy-safety-net-validate

# Verify no performance regression
/legacy-performance-baseline --compare
```

### Quick Rollback Test
```bash
# Test rollback capability (don't worry, this is safe)
/legacy-rollback-test --dry-run

# If needed, actually rollback
/legacy-rollback --to-baseline
```

---

## 📚 What You've Accomplished

In 15 minutes, you've:

1. **✅ Assessed** your legacy codebase comprehensively
2. **✅ Built** a safety net with characterization tests
3. **✅ Made** your first safe transformation
4. **✅ Verified** nothing broke in the process
5. **✅ Confirmed** rollback capability works

### Framework Benefits Demonstrated

- **No Production Risk**: Every change was protected by tests
- **Confidence Building**: You can see exactly what changed
- **Incremental Progress**: Small, safe steps forward
- **Team Safety**: Others can follow the same approach

---

## 🎯 Next Steps

### For Immediate Value
Continue with more transformations:

```bash
# Extract complex methods into testable units
/legacy-extract-method --target="LargeClass.complexMethod"

# Wrap existing methods with new capabilities
/legacy-wrap-method --target="PaymentProcessor.process" --enhancement="monitoring"
```

### For Systematic Improvement
Follow the complete workflow:

1. **[Command Reference](COMMAND_REFERENCE.md)** - See all available commands
2. **[User Guide](USER_GUIDE.md)** - Learn the complete system
3. **[Examples](EXAMPLES.md)** - See real transformation examples

### For Team Adoption
Share your success:

1. Show teammates the before/after comparison
2. Demonstrate the safety measures in action
3. Use the framework for larger transformations
4. Build team confidence with systematic approach

---

## 🆘 Troubleshooting

### Common Issues

**❌ "Command not recognized"**
- **Solution**: Ensure you're in a directory with `.claude/commands/` folder
- **Check**: Run `ls .claude/commands/` to verify commands exist

**❌ "No test framework detected"**
- **Solution**: The framework needs a basic test infrastructure
- **Check**: Verify you have `package.json`, `Cargo.toml`, or similar

**❌ "Insufficient coverage for safety"**
- **Solution**: Start with `/legacy-safety-net-create` to build coverage
- **Note**: This is a feature, not a bug - we prioritize safety

**❌ "Git repository required"**
- **Solution**: Initialize Git with `git init && git add . && git commit -m "Initial commit"`
- **Why**: Rollback requires version control

### Getting Help

**For Setup Issues:**
- Check your current directory: `pwd`
- Verify Git status: `git status`
- List available commands: `ls .claude/commands/`

**For Framework Questions:**
- **[Troubleshooting Guide](TROUBLESHOOTING.md)** - Comprehensive problem solving
- **[User Guide](USER_GUIDE.md)** - Deep framework understanding
- **[Command Reference](COMMAND_REFERENCE.md)** - Complete command documentation

**For Specific Transformations:**
- **[Examples](EXAMPLES.md)** - Real-world transformation examples
- **[CLAUDE.md](CLAUDE.md)** - Technical framework details

---

## 🌟 Success Stories

### 5-Minute Wins
> *"Ran assessment and immediately found 3 critical risks we didn't know existed"*

> *"Used sprout method to add monitoring without touching fragile payment code"*

### 15-Minute Transformations
> *"Created comprehensive safety net for our most complex class"*

> *"Extracted 200-line method into 5 focused, testable methods"*

### Team Adoption Success
> *"Entire team now uses framework - zero production incidents from refactoring"*

> *"Transformed 50,000 lines of legacy code systematically over 3 months"*

---

## 🎯 Ready for More?

### Continue Learning
**[User Guide →](USER_GUIDE.md)**
*Progressive learning from beginner to expert*

### See All Commands
**[Command Reference →](COMMAND_REFERENCE.md)**
*Complete documentation of all 24 commands*

### Get Inspired
**[Real Examples →](EXAMPLES.md)**
*Before/after transformations and success stories*

---

**Remember**: The framework prioritizes safety over speed. Every small, safe step builds confidence and maintains system stability while gradually improving your legacy codebase.