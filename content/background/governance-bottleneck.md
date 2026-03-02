---
weight: 10
title: The Governance Bottleneck
---
# Why Software Delivery Governance Matters

The modern world runs on mission-critical software. Organizations building this
software face a paradox: they need to move fast to stay competitive, but they
also need rigorous governance to manage risk.

Engineering teams have spent over a decade investing in DevOps and cloud
technologies, automating their way to multiple deployments per day. Meanwhile,
governance processes remain stubbornly manual and slow. A single line of code can
require dozens of manual steps, multiple approvals, and weeks of waiting — all
while providing little actual risk reduction.

## The Governance Bottleneck

While engineering teams have automated the journey to production, governance
processes haven't kept pace. Legacy models relying on manual documentation,
change advisory boards, and human approvals introduce friction and delay that
modern software delivery cannot sustain.

Consider the real cost: one engineer at a major financial institution documented
81 individual steps just to create and approve the paperwork needed to deploy a
single line of code. Three different tickets. Multiple meetings. All of this
happens after the code is written and tested.

This isn't just a productivity problem — it's a risk problem. Manual processes at
scale create opportunities for human error. When you're managing millions of
changes, relying on humans to catch every compliance gap is unrealistic, and
controls meant to reduce risk often increase it.

{{< hint info >}}
### The Strategic Impact

These legacy governance processes have several strategic impacts on the business:

**Speed** — Software can't be released until it has been manually approved. Modern
companies deploy changes continuously, but that speed isn't achievable with
legacy governance processes.

**Cost** — Every change takes hours to be manually verified and the costs mount up.
Large financial institutions spend hundreds of thousands of hours on manual
governance approvals annually.

**Risk** — Human processes can't stop every non-compliant change due to the volume
and speed of modern delivery.

Organizations that automate governance unlock massive gains in velocity AND
massive reductions in cost and risk.
{{< /hint >}}

## Regulators Have Raised Their Expectations

Regulators also recognize the problem. The UK's Financial Conduct Authority
analyzed over 1 million production changes and found that traditional governance
practices correlate with worse outcomes. Their research showed:

- Change Advisory Boards approved over 90% of changes they reviewed, with some
  firms not rejecting a single change all year, making them ineffective as an
  assurance mechanism
- Firms' change management processes are ineffective due to heavy reliance on
  manual review and actions
- Legacy technology and slow release cycles are indicative of high risk changes

The research is clear: heavyweight approval processes don't reduce risk. In fact,
formal change management that requires external approval makes organizations 2.6
times more likely to be low performers, with no corresponding improvement in
change failure rates.[^1]

## What Should Be in a Governance Framework?

An SDLC governance framework should define the risks associated with software
delivery and the controls that mitigate them. Specifically:

- A **risk register** identifying the risks in your software delivery lifecycle
- **Control areas** organized by lifecycle phase (Build, Release, Runtime)
    - For each control area:
      - A definition of the control
      - The risks this control mitigates
      - A rationale for why this control exists
      - Application rule (Mandatory, Optional)

{{< hint info >}}
### How Should the Framework Be Documented?
It should be defined and available on an internal website and stored in a version
controlled system such as git — exactly like this one.
{{< /hint >}}

[^1]: Forsgren PhD, Nicole. Accelerate: The Science of Lean Software and DevOps: Building and Scaling High Performing Technology Organizations. IT Revolution Press.
