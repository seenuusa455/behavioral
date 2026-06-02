# Refined Behavioral Answers — Google L5 Interview
## Srinivas Balusu | Lead Software Engineer → Targeting Senior SWE at Google

---

## Table of Contents

1. [Tell Me About Yourself](#1-tell-me-about-yourself)
2. [Why Move from Lead to Senior at Google?](#2-why-move-from-lead-engineer-to-senior-engineer-at-google)
3. [Favorite Project — ACL System at Walmart](#3-favorite-project--acl-system-at-walmart)
4. [Conflict Story — Architecture Debate at Walmart](#4-conflict-story--architecture-debate-at-walmart)
5. [Ambiguity Story — Building MFT Platform from Scratch](#5-ambiguity-story--building-mft-platform-from-scratch)

---

## 1. Tell Me About Yourself

I'm Srinivas Balusu, a Lead Software Engineer with about 14 years of experience building large-scale distributed systems and cloud platforms.

Over the years, I've naturally gravitated toward backend infrastructure and high-scale distributed systems — especially problems around scalability, reliability, performance optimization, and platform modernization. I enjoy working on systems that operate at meaningful scale and require balancing architectural tradeoffs with practical operational realities.

At Railinc, I currently lead two major systems: a Managed File Transfer platform processing over 1 million files daily, and a Kafka-based event pipeline handling more than 50 million events per day. Both run on AWS infrastructure using services like EKS, Transfer Family, and EFS, and I'm involved across the full lifecycle — architecture, development, performance optimization, and production operations.

Before Railinc, I worked at Walmart on supply chain automation systems. One project I'm particularly proud of involved solving a latency problem that many on the team believed wasn't achievable within the required SLA. I redesigned the processing approach using a pre-generation architecture, and the solution eventually contributed to roughly $12 million in annual operational savings.

What I enjoy most about engineering is solving complex technical problems while also helping teams scale effectively — whether that's improving system reliability, simplifying architectures, mentoring engineers, or driving better engineering practices such as code reviews, automated testing, CI/CD adoption, observability, performance optimization, incident management, and establishing engineering standards that improve delivery quality and maintainability.

At this stage of my career, I'm looking for opportunities to work on even larger-scale systems alongside strong engineering teams, where I can continue growing as a technical leader and contribute to long-term platform and architectural decisions.

---

## 2. Why Move from Lead Engineer to Senior Engineer at Google?

### Q: Why move from Lead Engineer at a smaller company to Senior Engineer at Google?

**Answer:**

I’ve genuinely enjoyed my time at Railinc and had the opportunity to work on several large-scale distributed systems with significant ownership. Over the years, I’ve grown from primarily focusing on implementation to leading architecture decisions, modernization efforts, and operating critical production systems at scale.

At this point in my career, I feel I’m looking for a different level of engineering challenge — particularly environments where the scale, complexity, and engineering rigor are even higher. I’m especially motivated by solving deeply distributed systems problems alongside very strong engineers who push my thinking and help me continue growing technically.

That’s one of the biggest reasons Google is exciting to me. The kinds of systems Google operates — globally distributed infrastructure, large-scale data processing, reliability engineering, platform architecture — align very closely with the areas I enjoy most.

For me, this move isn’t really about titles. I see Google’s Senior Software Engineer role as an opportunity to operate at a much larger technical scale, learn from some of the best engineers in the industry, and contribute to systems that impact users globally.

---

## 3. Favorite Project — ACL System at Walmart

### Q: Tell me about your favorite project / most technically challenging project.

**Answer:**

One of my favorite projects was the Automated Case Labeling platform I worked on at Walmart Supply Chain.

What made the project especially interesting was that it combined large-scale distributed systems engineering with a very real operational business problem. Distribution centers were relying heavily on manual labor for labeling packages, and Walmart wanted to automate the process while operating under a strict 6-second SLA from scan to label generation.

The challenge was that the required data came from multiple external systems outside our network boundary, and network latency alone was consuming most of the SLA budget. The team had spent a lot of time trying to optimize the existing flow incrementally, but we were still fundamentally constrained by the architecture.

What made this project memorable for me was the moment I stepped back and questioned the core assumption itself — *why are we computing everything at scan time?*

After analyzing the data flow, I realized that most of the label information was actually deterministic hours before the package physically arrived at the distribution center. So instead of optimizing the hot path further, I redesigned the system around pre-generation. We precomputed labels ahead of time based on trailer manifests, and at scan time we only filled a couple of dynamic fields locally in memory.

That architectural shift completely changed the performance profile of the system. We went from several seconds of dependency-heavy processing to sub-50 millisecond local operations.

But honestly, the technical part was only half the challenge. The harder part was building confidence across operations teams and stakeholders that this approach was safe at Walmart scale. We had to design fallback strategies, invalidation logic, and operational safeguards because distribution centers run 24/7 and failures directly impact shipping operations.

The project eventually rolled out across more than 20 distribution centers and saved roughly  million annually in labor costs.

What I enjoyed most about the project was that it reinforced something I still believe strongly today: *sometimes the biggest engineering breakthroughs come not from optimizing harder, but from reframing the problem entirely.*

---

## 4. Conflict Story — Architecture Debate at Walmart

### Q: Tell me about a disagreement with a teammate / a conflict at work.

**Answer:**

One conflict situation that stands out happened during a supply chain modernization effort at Walmart.

Two senior engineers on the team had very strong and opposing opinions around how a critical workflow should be designed. One preferred a synchronous REST-based approach because it was simpler operationally and easier to debug. The other strongly pushed for an event-driven Kafka-based architecture for scalability and resiliency reasons.

The disagreement had started affecting team momentum. Design meetings were becoming repetitive, implementation was stalled, and the discussion was slowly becoming more emotional than technical.

At that point, I realized the team did not actually have a shared decision-making framework. Everyone was defending preferred technologies rather than evaluating against the actual business requirements.

So instead of trying to decide the answer myself, I facilitated a dedicated architecture session focused entirely on tradeoffs.

I asked both engineers to evaluate their approach against a few concrete dimensions:
- failure handling
- operational complexity
- scalability
- debugging
- SLA requirements
- downstream dependencies

What became clear during the discussion was that neither extreme solution was ideal. The core transaction path required synchronous guarantees because of the SLA and operational visibility needs, but several downstream workflows were naturally asynchronous and benefited from event-driven fan-out.

That led us toward a hybrid architecture that combined both approaches rather than forcing a binary decision.

What I learned from that experience is that most technical conflicts are not actually about technology. They are usually about unclear constraints, lack of alignment on priorities, or people feeling unheard.

Since then, I’ve tried to focus less on “winning” technical debates and more on helping teams build shared context and decision clarity.

---

## 5. Ambiguity Story — Building MFT Platform from Scratch

### Q: Tell me about a time you worked in ambiguity / handled unclear requirements.

**Answer:**

One situation where I had to operate through significant ambiguity was when we started building a new Managed File Transfer platform at Railinc.

At the beginning, there was no detailed product specification or clearly defined architecture. Different business units had different expectations, some stakeholders were focused on operational reliability, others wanted modernization and cloud migration, and many existing workflows were tribal knowledge rather than documented behavior.

So the challenge was not just building the platform — it was first figuring out what problem we were actually solving.

The first thing I did was avoid jumping directly into implementation. Instead, I spent time mapping the ecosystem:
- how files moved through the organization
- where operational pain points existed
- which SLAs actually mattered
- which behaviors were business-critical versus historical artifacts

I interviewed multiple teams, analyzed production patterns, and tried to identify the underlying common needs rather than treating every request as unique.

At the same time, I knew we could not wait indefinitely for perfect clarity because the legacy system was becoming operationally risky.

So I intentionally made a series of reversible architectural decisions:
- modular services
- event-driven workflows
- tenant-aware processing
- configuration-driven onboarding

The goal was to create flexibility so the platform could evolve as requirements became clearer.

A few of my assumptions turned out to be correct — for example, multi-tenant onboarding became critical much earlier than stakeholders initially expected.

Other assumptions were wrong. I originally believed near-real-time processing would be essential for most teams, but later discovered reliability and operational visibility mattered much more than raw latency for many workflows.

Because we designed the platform modularly, we were able to adapt without major rewrites.

That experience reinforced an important lesson for me: *when operating in ambiguity, the goal is not to eliminate uncertainty completely. The goal is to make decisions that are informed, adaptable, and reversible while continuously learning from real usage.*

---

## Quick Reference: Which Story Answers Which Question

| Question Type | Use This Story |
|---------------|---------------|
| Favorite / most challenging project | ACL Pre-Generation (Section 3) |
| Innovation / creative solution | ACL Pre-Generation (Section 3) |
| Conflict / disagreement | REST vs Kafka Debate (Section 4) |
| Influencing without authority | REST vs Kafka Debate (Section 4) |
| Ambiguity / unclear requirements | MFT Platform (Section 5) |
| Working in ambiguity | MFT Platform (Section 5) |
| Architecture ownership | MFT Platform (Section 5) |
| Why Google / why move | Section 2 |
| Leadership under constraints | ACL (Section 3) + MFT (Section 5) |
| Tradeoff thinking | All three stories demonstrate this |

---

*These are polished, conversational-length answers ready for Google L5 behavioral rounds.*
*Last updated: May 2026*
