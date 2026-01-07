# 🔍 PHASE 01: DISCOVERY

> **Validate the idea before building. This phase saves months of wasted effort.**

---

## 🎯 PURPOSE

Deeply understand what we're building and ensure it's worth building. This phase:
- Validates the problem is real and significant
- Identifies target users precisely
- Analyzes competitors and market
- Defines the unique value proposition
- Establishes success criteria

**Time Investment**: 1-2 hours
**Skip Risk**: Building something nobody wants

---

## 📥 INPUTS REQUIRED

- User's initial idea or concept
- User available to answer questions

---

## 📤 EXPECTED OUTPUTS

1. **Discovery Document** (`projects/[name]/docs/DISCOVERY.md`)
   - Problem statement
   - Target users
   - Competition analysis
   - Unique value proposition
   - Success metrics

2. **Updated State Files**
   - ACTIVE_PROJECT.md with project initialized
   - DECISION_LOG.md first entries

3. **Git Commit**
   - `[phase-01] init: discovery complete for [project-name]`

---

## 🔄 PROCESS

### Step 1: Problem Definition (Ask User)

Ask these questions in a conversational way:

```markdown
## DISCOVERY QUESTIONS

### The Problem
1. "What problem are you trying to solve?"
   - Get specific examples
   - Understand the pain level (annoyance vs critical)

2. "Who experiences this problem?"
   - Demographics
   - Context (work, personal, specific industry?)

3. "How are people solving this today?"
   - Existing solutions
   - Workarounds
   - Why are current solutions insufficient?

4. "How often does this problem occur?"
   - Daily? Weekly? Occasionally?
   - Frequency = urgency

### The Solution
5. "Describe your ideal solution in one sentence."
   - Forces clarity of vision

6. "What would make someone choose your solution over alternatives?"
   - The differentiator
   - The "10x better" factor

7. "If you could only build ONE feature, what would it be?"
   - Core value
   - MVP focus

### The Business (if applicable)
8. "How do you plan to make money?" (or "What's the goal?")
   - Subscription / One-time / Freemium / Free (growth) / Internal tool

9. "How many users do you expect?"
   - Month 1, Month 6, Year 1
   - Helps with architecture decisions later

10. "What's your timeline?"
    - MVP in 2 weeks? Production in 2 months?
    - Affects scope decisions
```

### Step 2: Market Research (Do Research)

Based on answers, research:

```markdown
## RESEARCH TASKS

### Competitor Analysis
- Find 3-5 competitors or alternatives
- For each, document:
  - Name and URL
  - Key features
  - Pricing
  - Strengths
  - Weaknesses
  - User reviews (if available)

### Market Size (Quick Estimate)
- How many potential users exist?
- Is the market growing, stable, or shrinking?
- Are there adjacent markets?

### Trends
- Is this problem becoming more or less relevant?
- Technology trends that affect this space?
- Regulatory considerations?
```

### Step 3: Value Proposition (Synthesize)

Create a clear value proposition:

```markdown
## VALUE PROPOSITION CANVAS

### For [target user]
### Who [has this problem/need]
### Our [product name]
### Is a [category]
### That [key benefit]
### Unlike [main alternative]
### Our product [key differentiator]

## ONE-LINER
[Product] helps [target user] [solve problem] by [key mechanism], 
unlike [alternatives] which [limitation].
```

### Step 4: Define Success (Metrics)

```markdown
## SUCCESS METRICS

### North Star Metric
What single metric best indicates success?
Example: "Monthly active users who complete at least 3 [key actions]"

### Leading Indicators
- User signups
- Feature adoption rate
- User engagement frequency

### Lagging Indicators
- Revenue (if monetized)
- User retention (30-day, 90-day)
- Net Promoter Score

### MVP Success Criteria
What constitutes a successful MVP?
- X users signed up
- Y% complete onboarding
- Z% return within a week
```

### Step 5: Risk Assessment

```markdown
## RISKS AND ASSUMPTIONS

### Key Assumptions
- List assumptions that must be true for this to work
- Rate each: High confidence / Medium / Needs validation

### Risks
| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| [Risk 1] | High/Med/Low | High/Med/Low | [How to address] |
| [Risk 2] | ... | ... | ... |

### Deal Breakers
- What would make this project not worth pursuing?
- Are any deal breakers present?
```

### Step 6: Validate & Document

Create the Discovery Document:

```markdown
# Discovery Document: [Project Name]

## Executive Summary
[2-3 sentence overview]

## Problem Statement
[Clear description of the problem]

## Target Users
### Primary User
- Who: [Description]
- Pain Points: [List]
- Current Solution: [What they do now]

### Secondary Users (if applicable)
[Same format]

## Competition Analysis
| Competitor | Strengths | Weaknesses | Our Advantage |
|------------|-----------|------------|---------------|
| [Name 1]   | ...       | ...        | ...           |
| [Name 2]   | ...       | ...        | ...           |

## Value Proposition
[One-liner from Step 3]

## Success Metrics
[From Step 4]

## Risks & Assumptions
[From Step 5]

## Go/No-Go Recommendation
[Clear recommendation with reasoning]

## Next Steps (if Go)
1. Proceed to Phase 02: Requirements
2. Define core features
3. Create user stories
```

---

## ✅ QUALITY GATE

Before proceeding to Phase 02, verify:

- [ ] Problem is clearly defined and validated
- [ ] Target users are specifically identified
- [ ] At least 3 competitors analyzed
- [ ] Unique value proposition articulated
- [ ] Success metrics defined
- [ ] Risks identified and assessed
- [ ] Discovery document created and saved
- [ ] User has confirmed understanding via conversation
- [ ] ACTIVE_PROJECT.md updated
- [ ] Git commit made

---

## 📚 KNOWLEDGE REFERENCES

This phase is primarily about research and questioning.
No technical knowledge documents needed yet.

---

## ⚠️ COMMON MISTAKES

### Mistake 1: Skipping Discovery
"I know what I want to build" - Famous last words.
Even if you're confident, document it. Future you will thank you.

### Mistake 2: Vague Problem Definition
"It helps people be more productive" - Too vague.
Be specific: "It helps remote team managers track project progress without 
asking for status updates, reducing update meetings by 50%."

### Mistake 3: Ignoring Competition
"There's nothing like this" - Almost never true.
There's always an alternative, even if it's spreadsheets or doing nothing.

### Mistake 4: Feature Focus Instead of Problem Focus
Don't start with "I want to build X feature."
Start with "I want to solve Y problem."

### Mistake 5: Building for Everyone
"Anyone can use it" = No one will use it.
Narrow is better at the start.

---

## 💡 TIPS

### Tip 1: Ask "Why" Five Times
When user states a problem, ask why. Keep asking until you reach root cause.

### Tip 2: Look for Emotional Language
When user says "frustrated," "hate," "waste time" - you've found real pain.

### Tip 3: Validate Willingness to Pay
"Would you pay $X for this?" gets more honest answers than assumed interest.

### Tip 4: Smaller is Better
For MVP, cut scope aggressively. You can always add more.

### Tip 5: Document Everything
Assumptions made now will be forgotten later. Write them down.

---

## 📝 EXAMPLE OUTPUT

```markdown
# Discovery Document: TaskFlow

## Executive Summary
TaskFlow is a project management tool for small remote teams (5-15 people) 
that automatically collects status updates from connected tools, eliminating 
daily standup meetings and async status requests.

## Problem Statement
Remote team managers spend 3-5 hours per week collecting status updates 
through Slack messages, meetings, and email. Team members spend 15-30 minutes 
daily reporting status across multiple channels. This is tedious, error-prone, 
and interrupts deep work.

## Target Users
### Primary: Remote Team Manager
- Leading team of 5-15 people
- Uses project management tools (Jira, Asana, Linear)
- Conducts daily or weekly standups
- Pain: Constantly asking "what's the status of X?"

### Secondary: Individual Contributors
- Works on remote team
- Uses multiple tools for work
- Pain: Interrupted to give status updates

## Competition Analysis
| Tool | Strengths | Weaknesses | Our Advantage |
|------|-----------|------------|---------------|
| Geekbot | Async standups | Manual input required | Auto-collection |
| Range | Good integrations | Expensive | Simpler, cheaper |
| Status Hero | Simple | Limited integrations | More integrations |

## Value Proposition
TaskFlow gives remote team managers real-time project visibility by 
automatically collecting status from connected tools, unlike Geekbot or 
manual standups which require team members to manually report.

## Success Metrics
- North Star: Weekly active teams with 3+ connected tools
- MVP Success: 50 teams, 60% weekly retention

## Go/No-Go: GO
Strong problem, validated by user experience, clear differentiation, 
reasonable MVP scope.
```

---

**Phase Complete? Update ACTIVE_PROJECT.md and proceed to Phase 02: Requirements.**
