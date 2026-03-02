---
weight: 30
title: Controls Engineering
---

# Controls Engineering

Controls Engineering is the application of modern software engineering practices
to the domain of governance, risk, and compliance. Think of it as asking: "What
would happen if we applied software engineering to compliance and risk
management?"

This is analogous to how Google created Site Reliability Engineering (SRE) by
asking what would happen if software engineers did operations work. Controls
Engineering asks the equivalent question for governance.

## The Speed Mismatch Problem

Modern software engineering moves fast — teams deploy multiple times per day.
Governance moves slowly — frameworks are reviewed annually, policies go through
committees.

This speed mismatch creates friction. The traditional response is to slow
engineering down, but this approach fails both business needs and risk management
goals.

Controls Engineering offers a different path. By applying modern software
engineering practices to governance itself, organizations can achieve continuous
compliance without sacrificing velocity. This approach replaces manual
checkpoints with automated controls, transforms governance from costly theatre to
a competitive advantage, and proves compliance through verifiable evidence rather
than paperwork and promises.

## Controls Engineering is Not "Automating the Tickets"

There is a natural response when engineering teams encounter the governance
bottleneck: automate the paperwork. If filling out change tickets is slow, write
a script that fills them out. If uploading evidence to a change management system
is tedious, build an integration that does it automatically.

This approach feels like progress. It is faster. But it does not fundamentally
change the outcome. You are still doing the same process, with the same
assumptions, producing the same artifacts. You've just automated the receipts.

The problem is deeper than that. If your existing manual process doesn't actually
improve your risk posture, and in many organizations it doesn't, then automating
that process means you are now doing a risky thing more often. You have increased
your throughput without improving your controls.

Controls Engineering takes a different path. Instead of asking "how do we
automate this process?", it asks "what risk is this process trying to mitigate,
and what is the best way to mitigate that risk?" Sometimes the answer involves
automating part of the existing process. Often it means redesigning the control
entirely.

## What Do We Mean by Control?

A **control** is a check or restraint on an activity to meet one or more software
risk objectives.

Controls should only exist to tackle a given risk. If there is no risk to
mitigate or eliminate, then the control has no purpose. There is a good reason
for this: every control comes with a cost — typically delays and maintenance
overheads. If those costs don't protect against a high-value risk, then why pay
the cost?

When properly designed, controls are guardrails that keep your software delivery
lifecycle on track and aligned with your organization's policies, standards, and
regulatory requirements.

## Designing Automated Controls

At their most abstract level, every control, whether manual or automated, shares
the same fundamental components:

- **Facts**: The raw data or evidence being evaluated
- **Rules**: The criteria used to assess those facts
- **Evaluation**: The process of applying rules to facts
- **Evaluation Report**: Documentation of the decision and its rationale

In an automated control system, we can be more precise:

- **Event**: Something happens (a build completes, a deployment starts, a
  schedule triggers)
- **Context**: Specific contextual information about the event (git commit,
  artifact ID, repository, test results, etc.)
- **Query (Optional)**: The system can proactively gather additional facts it
  needs from a Compliance System of Record (CSOR)
- **Rules**: The same evaluation criteria, but now machine-readable and
  consistently applied
- **Evaluation Report**: Automatically generated documentation with full
  traceability

This structure ensures that automated controls can be both more rigorous and more
efficient than manual ones. Every evaluation is documented, every decision is
traceable, and the criteria are applied consistently across all events.

## Why Software Control Design Matters

When you implement automated controls they exhibit all the characteristics of any
other software system:

- **Controls have requirements.** A control should have clear requirements derived
  from the risk it mitigates. A control consumes inputs and produces outputs.
  These interfaces can be defined and documented.
- **Controls have a lifecycle.** Evaluation logic can be versioned, reviewed, and
  rolled out progressively to different parts of the organization.
- **Controls can be tested.** You can write tests for control logic, verify
  outputs given specific inputs, and regression test controls when you change
  them.
- **Controls have a design.** The policy enforcement points, decision points, and
  systems of record that make up a control can be designed with the same care as
  any software system. Controls can fail. Like any operational system,
  observability is key.

The key takeaway is this: controls aren't obstacles to velocity. When properly
designed, they can be the foundation that makes rapid, confident delivery
possible.

## Types of Software Delivery Controls

While there may be controls sprawled across your SDLC, it can be helpful to
categorize them into specific lifecycle areas based on the risks they are
mitigating. Typically, software controls fall naturally into these categories:

| Area | Scope |
| ----------- | ----------- |
| Build | Controls which apply to the processes around how software is constructed and qualified |
| Release | Controls which apply to release decisions and change control |
| Runtime | Controls which apply to runtime systems and environments |
| Lifecycle | Controls operating outside of the natural software delivery process but must be evidenced, such as ownership, architecture, and security |

