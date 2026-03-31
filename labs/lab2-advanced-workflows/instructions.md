# Lab 2: Advanced Bob Workflows for Stream Processing

**Duration:** 30 minutes
**Difficulty:** Intermediate
**Prerequisites:** Completed Lab 1, comfortable with basic Bob operations, Python/Kafka/Spark knowledge

## 🎯 Objectives

By the end of this lab, you will be able to:
- Execute complex, multi-step workflows
- Perform code refactoring across multiple files
- Debug and troubleshoot issues effectively
- Use advanced editing techniques
- Manage complex tasks with todo lists

## 📋 Setup

### ⚠️ Important: Sample Code Project Required

**This lab builds on the sample Python/Kafka project from Lab 1.** You'll need:
- The same sample project with multiple Python files
- Stream processing code with Kafka consumers/producers
- Test files for verification

**If you don't have the sample project:**
1. Complete Lab 1 setup first
2. Ensure you have the sample code repository from your facilitator
3. Have the project open in your IDE

### Prerequisites Checklist

Before starting, ensure you have:
- [ ] **Completed Lab 1**
- [ ] Bob running in your IDE
- [ ] **Sample stream processing project open** (from Lab 1)
- [ ] Understanding of basic Bob tools
- [ ] Kafka and Spark environments accessible

## 🔨 Exercises

### Exercise 1: Multi-File Refactoring (10 minutes)

**Scenario:** You need to rename a Kafka message processing function that's used across multiple stream processors and update all references.

**Tasks:**
1. Find all files that use the function `process_kafka_message`
2. Rename the function to `transform_stream_event` in the main processor
3. Update all import statements and function calls across consumers and producers
4. Verify the changes with pytest

**Bob Tools to Use:**
- `search_files` - Find all usages
- `read_file` - Review multiple files at once
- `apply_diff` - Make precise changes in each file
- `execute_command` - Run tests

**Example Prompt:**
```
I need to refactor the process_kafka_message function to transform_stream_event for better clarity. First, search for all files that use process_kafka_message in the src/streaming directory. Then read those files, update the function definition and all calls to it, and run pytest to verify everything still works.
```

**Expected Outcome:**
- Function renamed in the main stream processor
- All references updated across Kafka consumers and producers
- Tests pass successfully
- No broken imports or calls in the data pipeline

**Key Learning:**
- How to coordinate changes across multiple files
- Importance of searching before modifying
- Verifying changes with tests

---

### Exercise 2: Feature Implementation (10 minutes)

**Scenario:** Add data enrichment to the stream processing pipeline that requires changes to multiple files: schema, processor, and tests.

**Tasks:**
1. Add a new `enriched_metadata` field to the Spark DataFrame schema
2. Update the stream processor to add timestamp and source enrichment
3. Create tests for the enrichment logic
4. Update the pipeline documentation

**Bob Tools to Use:**
- `list_code_definition_names` - Understand existing structure
- `read_file` - Review related files together
- `apply_diff` - Make targeted changes
- `insert_content` - Add new test cases
- `update_todo_list` - Track progress

**Example Prompt:**
```
I need to add data enrichment to our Kafka stream processing pipeline. Please:
1. Update the StreamSchema class in src/schemas/event_schema.py to add enriched_metadata field
2. Modify the StreamProcessor in src/streaming/processor.py to add timestamp and source_system enrichment
3. Add tests for the enrichment logic in tests/test_enrichment.py
4. Update the pipeline documentation in docs/pipeline.md

Create a todo list to track this work.
```

**Expected Outcome:**
- Schema updated with new enrichment field
- Processor adds metadata to streaming events
- Tests cover the enrichment functionality
- Documentation reflects the new enrichment step
- Todo list shows completed steps

**Key Learning:**
- Breaking down complex features into steps
- Using todo lists for task management
- Coordinating related changes
- Importance of tests and documentation

---

### Exercise 3: Debugging and Troubleshooting (5 minutes)

**Scenario:** Kafka consumer tests are failing due to message deserialization issues.

**Tasks:**
1. Run the failing Kafka consumer test suite
2. Analyze the deserialization error messages
3. Locate the problematic JSON parsing code
4. Fix the schema mismatch issue
5. Verify the fix with integration tests

**Bob Tools to Use:**
- `execute_command` - Run tests
- `search_files` - Find related code
- `read_file` - Examine the problematic area
- `apply_diff` - Fix the issue

**Example Prompt:**
```
Run pytest tests/test_kafka_consumer.py and help me debug the deserialization failures. Analyze the error messages, find the problematic JSON parsing code in the consumer, explain what's wrong with the schema, and fix it.
```

**Expected Outcome:**
- Tests run and deserialization failures identified
- Root cause (schema mismatch) understood
- JSON parsing issue fixed correctly
- All Kafka consumer tests passing

**Key Learning:**
- Systematic debugging approach
- Reading and interpreting error messages
- Using Bob to trace issues
- Verifying fixes

---

### Exercise 4: Code Quality Improvement (5 minutes)

**Scenario:** Refactor a Spark aggregation function to improve performance and readability.

**Tasks:**
1. Identify inefficient Spark operations in the aggregation code
2. Refactor to use more efficient Spark transformations
3. Ensure streaming functionality remains the same
4. Add docstrings explaining the windowing logic

**Bob Tools to Use:**
- `read_file` - Analyze current code
- `apply_diff` - Make improvements
- `execute_command` - Run tests to verify

**Example Prompt:**
```
Review the aggregate_stream_metrics function in src/streaming/aggregator.py. Refactor it to use more efficient Spark operations (reduce shuffles, optimize window functions). Add docstrings explaining the windowing logic. Make sure all tests still pass.
```

**Expected Outcome:**
- Code is more readable with clear Spark operations
- Performance improved (fewer shuffles, better partitioning)
- Better documentation of windowing and aggregation logic
- Tests still pass
- Streaming functionality preserved

**Key Learning:**
- Refactoring without breaking functionality
- Balancing readability and performance
- Importance of tests during refactoring
- Adding helpful documentation

---

## 🎓 Advanced Techniques

### 1. Leveraging Bob Modes in Complex Workflows

As tasks get more complex, using the right mode becomes even more important:

**Strategic Mode Switching:**
```
[Ask Mode] - Understand the problem
"Explain the current authentication architecture and identify potential issues"

[Plan Mode] - Break down the solution
"Create a detailed plan to migrate from session-based to JWT authentication"

[Code Mode] - Implement step by step
"Implement step 1: Add JWT library and configuration"
```

**Why This Matters:**
- Ask Mode gives you deep understanding without making changes
- Plan Mode helps you think through complex changes before coding
- Code Mode focuses on implementation with full context

**Pro Tip:** Use Plan mode to create a todo list, then work through it in Code mode.

### 2. Using Bob Findings in Refactoring

Before refactoring, ask Bob to analyze the code:

```
"Analyze this module for security issues, code quality problems, and refactoring opportunities. Prioritize by severity."
```

**Bob Findings Will Identify:**
- Security vulnerabilities to fix first
- Code smells to address
- Performance bottlenecks
- Maintainability issues

**Then refactor with confidence:**
```
"Refactor this module addressing the high-priority findings you identified, starting with security issues."
```

### 3. Reading Multiple Files Efficiently

When working with related files, read them together:

```
Read these files together:
- src/streaming/kafka_consumer.py
- src/streaming/spark_processor.py
- src/schemas/event_schema.py
- tests/test_stream_pipeline.py

I need to understand how our Kafka-to-Spark streaming pipeline works.
```

**Benefits:**
- Bob gets full context
- Better understanding of relationships
- More accurate suggestions

### 2. Using Line Ranges for Large Files

For large files, read specific sections:

```
Read src/streaming/processor.py lines 1-50 and 200-250 to see the Spark session initialization and main processing function.
```

**Benefits:**
- Faster reading
- Focus on relevant code
- Reduced token usage

### 3. Complex apply_diff Operations

Make multiple changes in one request:

```
In src/streaming/processor.py, make these changes:
1. Update the process_batch function to add data validation
2. Add a new handle_late_data helper function for watermarking
3. Fix the typo in the comment on line 45 about window duration
```

**Benefits:**
- Atomic changes
- Fewer round trips
- Better context preservation

### 4. Using Todo Lists for Complex Tasks

Break down large tasks:

```
Create a todo list for implementing real-time anomaly detection:
- [ ] Add anomaly detection model to Spark processor
- [ ] Create Kafka topic for anomaly alerts
- [ ] Add windowed aggregation for baseline calculation
- [ ] Implement alerting logic for threshold violations
- [ ] Add tests for anomaly detection flow
```

**Benefits:**
- Clear progress tracking
- Organized approach
- Easy to resume if interrupted

---

## 💡 Best Practices

### 1. Plan Before Executing
- Search and read before modifying
- Understand the full scope
- Identify all affected files

### 2. Make Atomic Changes
- Group related changes together
- Keep changes focused
- Verify after each major change

### 3. Test Continuously
- Run tests after changes
- Fix issues immediately
- Don't accumulate technical debt

### 4. Provide Context
- Explain what you're trying to achieve
- Mention constraints or requirements
- Share relevant background information

### 5. Use Version Control
- Commit working changes
- Create branches for experiments
- Easy rollback if needed

---

## 🐛 Common Challenges

### Challenge: Changes conflict with each other
**Solution:** Make changes in logical order, test incrementally

### Challenge: Lost track of what needs to be done
**Solution:** Use `update_todo_list` to track progress

### Challenge: Tests failing after refactoring
**Solution:** Make smaller changes, test more frequently

### Challenge: Unsure about the impact of changes
**Solution:** Search for all usages first, read related code

### Challenge: Complex changes feel overwhelming
**Solution:** Break into smaller steps, tackle one at a time

---

## 📝 Discussion Questions

1. How do you decide when to make changes in one request vs. multiple requests?
2. What's your strategy for refactoring code without breaking functionality?
3. How can todo lists help manage complex workflows?
4. What's the best way to verify that multi-file changes work correctly?
5. How do you balance speed with thoroughness when making changes?

---

## ✅ Completion Checklist

- [ ] Completed Exercise 1: Multi-File Refactoring
- [ ] Completed Exercise 2: Feature Implementation
- [ ] Completed Exercise 3: Debugging and Troubleshooting
- [ ] Completed Exercise 4: Code Quality Improvement
- [ ] Understand how to coordinate multi-file changes
- [ ] Can use todo lists for complex tasks
- [ ] Comfortable with advanced editing techniques
- [ ] Know how to debug effectively with Bob

---

## 🚀 Next Steps

Once you've completed this lab:
1. Review the solutions in the `solution/` directory
2. Try applying these techniques to your own code
3. Move on to Lab 3: Client-Specific Implementation
4. Experiment with more complex scenarios

---

## 📚 Additional Resources

- **Bob Differentiators**: See `resources/bob-differentiators.md` - Learn what makes Bob unique
- **Advanced Bob Patterns**: [Link to docs]
- **Refactoring Guide**: See `resources/cheat-sheet.md`
- **Debugging Tips**: See `resources/troubleshooting.md`

### 🌟 Leverage Bob's Advanced Capabilities

As you work through advanced workflows, remember Bob's differentiators:
- **Automatic Model Selection** - Bob uses the right model for each task (you'll notice faster responses for simple tasks, deeper analysis for complex ones)
- **Bob Findings** - Ask Bob to analyze code for security and quality issues proactively
- **MCP Integrations** - Connect to your internal tools and documentation
- **Context Optimization** - Bob efficiently manages large codebases

Learn more in `resources/bob-differentiators.md`

---

**Need Help?** Ask your facilitator or use the dedicated support channel!

**Pro Tip:** The best way to learn advanced workflows is to practice with real code. Don't be afraid to experiment!
## 💰 Business Impact

This lab demonstrates Bob's advanced capabilities for complex development tasks:

### ⏱️ Productivity Gains
- **Multi-File Refactoring**: 80% faster than manual find-and-replace across files
- **Complex Debugging**: Reduces debugging time by 60% with intelligent analysis
- **Code Generation**: 70% faster than writing boilerplate code manually
- **Workflow Automation**: Eliminates 3-4 hours of repetitive tasks per week

### 🐛 Quality Improvements
- **Refactoring Safety**: 95% reduction in errors from large-scale code changes
- **Test Coverage**: Automated test generation increases coverage by 40%
- **Code Consistency**: Ensures uniform patterns across entire codebase
- **Documentation**: Auto-generated docs are 90% complete and accurate

### 🔒 Security Enhancements
- **Dependency Updates**: Safely updates vulnerable packages with compatibility checks
- **Security Pattern Implementation**: Applies security best practices consistently
- **Code Review Automation**: Catches 80% of security issues before human review

### 💼 Efficiency Impact
- **Reduced Refactoring Time**: Saves 6-8 hours per major refactoring project
- **Faster Feature Development**: 50% reduction in time for complex features
- **Lower Technical Debt**: Prevents accumulation of code quality issues

**Estimated Weekly Value per Developer**: 6-8 hours saved in productivity gains

---

## 🌟 Bob Differentiators in Advanced Workflows

This lab showcased Bob's enterprise-grade capabilities:

### 1. **Intelligent Model Selection**
Bob automatically chose the right AI model for each task—faster models for simple edits, more powerful models for complex refactoring. You didn't need to configure this; Bob optimized behind the scenes.

### 2. **Context Optimization**
When reading multiple files, Bob efficiently managed context to understand relationships without hitting token limits. This enables working with large codebases that would overwhelm other AI tools.

### 3. **Atomic Multi-File Operations**
Bob coordinated changes across multiple files in a single operation, ensuring consistency. Other tools require manual coordination or risk inconsistent states.

### 4. **Extensible Architecture (MCP)**
While not used in this lab, Bob's Model Context Protocol (MCP) integration allows connection to internal tools, databases, and documentation—making Bob aware of your entire development ecosystem.

### 5. **Enterprise Modernization Focus**
Bob excels at Java and legacy code transformation, with specialized capabilities for modernizing enterprise applications. This differentiates Bob for organizations with large existing codebases.

### 6. **Proactive Quality Analysis**
Bob Findings runs continuously, identifying issues before you ask. This proactive approach catches problems early, reducing technical debt and security vulnerabilities.

---
