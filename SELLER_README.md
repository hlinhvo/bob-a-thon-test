<!--
---
bob_context:
  template_type: "client_bobathon"
  version: "1.0.0"
  primary_config: "bobathon-config.yaml"
  
instructions_for_bob: |
  This is a bobathon (Bob bootcamp) template for training clients on Bob usage.
  
  IMPORTANT: Always read bobathon-config.yaml first to understand the client context.
  
  Key files:
  - bobathon-config.yaml: Client info, tech stack, use cases, schedule
  - .bob/instructions.md: Detailed instructions for you (Bob)
  - labs/: Lab exercises to customize for client
  - schedule/: Timing and agenda templates
  - examples/: Sample configs for different industries
  
  When helping with this template:
  1. Read bobathon-config.yaml to understand client needs
  2. Tailor all examples to their tech stack
  3. Use their actual use cases and priorities
  4. Respect their time constraints and schedule
  5. Reference their specific tools and frameworks
  
  For detailed guidance, read .bob/instructions.md

quick_start_for_bob: |
  User asks for bobathon help → Read bobathon-config.yaml → Understand context →
  Read relevant template files → Customize for client → Provide tailored assistance

common_tasks:
  - customize_labs: "Read config + lab instructions, update for client's tech stack"
  - adjust_schedule: "Read config + schedule, modify timing based on constraints"
  - create_use_cases: "Read config, develop scenarios using client's actual problems"
  - prepare_materials: "Read all relevant files, ensure consistency with client context"
---
-->
# Client Bobathon Starter Template

A comprehensive template for delivering customized Bobathons (Bob Bootcamps) to clients. This template provides everything needed to plan, execute, and follow up on a successful one-day Bob training session.

## 📋 Overview

This bobathon template is designed to help clients learn Bob through a structured, hands-on approach. The default format is a 6-hour session with:
- **Morning (3 hours):** Introduction and core Bob features
- **Lunch (1 hour):** Break
- **Afternoon (3 hours):** Client-specific use cases and implementation

## 🎯 What's Included

### Core Files
- **`bobathon-config.yaml`** - Main configuration file that Bob consumes
- **`README.md`** - This file, with instructions for using the template
- **`BOBATHON_BUILDER_GUIDE.md`** - Complete guide for using the Bobathon Builder mode
- **`.bobmodes`** - Custom mode configuration for guided bobathon creation
- **`schedule/detailed-agenda.md`** - Comprehensive timing breakdown and facilitator guide

### Lab Exercises
- **`labs/lab1-basic-operations/`** - Beginner-level exercises for core Bob features
- **`labs/lab2-advanced-workflows/`** - Intermediate exercises for complex scenarios
- **`labs/lab3-client-specific/`** - Advanced exercises tailored to client needs

### Resources
- **`resources/bob-differentiators.md`** - What makes Bob unique (NEW!)
- **`resources/cheat-sheet.md`** - Quick reference guide for Bob commands
- **`resources/troubleshooting.md`** - Common issues and solutions
- **`resources/external-links.md`** - Curated external resources

### Examples
- **`examples/`** - Sample configurations for different industries

## 🚀 Quick Start

### Option A: Use the Bobathon Builder Mode (Recommended)

The easiest way to create a customized bobathon is using the **Bobathon Builder** mode, which guides you through an interactive Q&A process.

**📖 [Read the Bobathon Builder Guide](BOBATHON_BUILDER_GUIDE.md)** for complete installation and usage instructions.

**Quick Start:**
1. Open this project with Bob
2. Switch to "🎓 Bobathon Builder" mode
3. Say: "Help me create a new bobathon for [Client Name]"
4. Answer the guided questions
5. Bob will generate and validate all materials

### Option B: Manual Configuration

If you prefer to manually edit the configuration:

#### 1. Clone or Copy This Template
```bash
git clone <repository-url>
cd bob_client_bobathon_starter
```

#### 2. Customize the Configuration
Edit `bobathon-config.yaml` with your client's information:

```yaml
client:
  name: "Acme Corporation"
  market: "Financial Services"

technologies:
  primary_language: "Python"
  frameworks: ["Django", "React"]
  infrastructure: "AWS"

use_cases:
  - name: "API Development"
    description: "Build RESTful APIs faster"
    priority: "high"
```

#### 3. Prepare Lab Materials
Customize the lab exercises in the `labs/` directory based on your client's:
- Technology stack
- Use cases
- Skill level
- Actual codebase

**Tip:** You can ask Bob to help customize labs even without using the Bobathon Builder mode.

#### 4. Review the Schedule
Check `schedule/detailed-agenda.md` and adjust timing if needed:
- Compress for half-day format (3 hours)
- Expand for two-day format (12 hours)
- Adjust for virtual vs. in-person delivery

### 5. Deliver the Bobathon
Follow the detailed agenda and use Bob to demonstrate capabilities in real-time.

## 📖 Detailed Instructions

### Customizing for Your Client

#### Step 1: Gather Client Information
Before customizing the template, collect:
- Client name and industry
- Technology stack and tools
- Key pain points and use cases
- Team size and skill levels
- Available time and format preferences

#### Step 2: Update bobathon-config.yaml
This is the most important file. Bob will read this to understand the client context.

**Required Sections:**
- `client` - Basic client information
- `technologies` - Tech stack details
- `use_cases` - Specific scenarios to address
- `schedule` - Timing and agenda

**Optional Sections:**
- `resources` - External documentation and APIs
- `participants` - Team composition
- `success_criteria` - Measurable outcomes
- `follow_up` - Post-bobathon support plan

#### Step 3: Customize Lab Exercises

**Lab 1: Basic Operations (30 minutes)**
- Keep this generic but use client's tech stack
- Focus on fundamental Bob commands
- Ensure everyone completes successfully

**Lab 2: Advanced Workflows (30 minutes)**
- Introduce complexity gradually
- Use realistic scenarios from client's domain
- Include debugging and refactoring

**Lab 3: Client-Specific (90 minutes)**
- Use actual client codebase if possible
- Address real problems from their backlog
- Demonstrate tangible value and ROI

#### Step 4: Prepare Resources
- Update cheat sheet with client-specific examples
- Add troubleshooting for client's environment
- Curate external links relevant to their stack

## 🌟 Bob's Unique Differentiators

Understanding what makes Bob unique helps you deliver more impactful bobathons. Bob stands out in four key areas:

### 1. 🔧 Extensible Architecture
- **Custom Modes**: Tailor AI behavior for specific workflows (Code, Ask, Plan, or create your own)
- **MCP Server Integration**: Connect external tools and services directly into development workflow
- **Marketplace**: Share and discover custom modes created by the community

### 2. 🧠 Intelligent Resource Optimization
- **Automatic Model Selection**: Bob chooses the right AI model for each task (Frontier-class for complex, lighter for simple)
- **Dynamic Context Management**: Efficient compression and prioritization reduces costs by up to 60%
- **Transparent Operation**: No cognitive load of choosing models yourself

### 3. 🔍 Bob Findings: Automated Analysis
- **Security Scanning**: Continuous vulnerability detection with remediation recommendations
- **Code Quality**: Intelligent refactoring suggestions to reduce technical debt
- **Compliance**: Enforcement of best practices across your codebase
- **Proactive**: Catches issues before they reach production

### 4. ☕ Enterprise Java Modernization
- **Deep Integration**: Works with IBM's Application Modernization Accelerator
- **J2EE to Liberty**: Automated migration with minimal manual intervention
- **Version Upgrades**: Seamless Java version migrations (8 → 11 → 17 → 21)
- **Beyond Java**: Can modernize other languages too (Python, JavaScript, PHP, Ruby, .NET)

**📖 For complete details, see [`resources/bob-differentiators.md`](resources/bob-differentiators.md)**

### Why This Matters for Your Bobathon

When delivering bobathons, emphasize these differentiators:
- **Morning Session**: Introduce modes, Bob Findings, and literate coding
- **Advanced Session**: Demonstrate MCP integrations and intelligent optimization
- **Client Session**: Show how differentiators solve their specific problems
- **Throughout**: Let participants experience automatic model selection naturally

## 🎓 Bobathon Structure

### Morning Session (3 hours)

#### Introduction & Setup (30 min)
- Welcome and objectives
- Bob overview and capabilities
- Environment verification

#### Basic Bob Features (90 min)
- Core commands and navigation
- File operations and code editing
- **Lab 1:** Hands-on practice with basic operations

#### Advanced Bob Features (60 min)
- Complex workflows and multi-step tasks
- Advanced editing techniques
- **Lab 2:** Intermediate scenarios and refactoring

### Afternoon Session (3 hours)

#### Customer-Specific Use Cases (150 min)
- Review client's key use cases
- Walkthrough of client's codebase
- **Lab 3:** Extended hands-on with real scenarios
- Best practices for client's environment

#### Wrap-up & Next Steps (30 min)
- Key takeaways and lessons learned
- Resources and support channels
- Action items and follow-up plan

## 📊 Time Allocation

| Component | Duration | Percentage |
|-----------|----------|------------|
| Introduction | 30 min | 8% |
| Basic Features | 90 min | 25% |
| Advanced Features | 60 min | 17% |
| Client-Specific | 150 min | 42% |
| Wrap-up | 30 min | 8% |
| **Total** | **6 hours** | **100%** |

## 🛠️ Lab Exercise Guidelines

### Creating Effective Labs

**Lab 1: Basic Operations**
- **Goal:** Build confidence with core commands
- **Duration:** 30 minutes
- **Difficulty:** Beginner
- **Format:** Guided exercises with clear instructions
- **Success:** Everyone completes all exercises

**Lab 2: Advanced Workflows**
- **Goal:** Handle complex, multi-step tasks
- **Duration:** 30 minutes
- **Difficulty:** Intermediate
- **Format:** Semi-guided with problem-solving
- **Success:** Most complete, all understand concepts

**Lab 3: Client-Specific**
- **Goal:** Apply Bob to real business problems
- **Duration:** 90 minutes
- **Difficulty:** Advanced
- **Format:** Open-ended with facilitator support
- **Success:** Tangible solutions to real problems

### Lab Structure Template

Each lab should include:
1. **Objectives** - What participants will learn
2. **Prerequisites** - Required knowledge and setup
3. **Instructions** - Step-by-step guidance
4. **Exercises** - Hands-on tasks to complete
5. **Solutions** - Reference implementations
6. **Discussion Points** - Key takeaways

## 🎯 Success Criteria

### Immediate (End of Bobathon)
- ✅ All participants can use Bob independently
- ✅ 80%+ complete all three labs
- ✅ Average satisfaction rating ≥ 4/5
- ✅ Clear understanding of support channels

### Short-term (1-2 weeks)
- ✅ Active daily usage by participants
- ✅ At least one use case in production
- ✅ Questions resolved through support

### Long-term (1 month)
- ✅ Measurable productivity improvements
- ✅ Team adoption rate ≥ 70%
- ✅ Additional use cases identified

## 📝 Facilitator Checklist

### Before the Bobathon
- [ ] Review and customize `bobathon-config.yaml`
- [ ] Prepare all lab exercises with client context
- [ ] Test labs in client's environment
- [ ] Set up communication channels
- [ ] Prepare demo environment
- [ ] Send pre-bobathon materials to participants
- [ ] Confirm logistics (time, location, tools)

### During the Bobathon
- [ ] Start with quick wins to build confidence
- [ ] Encourage questions and interaction
- [ ] Monitor pace and adjust as needed
- [ ] Provide real-time support during labs
- [ ] Capture questions for follow-up
- [ ] Take notes on what works well

### After the Bobathon
- [ ] Send follow-up email with resources
- [ ] Schedule office hours session
- [ ] Collect and review feedback
- [ ] Update template based on learnings
- [ ] Check in on action items
- [ ] Plan advanced topics workshop

## 🔧 Customization Options

### Half-Day Format (3 hours)
```yaml
schedule:
  total_duration_hours: 3
  
  segments:
    - Introduction: 15 min
    - Basic Features: 45 min
    - Advanced Topic: 30 min
    - Client Lab: 60 min
    - Wrap-up: 15 min
```

### Two-Day Format (12 hours)
```yaml
schedule:
  total_duration_hours: 12
  
  day1:
    - Deep dive into Bob features
    - Extensive practice labs
    - Advanced topics and patterns
  
  day2:
    - Client-specific implementation
    - Real-world problem solving
    - Team collaboration exercises
```

### Virtual Format Adjustments
- Add 15-min breaks every 90 minutes
- Use breakout rooms for labs
- Provide pre-recorded demos
- Use collaborative tools (Miro, Mural)
- Record sessions for later review

## 📚 Additional Resources

### For Facilitators
- `schedule/detailed-agenda.md` - Comprehensive timing guide
- `schedule/facilitator-guide.md` - Tips and best practices
- `resources/troubleshooting.md` - Common issues

### For Participants
- `resources/cheat-sheet.md` - Quick reference
- `resources/external-links.md` - Learning resources
- Lab solutions in each lab's `solution/` directory

## 🤝 Support

### During Bobathon
- Facilitator provides real-time support
- Use dedicated Slack/Teams channel
- Screen sharing for troubleshooting

### Post-Bobathon
- Office hours (weekly for first month)
- Email support
- Community forum access
- Documentation and guides

## 📞 Contact

For questions about this template or Bob bobathons:
- **Email:** [support@example.com]
- **Slack:** [#bob-bobathons]
- **Documentation:** [docs.example.com]

## 📄 License

This template is provided as-is for use in Bob client bobathons.

## 🔄 Version History

- **v1.0.0** - Initial template release
  - 6-hour default format
  - Three lab exercises
  - Comprehensive configuration file
  - Detailed agenda and facilitator guide

## 🙏 Acknowledgments

This template was created based on successful Bob bobathons delivered to clients across various industries. Special thanks to all the facilitators and participants who provided feedback to improve this template.

---

**Ready to get started?** Edit `bobathon-config.yaml` with your client's information and begin customizing the labs!