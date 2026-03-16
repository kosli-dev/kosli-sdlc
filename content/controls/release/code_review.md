---
title: Code Review
summary: "Code review is performed on all software changes prior to production deployment, providing peer verification of security, quality, and correctness."
weight: 10
control_code: SDLC-CTRL-0007
level: 1
doc-status: Draft
type: PREV
areas:
  - process
nist-sp-800-53r5_references:
  - id: sa-11
    note: Developer testing and evaluation — code review is a form of peer evaluation applied to all changes before they reach production.
  - id: sa-15
    note: Development process, standards, and tools — mandates peer review as part of the development process.
  - id: cm-3
    note: Configuration change control — requires changes to be reviewed and approved before implementation.
  - id: si-7
    note: Software and information integrity — peer review helps detect malicious or erroneous changes to code.
  - id: ac-5
    note: Separation of duties — the reviewer must be a different person from the author of the change.
soc2-type2_references:
  - id: cc8.1
    note: Requires changes to be authorised before implementation; code review provides the peer approval mechanism for all source code changes.
  - id: cc2.1
    note: Requires relevant quality information to be communicated; code review is the primary mechanism for knowledge sharing and defect identification during development.
mitigates:
  - insider_threat
  - vulnerable_software_in_production
related_mitigations:
  - SDLC-CTRL-0001
  - SDLC-CTRL-0010
  - SDLC-CTRL-0008
---
# {{% param "title" %}}
{{< area_head >}}

## Description
Peer review is an essential mitigation against insider threats, as well as a means of improving knowledge sharing and software quality. At a minimum, code reviews are performed by someone capable of understanding the change and its associated risks.

Pull requests document the review process, including the rationale for the change and any relevant context. Reviewers consider security concerns, code quality and maintainability, and whether manual testing is required.

{{< figure src="/images/feature-branch-pr.svg" alt="Feature Branch Strategy" >}}

{{< hint warning >}}
### Code Review Anti-patterns

A common anti-pattern when using pull requests is waiting for review. In an ideal situation, the lead time for review should approach zero. If there is any delay on integration, it can lead to people batching larger and larger changes — causing larger pull requests, more delays, poorer code reviews, and ultimately more risks.

To avoid this, we recommend pair- or ensemble-programming: a practice where more than one person works together to complete tasks. This way, as soon as one developer creates the pull request, another person can sign off immediately.

Note: the reviewer should not be the person who pushes the last commit on the branch.
{{< /hint >}}

## Requirements
* All code changes MUST be reviewed by at least one peer before merging to a protected branch
* The reviewer MUST NOT be the author of the change
* Reviews MUST consider security implications, code quality, and verification requirements
* Code review evidence MUST be recorded and linked to the artefact for audit purposes
* Protected branches MUST require approved pull requests before merge

## How we implement this control

* We prefer real time reviews with pair or ensemble programming
* We use pull requests to document reviews in GitHub
* We protect the `main` branch in each repository
* We record the pull requests in Kosli and control/monitor that no runtime workload is missing PR attestations

{{< compliance_refs >}}

## Links
- [About pull request reviews — GitHub](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/about-pull-request-reviews)
- [About protected branches — GitHub](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches)
