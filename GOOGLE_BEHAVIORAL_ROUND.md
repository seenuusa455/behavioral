# Google Behavioral Round — Key Questions

---

## Table of Contents

1. [Tell Me About Yourself](#1-tell-me-about-yourself)
2. [Difficult Colleague](#2-tell-me-about-a-time-when-you-had-a-colleague-who-was-difficult-to-work-with)
3. [Received Negative Feedback](#3-tell-me-about-a-time-you-received-negative-feedback)
4. [Mentoring Feedback Not Getting Through](#4-tell-me-about-a-time-you-were-mentoring-a-junior-engineer-and-your-feedback-wasnt-getting-through)
5. [Plan a Team Offsite](#5-if-you-were-going-to-plan-an-offsite-for-the-team-how-would-you-do-it)

---

## 1. Tell Me About Yourself

I'm Srinivas Balusu, a Lead Software Engineer with about 14 years of experience building large-scale distributed systems and cloud platforms.

Over the years, I've naturally gravitated toward backend infrastructure and high-scale distributed systems — especially problems around scalability, reliability, performance optimization, and platform modernization. I enjoy working on systems that operate at meaningful scale and require balancing architectural tradeoffs with practical operational realities.

At Railinc, I currently lead two major systems: a Managed File Transfer platform processing over 1 million files daily, and a Kafka-based event pipeline handling more than 50 million events per day. Both run on AWS infrastructure using services like EKS, Transfer Family, and EFS, and I'm involved across the full lifecycle — architecture, development, performance optimization, and production operations.

Before Railinc, I worked at Walmart on supply chain automation systems. One project I'm particularly proud of involved solving a latency problem that many on the team believed wasn't achievable within the required SLA. I redesigned the processing approach using a pre-generation architecture, and the solution eventually contributed to roughly $12 million in annual operational savings.

What I enjoy most about engineering is solving complex technical problems while also helping teams scale effectively — whether that's improving system reliability, simplifying architectures, mentoring engineers, or driving better engineering practices such as code reviews, automated testing, CI/CD adoption, observability, performance optimization, incident management, and establishing engineering standards that improve delivery quality and maintainability.

At this stage of my career, I'm looking for opportunities to work on even larger-scale systems alongside strong engineering teams, where I can continue growing as a technical leader and contribute to long-term platform and architectural decisions.

---

## 2. Tell Me About a Time When You Had a Colleague Who Was Difficult to Work With

**Story: PR Review Friction at Railinc**

**Context:** A developer on my team consistently submitted PRs with missing error handling, no input validation, and inconsistent naming. I left thorough review comments explaining the issues. His response: he got visibly frustrated, started avoiding reviews, and his PR turnaround time doubled. I wasn’t sure initially whether the problem was my communication style or his receptiveness — turns out it was both.

**Action:**
- I recognized the core issue: written comments lack tone. What I intended as helpful guidance was landing as personal criticism
- I invited him for a 1:1 coffee — not about code, just to connect as humans first
- I acknowledged his frustration directly: “I know detailed reviews can feel like someone picking apart your work. That’s not my intent.”
- I explained the *why*: “These patterns exist because we got burned in production. Missing error handling caused a 3 AM page last quarter.”
- I shifted my approach: instead of just flagging problems, I offered to pair-program on his next feature so he could see the patterns in context
- I categorized my future reviews: must-fix (blocking), should-fix (non-blocking), nit (optional)

**Result:** His code quality improved dramatically within 2 sprints. He started asking for early design feedback *before* writing code. He later became one of the team’s strongest contributors and started mentoring others on the same patterns.

**Learnings:** That experience taught me that feedback delivery matters as much as feedback content. I was technically right in every review comment, but being right doesn’t help if the person shuts down. I realized the deeper issue was that I was optimizing for code quality in isolation when I should have been optimizing for the person’s growth trajectory. Since then, I invest in the relationship first and the technical feedback follows naturally.

---

## 3. Tell Me About a Time You Received Negative Feedback

**Story: Code Reviews Too Detailed at Railinc**

**Context:** During a retrospective, a team member told me that my code reviews were too detailed and were slowing down the team. My initial reaction was defensive — I valued thoroughness and took pride in catching issues early. But I paused instead of reacting.

**Action:**
- I asked for specific examples rather than dismissing the feedback
- He showed me PRs where I’d left 30+ comments on non-critical style issues while the team was under deadline pressure. He was right — I was optimizing for code perfection when the team needed velocity
- I took a step back and realized I was applying the same level of scrutiny to a quick internal tool as I would to a production-critical payment path
- I changed my approach:
  - Categorized comments: must-fix (blocking), should-fix (non-blocking), nit (optional)
  - Only blocked PRs on must-fix items
  - Created a team style guide so style discussions happened once, not on every PR
  - Asked the team to flag if I slipped back into old patterns

**Result:** PR turnaround time improved significantly. Team velocity increased. And code quality stayed high because the must-fix items were still caught — I just stopped nitpicking things that didn’t matter at deployment time.

**Learnings:** That was a humbling moment. I realized I’d been conflating “thoroughness” with “value.” Not every comment I *can* leave is a comment I *should* leave. The deeper lesson is that feedback I receive about my own behavior deserves the same intellectual honesty I bring to technical problems. My first instinct to get defensive was the signal that the feedback was hitting something real. Since then, I actively seek critical feedback because I know that’s where my growth edges are.

---

## 4. Tell Me About a Time You Were Mentoring a Junior Engineer and Your Feedback Wasn’t Getting Through

**Story: Helping a Developer Who Was Too Embarrassed to Ask Questions**

**Context:** A developer on my team was consistently delivering 3-5 days late on every task. I’d given him written feedback multiple times — pointed out estimation issues, suggested breaking tasks smaller, shared documentation. None of it was working. His delivery kept slipping, and the team was getting frustrated because their work depended on his output.

**Action:**
- I realized my feedback was addressing the *symptom* (late delivery) but not the *cause*. Written tips about estimation don’t help if the person is stuck for a different reason entirely
- I took him to lunch — deliberately casual, one-on-one, away from the team
- I opened with curiosity, not critique: “I’ve noticed your tasks are taking longer than the estimates. I want to help — is there something blocking you that’s not visible in standup?”
- He admitted something he’d been hiding: he was struggling with Kafka and Kubernetes (newer technologies for him) and was too embarrassed to ask for help in front of the team
- That changed my approach completely. The problem wasn’t motivation or work ethic — it was psychological safety. He didn’t feel safe saying “I don’t know”
- I paired with him on his next task to identify exactly where he was getting stuck (it was Kafka consumer configuration, not the business logic)
- I offered to be his first call when stuck: “Text me before you spend 2 hours spinning. That’s not weakness, that’s efficiency.”
- I also normalized the struggle publicly in standup: “Kafka consumer configs tripped me up too when I first started — the documentation is awful”

**Result:** His delivery normalized within 2 sprints. He started asking for help proactively — in standup, openly. Six months later, he was the one helping new team members with Kafka.

**Learnings:** I learned that when feedback isn’t landing, the problem is usually not *what* you’re saying — it’s that you’re addressing the wrong root cause. My written feedback about estimation was technically correct but completely irrelevant to his actual blocker. That experience changed how I mentor: I now start by understanding *why* someone is struggling before I offer solutions. The other key insight is that psychological safety is a prerequisite for learning. If someone doesn’t feel safe admitting what they don’t know, no amount of good technical feedback will help.

---

## 5. If You Were Going to Plan an Offsite for the Team, How Would You Do It

**Answer:**

I’d approach it the same way I approach engineering problems — start with the goal, then design backward from there.

**Step 1: Define the purpose clearly**

Not all offsites are the same. I’d first clarify *what outcome we’re optimizing for*:
- Is this about team bonding (people who don’t know each other well)?
- Strategic alignment (team direction for next quarter)?
- Technical deep-dive (architecture decisions that need focused time)?
- Morale/celebration (after a tough delivery)?

The format should serve the goal, not the other way around.

**Step 2: Get input from the team**

I’d send a lightweight survey or async thread: “What would make this offsite valuable for you?” People are more engaged when they’ve shaped the agenda. I’d also ask about constraints — travel preferences, dietary needs, accessibility.

**Step 3: Design the agenda with intentional structure**

My framework:
- **Morning blocks:** Focused work (strategic planning, architecture discussions, retrospectives) — when energy is high
- **Afternoon blocks:** Collaborative/creative work (brainstorming, hackathon, team activities)
- **Unstructured time:** Deliberate gaps for organic conversations. Some of the best insights happen over coffee, not in sessions
- **One or two social activities:** Something that works for introverts AND extroverts — not just loud bars

**Step 4: For a distributed team specifically (which is my reality)**

- Schedule it when it maximizes overlap with offshore team members
- Make sure the offsite isn’t the only time people connect — it should reinforce existing relationships, not be the sole source of them
- Document outcomes and share async so people who couldn’t attend don’t feel excluded

**Step 5: Follow through**

The biggest failure mode of offsites is generating excitement that evaporates Monday morning. I’d assign owners to action items *during* the offsite and schedule a 2-week follow-up to check progress.

**What I’d avoid:**
- Wall-to-wall meetings with no breathing room
- Activities that alienate introverts or people with physical limitations
- Pure “fun” with no tangible outcome — people feel guilty about time away from work unless they see the value
- Planning it entirely top-down without team input

**Why this question matters for Google:**

This tests organizational thinking, empathy, and whether you can plan something cross-functional without being told exactly what to do. It’s a proxy for: *can this person take ambiguous ownership of something that isn’t strictly technical and still deliver a good outcome?*

---

## Quick Reference: Which Existing Stories Map Here

| Question | Primary Story | Also Pulls From |
|----------|--------------|-----------------|
| Tell me about yourself | 90-second intro | N/A |
| Difficult colleague | PR Review Friction | KT Buddy at Walmart (alternative) |
| Received negative feedback | Code Review Too Detailed | Could also use: Manager feedback on delegation |
| Mentoring not getting through | Late Developer + Kafka struggle | Interns at Walmart (alternative) |
| Plan an offsite | Original answer (no prior story) | Demonstrates organizational thinking |

---

*Prepared for Google L5 behavioral round.*
