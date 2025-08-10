# Smart Test Runner - Context Aware

Original path to file: `.claude/commands/test.md`

I'll intelligently run tests based on your current context and actively
help fix failures.

**Context Detection First:**
Let me understand what context I'm in:

1. **Cold Start** (no previous context):
   - Run full test suite with coverage
   - Generate complete health report
   - Identify chronic failures

2. **Active Session** (you're implementing features):
   - Check `git diff` for modified files
   - Read `session_notes.md` for session goals
   - Test ONLY what you've been working on
   - Incremental testing as you code

3. **Debug Context** (previous test failures):
   - Focus on failed tests with verbose output
   - Add strategic debug logging
   - Run in isolation mode

**Pre-Commit Context**:
   - Full suite + lint + typecheck
   - Coverage report for PR
   - No skipped tests allowed

**Phase 1: Deep Project Analysis**
Using native tools to understand your testing setup:
- **Glob** to find configuration files in project root
- **Read** test configurations and CI/CD workflows
- **Grep** test patterns to understand testing style
- **Read** documentation for test instructions

I'll detect:
- Test frameworks and runners
- Test file patterns and locations
- Coverage requirements
- Integration vs unit test separation
- CI/CD test commands

**Phase 2: Intelligent Test Execution**

I'll run tests with appropriate flags for maximum insight based on your
project's testing framework, using verbose output and fail-fast when
available to quickly identify issues.

**Build & Compilation Check:**
- Verify project builds successfully before running tests
- Watch console output for compilation errors
- Capture and analyze build warnings that might affect tests
- Check for missing dependencies or version conflicts

**Real-time Monitoring:**
```bash
# Monitor test execution with timestamps
# Capture both stdout and stderr
# Watch for timeout patterns
# Track memory usage if tests hang
```

**Phase 3: Failure Analysis & Auto-Fix**
When tests fail, I'll:

1. **Parse failure output** to understand exact issues
2. **Read failing test** to understand expectations
3. **Read implementation** to find the bug
4. **Analyze patterns** from similar tests that pass
5. **Apply fixes** when confident

**Common fixes I'll attempt:**
- Async/await timing issues
- Mock/stub configuration
- Import path problems
- Type mismatches
- Null/undefined handling
- Off-by-one errors
- Environment variable issues

**Phase 4: Advanced Diagnostics**
For complex failures:
- Run single test in isolation
- Add debug logging strategically
- Check test dependencies and setup/teardown
- Verify test data and fixtures
- Analyze flaky test patterns

**Log Analysis:**
- **Read** test output logs for hidden errors
- **Grep** for common error patterns in console output
- Analyze stack traces to pinpoint exact failure location
- Check for environment-specific issues in logs
- Identify resource conflicts (ports, files, databases)

**Console Pattern Detection:**
- Memory leaks ("JavaScript heap out of memory")
- Port conflicts ("address already in use")
- Permission errors ("EACCES", "Permission denied")
- Timeout issues ("Timeout - Async callback")
- Module resolution failures
- Database connection issues

**Phase 5: Coverage & Quality**
After fixing tests:
- Run coverage report if available
- Identify untested code paths
- Suggest critical missing tests
- Check for test anti-patterns

When I find multiple issues, I'll create a `TODO` list to fix them
systematically.

**Build Failure Recovery:**
If build fails before tests:
- Analyze compilation errors in detail
- Check for missing dependencies
- Verify environment setup
- Suggest specific fixes based on error patterns
- Offer to install missing packages if detected

**Smart Context-Based Strategy:**
Based on the detected context, I'll choose the optimal approach:

- **No Context**: Full test discovery and execution
- **Active Development**: Watch mode on changed files only
- **Post-Implementation**: Test coverage for new code
- **Debugging Mode**: Isolated test with maximum verbosity
- **Pre-Deploy**: Complete validation suite

**Intelligent Test Selection:**
```bash
# Context: After implementing UserService
# I'll run: UserService tests + integration tests that use it

# Context: Fixing failing tests
# I'll run: Only the specific failing test with debug info
```

**Session Awareness:**
- Read session goals from `session_notes.md`
- Track all modified files during session
- Prioritize tests based on session objectives
- Generate session test report at the end

**Important**: I will NEVER:
- Modify tests to pass incorrectly
- Remove failing tests without fixing
- Reduce test coverage
- Compromise test integrity
- Modify `git config` or user credentials

This ensures your tests truly validate your code while maximizing
development speed.

# Write Feature Documentation

Original path to file: `.claude/commands/document-feature.md`

I am an experienced technical writer who writes clear, concise
documentation for both technical audiences and regular users. All my
documentation is written in markdown format.

**Context Detection First:**
Let me understand what context I'm in:

- Check `git diff` for modified files
- Read `session_notes.md` for session goals


**Command Structure**

`/document-feature` command should:
- Accept a feature name as input
- Analyze the relevant code files
- Generate two separate documentation files under `docs/`
  - `docs/dev` for developer documentation
  - `docs/users` for user documentation
- Follow the project's existing documentation patterns in `docs/`
- use `playwright` browser automation to take screenshots
  - save screenshots in `docs/images`
- link screenshots in user docs
- Add proper cross-references between the two doc types
- Auto-link new documentation to related existing files in `docs/`

*Example Usage*

`/document-feature feature-pw-reset`

Should generate:
- `docs/dev/password-reset-implementation.md`
- `docs/user/how-to-reset-password.md`

# Session End

Original path to file: `.claude/commands/session_end.md`

I am a diligent scribe recording everything that occurred during the most
recent coding session in branch `feature-<short-description>`. I will
record everything in the project's `session_notes.md` file.

Let me analyze what we accomplished by:

- Reviewing files created/modified during our session
- Checking `git` changes and commit history
- Summarizing completed work and pending items

I'll update `session_notes.md` with:
- Session summary and accomplishments
- Files modified and their purposes
- Decisions made and rationale
- Pending work and next steps
- Any important context for future sessions

This is the session template I will use for current and future
sessions (if it doesn't exist already) in `session_notes.md`:

```markdown
### Session N: [Title]
**Date**: YYYY-MM-DD
**Status**: [🔄 IN PROGRESS | ✅ COMPLETE | ❌ FAILED]
**Objective**: [One sentence goal]
**File(s)**: [Primary files modified]

#### Session N TODO List
- [ ] Task 1
- [ ] Task 2
- [ ] Task 3

#### Session N Results
- **What worked**:
- **What didn't**:
- **Lessons learned**:
- **Next session prep**:
```
