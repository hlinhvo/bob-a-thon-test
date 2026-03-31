# Bob Quick Reference Guide

A quick reference for common Bob operations and best practices.

## 🔧 Core Tools

### File Operations

#### read_file
Read one or more files, optionally with line ranges.

```xml
<read_file>
<args>
<file>
<path>src/app.py</path>
</file>
</args>
</read_file>
```

**Multiple files with line ranges:**
```xml
<read_file>
<args>
<file>
<path>src/app.py</path>
</file>
<file>
<path>src/utils.py</path>
<line_range>1-50</line_range>
<line_range>100-150</line_range>
</file>
</args>
</read_file>
```

**When to use:**
- Understanding code structure
- Before making changes
- Reviewing multiple related files
- Analyzing specific sections

---

#### list_files
List files and directories.

```xml
<list_files>
<path>src/</path>
<recursive>true</recursive>
</list_files>
```

**When to use:**
- Exploring project structure
- Finding files
- Understanding organization

---

#### search_files
Search for patterns using regex.

```xml
<search_files>
<path>src/</path>
<regex>TODO|FIXME</regex>
<file_pattern>*.py</file_pattern>
</search_files>
```

**When to use:**
- Finding specific code patterns
- Locating function calls
- Discovering TODOs
- Finding all usages

---

### Code Editing

#### apply_diff
Make precise changes to files (PREFERRED for edits).

```xml
<apply_diff>
<path>src/utils.py</path>
<diff>
:start_line:10
-------
def old_function():
    return "old"
</diff>
</apply_diff>
```

**When to use:**
- Targeted code changes
- Refactoring
- Bug fixes
- Most editing scenarios

---

#### write_to_file
Write complete file content (overwrites existing).

```xml
<write_to_file>
<path>config.json</path>
<content>
{
  "setting": "value"
}
 line 0 for appending

---

### Code Analysis

#### list_code_definition_names
List classes, functions, and other definitions.

```xml
<list_code_definition_names>
<path>src/</path>
</list_code_definition_names>
```

**When to use:**
- Understanding code structure
- Finding specific functions
- Exploring unfamiliar code

---

### Command Execution

#### execute_command
Run CLI commands.

```xml
<execute_command>
<command>npm test</command>
</execute_command>
```

**When to use:**
- Running tests
- Building projects
- Installing dependencies
- Git operations

---

### Task Management

#### update_todo_list
Track multi-step tasks.

```xml
<update_todo_list>
<todos>
[x] Completed task
[-] In progress task
[ ] Pending task
</todos>
</update_todo_list>
```

**When to use:**
- Complex multi-step tasks
- Tracking progress
- Planning work

---

## 💡 Best Practices

### Prompting Tips

**Be Specific:**
❌ "Fix the bug"
✅ "Fix the null pointer exception in getUserData() on line 45 of src/user.py"

**Provide Context:**
❌ "Add a function"
✅ "Add a validateEmail() function to src/utils.py that checks email format using regex"

**Break Down Complex Tasks:**
❌ "Refactor the entire application"
✅ "Refactor the user authentication module: 1) Extract validation logic, 2) Add error handling, 3) Update tests"

**Use Examples:**
❌ "Make it better"
✅ "Refactor this function to use list comprehension like we do in other utility functions"

---

### Workflow Patterns

#### Pattern 1: Read → Understand → Modify
```
1. Read the file(s)
2. Ask Bob to explain if needed
3. Make targeted changes
4. Verify with tests
```

#### Pattern 2: Search → Read → Update All
```
1. Search for all usages
2. Read affected files
3. Update all occurrences
4. Run tests
```

#### Pattern 3: Plan → Execute → Verify
```
1. Create todo list
2. Execute step by step
3. Test after each step
4. Update todo list
```

---

### Tool Selection Guide

| Task | Recommended Tool | Alternative |
|------|-----------------|-------------|
| View file content | `read_file` | - |
| Find files | `list_files` | `search_files` |
| Search code | `search_files` | `read_file` + manual search |
| Edit existing code | `apply_diff` | `write_to_file` (small files) |
| Create new file | `write_to_file` | - |
| Add new lines | `insert_content` | `apply_diff` |
| Run tests | `execute_command` | - |
| Track progress | `update_todo_list` | Manual notes |

---

## 🎯 Common Scenarios

### Scenario: Rename a Function

```
Step 1: Find all usages
"Search for all files that use the function getUserData"

Step 2: Read affected files
"Read these files: [list from search results]"

Step 3: Update all occurrences
"Rename getUserData to fetchUserProfile in all these files"

Step 4: Verify
"Run the test suite to verify everything works"
```

---

### Scenario: Add a New Feature

```
Step 1: Plan
"Create a todo list for adding email validation to the User model"

Step 2: Understand existing code
"Read src/models/user.py and show me the current validation logic"

Step 3: Implement
"Add email validation following the existing pattern"

Step 4: Test
"Create tests for email validation in tests/test_user.py"

Step 5: Document
"Update the User model docstring to document email validation"
```

---

### Scenario: Debug an Issue

```
Step 1: Reproduce
"Run the failing test: pytest tests/test_checkout.py::test_payment"

Step 2: Analyze
"Read the test file and the checkout module to understand the flow"

Step 3: Locate issue
"Search for error handling in the payment processing code"

Step 4: Fix
"Update the payment timeout handling in src/payment.py"

Step 5: Verify
"Run all payment-related tests to ensure the fix works"
```

---

### Scenario: Refactor Code

```
Step 1: Analyze
"Read src/services/report_generator.py and identify areas for improvement"

Step 2: Plan
"Create a refactoring plan focusing on readability and maintainability"

Step 3: Refactor incrementally
"Extract the data processing logic into separate functions"

Step 4: Test continuously
"Run tests after each refactoring step"

Step 5: Document
"Add docstrings to the new functions"
```

---

## ⚡ Quick Commands

### File Operations
- Read file: "Read src/app.py"
- List files: "List all Python files in src/"
- Search: "Search for TODO comments in the codebase"

### Code Changes
- Simple edit: "Change the timeout value to 30 in config.py"
- Add function: "Add a helper function to format dates in utils.py"
- Refactor: "Refactor the calculate_total function to be more readable"

### Testing
- Run tests: "Run the test suite"
- Run specific test: "Run tests for the user module"
- Check coverage: "Run tests with coverage report"

### Analysis
- Explain code: "Explain how the authentication flow works"
- Find usages: "Find all places where getUserData is called"
- Review: "Review this code for potential issues"

---

## 🚫 Common Mistakes

### Mistake 1: Not Reading Before Editing
❌ "Update the config file"
✅ "Read config.json, then update the timeout value to 30"

### Mistake 2: Vague Requests
❌ "Fix the code"
✅ "Fix the IndexError on line 42 of src/parser.py by adding bounds checking"

### Mistake 3: Too Many Changes at Once
❌ "Refactor everything and add new features"
✅ "First refactor the user module, then we'll add the new features"

### Mistake 4: Not Verifying Changes
❌ Make changes and move on
✅ "Make the changes, then run tests to verify"

### Mistake 5: Insufficient Context
❌ "Add validation"
✅ "Add email validation to the User model following the same pattern as password validation"

---

## 📚 Advanced Tips

### Tip 1: Batch Related Changes
Instead of multiple requests, combine related changes:
```
"In src/user.py:
1. Add email field to User class
2. Add email validation method
3. Update __init__ to accept email
4. Update __str__ to include email"
```

### Tip 2: Use Line Ranges for Large Files
```
"Read src/app.py lines 1-50 for initialization and lines 200-250 for the main logic"
```

### Tip 3: Leverage Bob's Understanding
```
"Review the authentication flow and suggest improvements for security"
```

### Tip 4: Ask for Explanations
```
"Explain why this function might be causing performance issues"
```

### Tip 5: Get Multiple Options
```
"Show me three different ways to implement this feature, with pros and cons"
```

---

## 🎓 Learning Resources

### Practice Exercises
1. Read and understand a new codebase
2. Refactor a complex function
3. Add a new feature with tests
4. Debug a failing test
5. Optimize slow code

### Next Steps
- Try Bob with your own code
- Experiment with different prompting styles
- Share learnings with your team
- Build your own workflow patterns

---

## 📞 Getting Help

### When Stuck
1. Ask Bob to explain the issue
2. Break the problem into smaller steps
3. Search for similar patterns in the codebase
4. Consult the facilitator or support channel

### Resources
- Full documentation: [Link]
- Support channel: [Link]
- Community forum: [Link]
- Video tutorials: [Link]

---

**Remember:** The more context you provide, the better Bob can help you!