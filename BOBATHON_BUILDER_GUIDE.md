# Bobathon Builder Mode - Installation and Usage Guide

## 🎯 Overview

The **Bobathon Builder** mode is a custom Bob mode that guides you through creating customized bobathons for clients. It provides:

- **Interactive Q&A** to gather client information
- **Automatic validation** to ensure completeness
- **Smart customization** of labs and materials
- **Quality assurance** checks before delivery

## 📦 Installation

The Bobathon Builder mode is already included in this template! The mode configuration is in the `.bobmodes` file at the root of this project.

### Verify Installation

1. Open this project in VS Code with Bob installed
2. Look for the mode selector in Bob's interface
3. You should see "🎓 Bobathon Builder" in the list of available modes

### If the Mode Doesn't Appear

If you don't see the Bobathon Builder mode:

1. **Reload VS Code Window:**
   - Press `Ctrl+Shift+P` (Windows/Linux) or `Cmd+Shift+P` (Mac)
   - Type "Reload Window" and press Enter
   - Bob will reload and detect the `.bobmodes` file

2. **Check the .bobmodes file:**
   - Ensure `.bobmodes` exists in the workspace root
   - Verify it contains the `bobathon-builder` mode configuration

3. **Restart Bob:**
   - Close and reopen VS Code
   - Bob should detect the custom mode on startup

## 🚀 Quick Start

### Step 1: Switch to Bobathon Builder Mode

1. Open Bob in VS Code
2. Click the mode selector (shows current mode like "💻 Code" or "❓ Ask")
3. Select "🎓 Bobathon Builder" from the list

### Step 2: Start Creating a Bobathon

Once in Bobathon Builder mode, you can:

**Option A: Create from Scratch**
```
Help me create a new bobathon for [Client Name]
```

**Option B: Start from an Example**
```
I want to create a bobathon based on the Financial Services example
```

**Option C: Customize Existing Config**
```
Customize the labs for the client in bobathon-config.yaml
```

### Step 3: Answer the Questions

Bob will guide you through a series of questions:

1. **Client Information**
   - Company name and industry
   - Primary contact details

2. **Technology Stack**
   - Programming language
   - Frameworks and tools
   - Infrastructure (AWS, Azure, etc.)

3. **Lab Technology Preference**
   - Should Labs 1 & 2 (basic Bob features) use the same technology as the client?
   - Or use generic examples that work across languages?
   - This helps ensure labs are relevant to the client's daily work

4. **Use Cases**
   - What problems to solve
   - Priority levels
   - Time estimates

5. **Schedule**
   - Total duration (3, 6, or 12 hours)
   - Date and timezone
   - Timing preferences

6. **Participants**
   - Team size
   - Roles and skill levels
   - Prerequisites

### Step 4: Review and Validate

After gathering information, Bob will:
- Generate `bobathon-config.yaml`
- Validate completeness
- Check for consistency
- Offer to customize labs

### Step 5: Customize Materials

Choose what to customize:
- **Lab 1:** Basic operations for their tech stack
- **Lab 2:** Advanced workflows for their tech stack
- **Lab 3:** Client-specific scenarios based on use cases
- **Schedule:** Detailed agenda with timing

### Step 6: Save Your Bobathon

Once everything is complete and validated, Bob will ask how you want to save the bobathon:

**Option 1: Export to New Directory (Recommended)**
- Creates a clean, standalone bobathon in `../{client-name}-bobathon/`
- Optionally removes template files (.bob/, .bobmodes, examples/)
- Ready to initialize as a new git repository
- Perfect for client delivery

**Option 2: Prepare for New Repository**
- Creates a branch with your changes
- Asks for target repository URL
- Provides exact git commands to push
- Optionally cleans up template files

**Option 3: Create Branch in This Repo**
- Keeps bobathon with template for easy updates
- Creates branch like `bobathon-acme-corp`
- All bobathons in one repository
- Easy to switch between clients

**Option 4: Commit to Current Branch**
- Simple commit to current branch
- You handle git workflow manually
- Good for quick iterations

## 📋 Common Workflows

### Workflow 1: Complete New Bobathon Setup

```
User: "Create a new bobathon for Acme Financial Services"

Bob will ask about:
1. Industry and contact info
2. Tech stack (Java, Spring Boot, etc.)
3. Lab technology preference:
   "Should Labs 1 & 2 use Java/Spring Boot like your client work,
    or generic examples? Using client tech makes labs more relevant
    but takes more customization time."
4. Key use cases (API development, security, etc.)
5. Duration and schedule
6. Team composition
7. Business value tracking preferences
8. **Code generation strategy (MANDATORY)**

Then Bob will:
- Generate bobathon-config.yaml
- Customize labs based on technology preference
- Add Business Impact sections to each lab
- Embed real-time value indicators in exercises
- **Ask about code generation strategy (REQUIRED - you must choose):**
  * Generate both starter code and solutions (recommended - complete package)
  * Generate starter code only (participants build solutions)
  * Generate solutions only (you provide starter code)
  * Have Bob generate code live during labs (demonstrates Bob's capabilities)
  * No code generation (manual creation or use existing code)
- Create Lab 3 scenarios with business value metrics
- Set up business value tracking (surveys, metrics)
- Validate everything
```

### Workflow 2: Customize Labs Only

```
User: "Customize all labs for the client in bobathon-config.yaml"

Bob will:
1. Read the existing config
2. Update Lab 1 with client's tech stack
3. Update Lab 2 with client's tech stack
4. **Ask about code generation strategy (MANDATORY)**
5. Generate code based on selected strategy
6. Create Lab 3 scenarios from use cases
7. Validate consistency
```

### Workflow 3: Setup Business Value Tracking

```
User: "Set up business value tracking for this bobathon"

Bob will:
1. Explain business value tracking benefits
2. Ask about collection strategy:
   - After each lab + end of bobathon + follow-up (recommended)
   - After each lab + end of bobathon
   - End of bobathon only
3. Ask about survey tool (Google Forms, Slido, etc.)
4. Generate survey questions for each collection point
5. Add tracking configuration to bobathon-config.yaml
6. Provide survey creation guidance
```

### Workflow 4: Validate Existing Bobathon

```
User: "Validate the bobathon materials"

Bob will:
1. Read all bobathon files
2. Check required fields
3. Verify timing calculations
4. Ensure tech stack consistency
5. Check Business Impact sections exist
6. Verify business value tracking configured
7. Detect placeholders
8. Report findings
9. Offer to fix issues
```

### Workflow 5: Adjust Schedule

```
User: "We only have 4 hours instead of 6, adjust the schedule"

Bob will:
1. Read current config
2. Recalculate timing
3. Prioritize high-value use cases
4. Suggest what to skip
5. Update schedule
6. Validate new timing

### Workflow 6: Save Completed Bobathon

```
User: Bobathon is complete and validated

Bob will first ask:
"Would you like to update external resources and contact information?"

Options:
1. I'll edit them myself (default)
   - Bob provides file locations and line numbers
   - You manually update placeholders

2. Have Bob update them
   - Bob asks for documentation URLs
   - Bob asks for support contact info
   - Bob updates both files automatically
   - Handles unknown items (placeholder/delete/skip)

3. Skip for now
   - Keep template placeholders
   - Update before delivery

Then Bob will ask:
"How would you like to save it?"

Options:
1. Export to new directory (../acme-corp-bobathon/)
   - Creates clean, standalone bobathon
   - Optionally removes template files
   - Provides git init instructions

2. Prepare for new repository
   - Asks for target repo URL
   - Creates branch and commits
   - Provides exact push commands

3. Create branch in this repo
   - Branch: bobathon-acme-corp
   - Keeps with template
   - Easy to maintain multiple clients

4. Commit to current branch
   - Simple commit
   - Manual git workflow
```

### Validation is Mandatory

**Important:** Bob will ALWAYS run validation before presenting save options. This is non-negotiable and ensures:
- Complete bobathon materials
- No missing required elements
- Consistent quality across all deliverables
- Ready-to-use package for facilitators

If you try to save without validation passing, Bob will:
1. Stop the save process
2. Run validation automatically
3. Report what needs to be fixed
4. Offer to fix issues
5. Only proceed after validation passes

**Example: Validation Before Save**
```
User: "Save the bobathon"

Bob: "Running mandatory validation first..."
[Validation runs]
Bob: "❌ Validation found 3 issues:
1. Code generation strategy not set
2. Lab 1 missing Bob differentiators section
3. Dollar amounts found in Lab 2 business impact

Would you like me to fix these issues?"

User: "Yes, fix them"

Bob: [Fixes issues]
Bob: "✅ All issues resolved. Running validation again..."
[Validation passes]
Bob: "✅ Validation passed! How would you like to save the bobathon?"
```

**Example: Update Resources with Bob**
```
Bob: "Would you like to update external resources and contact information?"
User: "Have Bob update them"

Bob: "What are your Bob documentation URLs?"
User: "Main docs: https://docs.bob.com, API: https://api.bob.com"

Bob: "Do you have company-specific resources to add?"
User: "Yes, internal wiki: https://wiki.acme.com/bob"

Bob: "What are the after-bobathon support contact details?"
User: "Email: bob-support@acme.com, Slack: #bob-help, Office hours: Mon-Fri 2-4pm EST"

Bob will:
1. Update resources/external-links.md with documentation links
2. Add company resources to external-links.md
3. Update resources/troubleshooting.md with support contacts
4. Report what was updated and any remaining placeholders
```

**Example: Export to New Directory**
```
Bob: "Should I remove template-specific files?"
User: "Yes, create a clean bobathon"

Bob will:
1. Create ../acme-corp-bobathon/
2. Copy bobathon files
3. Remove .bob/, .bobmodes, examples/
4. Provide git commands:
   cd ../acme-corp-bobathon
   git init
   git add .
### 7. Business Value Tracking
**Set up business value tracking when:**
- You want to demonstrate ROI to stakeholders
- Client needs metrics for adoption decisions
- You're measuring bobathon effectiveness
- Building case studies for future clients

**Collection strategy:**
- **Comprehensive** (recommended): After each lab + end of bobathon + 2-4 week follow-up
- **Balanced**: After each lab + end of bobathon
- **Minimal**: End of bobathon only

**Metrics to capture:**
- Time savings (hours/week)
- Quality improvements (% bugs caught)
- Security enhancements (vulnerabilities prevented)
- Efficiency gains (time saved per task)
- Adoption rate (% of team using Bob)
- Ease of use (1-5 scale)
- Likelihood to adopt (1-5 scale)

**IMPORTANT:** Never use dollar amounts in productivity or savings statements. Use time-based metrics (hours saved) or percentage improvements instead.

### 8. Bob Differentiators (MANDATORY)
**Every lab must include Bob differentiators inline:**

Bob differentiators should be woven into the lab content, not just listed separately. They must:
- Relate to specific exercises in the lab
- Show practical value, not just list features
- Demonstrate what makes Bob unique vs. other AI tools
- Help participants understand why Bob is different

**Required differentiators to cover across labs:**
1. **Literate Coding** - Understanding and explaining code in natural language
2. **Multi-Mode Intelligence** - Ask, Plan, Code modes with different reasoning
3. **Bob Findings** - Proactive security and quality analysis
4. **Smart Auto-Approval** - Configurable trust levels for operations
5. **Intelligent Model Selection** - Automatic optimization per task
6. **Context Optimization** - Efficient handling of large codebases
7. **Extensible Architecture** - MCP server integrations
8. **Enterprise Modernization** - Java and legacy code transformation

**Best practice:** Include 4-5 differentiators per lab, tied to exercises that demonstrate them.

   git commit -m "Initial bobathon for Acme Corp"
   git remote add origin [your-url]
   git push -u origin main
```

**Example: Prepare for New Repository**
```
Bob: "What's the target repository URL?"
User: "https://github.com/myorg/acme-bobathon.git"

Bob: "Remove template files?"
User: "Yes"

Bob will:
1. Create branch bobathon-acme-corp
2. Remove template files
3. Commit changes
4. Provide commands:
   git remote add acme https://github.com/myorg/acme-bobathon.git
   git push acme bobathon-acme-corp:main
```
```

## 💡 Tips for Best Results

### 1. Be Specific
Instead of: "Create a bobathon"
Try: "Create a bobathon for a healthcare client using Python and Django"

### 2. Use the Suggestions
Bob provides 2-4 suggestions for each question - use them to save time!

### 3. Start from Examples
If your client is similar to an example, start there:
- Financial Services → `examples/sample-config-fintech.yaml`
- Healthcare → `examples/sample-config-healthcare.yaml`

### 4. Choose Lab Technology Wisely
**Use client technology for Labs 1 & 2 when:**
- Client uses a specific, less common language/framework
- Team is new to their tech stack and needs practice
- You have time for full customization
- Examples in client's tech will be more engaging

**Use generic examples when:**
- Client uses common languages (Python, JavaScript, Java)
- Time is limited (3-hour bobathon)
- Focus is on Bob concepts, not language specifics
- Team is experienced with their stack

### 5. Code Generation Strategy (MANDATORY)

**You MUST choose one of these options for every bobathon:**

**1. Generate both starter code and solutions (recommended) when:**
- You want a complete, ready-to-deliver bobathon
- Facilitators need reference implementations
- Participants benefit from seeing working examples
- Time allows for code review and customization
- **Best for:** Standard bobathons, new facilitators, complete packages

**2. Generate starter code only when:**
- You want participants to build solutions during the bobathon
- Focus is on learning by doing
- Facilitators are comfortable creating solutions on the fly
- **Best for:** Hands-on learning focus, experienced facilitators

**3. Generate solutions only when:**
- You have custom starter code to provide separately
- Need flexibility for unique scenarios
- Solutions serve as reference for facilitators
- **Best for:** Custom starter code requirements, specific client needs

**4. Have Bob generate code live during labs when:**
- You want to demonstrate Bob's capabilities in real-time
- Most interactive and engaging approach
- Facilitators are very experienced with Bob
- **Best for:** Showcasing Bob's power, advanced facilitators

**5. No code generation when:**
- You have existing code samples to use
- Labs will use client's actual codebase
- You prefer complete manual control
- **Best for:** Using actual client code, very specific requirements

**This decision is mandatory and affects:**
- Lab delivery approach
- Facilitator preparation needs
- Participant experience
- Time requirements
- Materials completeness

### 6. Validate Before Delivery
Always run validation before considering the bobathon complete:
```
Validate the bobathon materials and fix any issues
```

### 6. Iterate as Needed
You can always ask Bob to adjust:
```
The Lab 3 scenarios are too complex, simplify them
Add more time to the API development use case
Change the tech stack from Java to Python
```

## 🎓 Understanding the Mode

### What the Mode Can Do

✅ **Read and analyze:**
- Bobathon configuration
- Lab instructions
- Schedule files
- Example configs
- Resource files

✅ **Edit and create:**
- `bobathon-config.yaml`
- Lab instructions (`labs/*.md`)
- Schedule files (`schedule/*.md`)
- Example configs (`examples/*.yaml`)
- Resource files (`resources/*.md`)

✅ **Execute commands:**
- Validation scripts
- File operations
- Testing commands

### What the Mode Cannot Do

❌ **Cannot edit:**
- Files outside the bobathon template
- System files
- Unrelated project files

❌ **Cannot access:**
- External APIs (unless via MCP)
- Network resources
- Browser actions

### Mode Restrictions

The mode is restricted to bobathon-related files for safety:
- Prevents accidental changes to other files
- Ensures focus on bobathon preparation
- Maintains template integrity

## 🔍 Troubleshooting

### Issue: Mode Not Appearing

**Solution:**
1. Verify `.bobmodes` file exists in workspace root
2. Reload VS Code window
3. Check Bob is properly installed and activated

### Issue: Bob Asks Too Many Questions

**Solution:**
- This is intentional! The mode gathers complete information upfront
- Use the suggestions to answer quickly
- You can provide multiple answers at once:
  ```
  Client: Acme Corp, Financial Services
  Tech: Java, Spring Boot, PostgreSQL
  Use cases: API development, security compliance, testing
  ```

### Issue: Generated Config Has Errors

**Solution:**
1. Ask Bob to validate: "Validate the bobathon materials"
2. Bob will identify and fix issues
3. Review the validation report

### Issue: Labs Don't Match Tech Stack

**Solution:**
```
The labs still use Python but our client uses Java. 
Please update all labs to use Java and Spring Boot.
```

### Issue: Timing Doesn't Fit

**Solution:**
```
We have 4 hours instead of 6. Adjust the schedule and 
prioritize the high-priority use cases.
```

## 📚 Additional Resources

### Mode Documentation
- `.bob/rules-bobathon-builder/1_workflow.xml` - Detailed workflows
- `.bob/rules-bobathon-builder/2_validation_rules.xml` - Validation rules
- `.bob/rules-bobathon-builder/3_best_practices.xml` - Best practices

### Template Documentation
- `README.md` - Main template documentation
- `.bob/instructions.md` - General Bob instructions
- `schedule/detailed-agenda.md` - Schedule template
- `resources/cheat-sheet.md` - Bob quick reference

### Examples
- `examples/sample-config-fintech.yaml` - Financial services example
- `examples/sample-config-healthcare.yaml` - Healthcare example

## 🎯 Success Checklist

Before delivering a bobathon, ensure:

- [ ] `bobathon-config.yaml` is complete (no placeholders)
- [ ] All labs use client's tech stack
- [ ] All labs have Business Impact sections
- [ ] Real-time value indicators embedded in exercises
- [ ] Lab 3 addresses client's use cases with business value metrics
- [ ] Business value tracking configured (if enabled)
- [ ] Survey questions generated for data collection
- [ ] **Code generation strategy explicitly set (MANDATORY)**
- [ ] Code generated according to selected strategy
- [ ] Starter code exists in labs/*/starter/ (if strategy includes starter)
- [ ] Solution code exists in labs/*/solution/ (if strategy includes solutions)
- [ ] README files exist in appropriate directories
- [ ] Generated code matches client's tech stack
- [ ] If live generation: instructions include facilitator guidance
- [ ] If no generation: instructions explain code source
- [ ] **Bob differentiators included inline in each lab (MANDATORY)**
- [ ] At least 4-5 differentiators explained per lab
- [ ] Differentiators tied to specific exercises
- [ ] **No dollar amounts ($) in any business impact statements**
- [ ] Timing calculations are correct
- [ ] Schedule matches available time
- [ ] All materials are consistent
- [ ] Validation passes with no errors
- [ ] Examples are specific to client
- [ ] No generic placeholders remain

## 🤝 Getting Help

### During Bobathon Preparation

Ask Bob directly:
```
How do I customize Lab 2 for a Django project?
What's the best way to structure Lab 3 scenarios?
Can you explain the validation errors?
Generate sample code for Lab 1 using Python and Flask
Should I generate solutions or just starter code?
```

### After Bobathon Delivery

- Review participant feedback
- Update template based on learnings
- Share improvements with team
- Document lessons learned

## 📞 Support

If you encounter issues with the Bobathon Builder mode:

1. **Check this guide** for common solutions
2. **Review the mode documentation** in `.bob/rules-bobathon-builder/`
3. **Ask Bob for help** - it can explain its own capabilities
4. **Contact support** - [your support channel]

## 🎉 You're Ready!

You now know how to:
- ✅ Install and activate the Bobathon Builder mode
- ✅ Create new bobathons from scratch
- ✅ Customize labs and materials
- ✅ Validate bobathon quality
- ✅ Troubleshoot common issues

**Next Step:** Switch to Bobathon Builder mode and create your first bobathon!

```
Help me create a new bobathon for [Your Client Name]
```

---

**Version:** 1.0.0
**Last Updated:** 2026-01-15
**Template:** Bob Client Bobathon Starter