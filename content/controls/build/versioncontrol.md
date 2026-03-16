---
title: Version Control
weight: 10
control_code: SDLC-CTRL-0001
level: 1
doc-status: Draft
type: PREV
areas:
  - build
nist-sp-800-53r5_references:
  - id: sa-10
    note: Core control — requires source code and associated documentation to be placed under configuration management.
  - id: cm-2
    note: Version control is the primary mechanism for establishing and maintaining a documented software baseline.
  - id: cm-3
    note: Requires changes to be tracked, reviewed, and approved; version control provides the audit trail of what changed, when, and by whom.
  - id: cm-6
    note: Configuration files such as infrastructure-as-code and application settings must be managed under version control alongside source code.
  - id: cm-9
    note: Requires a formal configuration management plan; use of version control is a core component of that plan.
  - id: si-12
    note: Requires retention of information in accordance with applicable policies; maps to preserving version history for the lifetime of the software.
  - id: au-9
    note: Commit history constitutes an audit trail; this control requires it to be protected from unauthorised modification or deletion.
  - id: ac-2
    note: Governs provisioning, review, and revocation of committer access to the version control system.
  - id: ac-3
    note: Requires access controls to be consistently enforced; maps to branch protection rules and repository permission models.
  - id: ia-5
    note: Covers management of credentials used to authenticate to the version control system, including SSH keys and tokens used for commit signing.
mitigates:
  - insider_threat
  - audit_and_compliance_failure
related_mitigations:
  - SDLC-CTRL-0007
  - SDLC-CTRL-0002
---
# {{% param "title" %}}
{{< area_head >}}

## Summary
Software and configuration are stored in an approved version control system, providing traceability of all changes across all releases.

## Description
Version control is required to maintain a history of all software and configuration changes across all releases. It provides traceability of who made changes and when, establishing the provenance of software over time.

The control establishes verifiable evidence of the state of source code or configuration at the time a release was created. This is important not only for identifying who made changes, but also for understanding what functionality existed at a given point in time — enabling diagnosis of software behaviour weeks, months, or even years after it was originally built, tested, and deployed.

Version control is also integral to ensuring that the software being built and tested is the same software being deployed, by tracking the specific commit or version and providing a reference for traceability.

## Requirements
* Source code MUST be stored in an approved version control system
* The version control system MUST preserve the integrity of history to prevent tampering and maintain the audit trail
* The version control system MUST record the author of each change
* History MUST be maintained for the lifetime of the software or in alignment with applicable retention requirements
* The version control system MUST support access control and SHOULD be configured with branch protection rules
* Deployment branches MUST be protected with required reviews and passing builds before merge
* Merges to protected branches SHOULD create merge or squash commits to enable atomic rollback

## How we implement this control

We use {{< param "vcs" >}} to manage versioning for software development source code. For repository hosting and user management we use {{< param "vcsHost" >}}.

Our git repositories can be found here: https://github.com/kosli-dev

### Branching Strategies

Every service will follow one of the following branching strategies:

1. Feature Branch + Pull Request, or:
2. Production Branches

These are described below.

#### 1. Feature Branch + Pull Request

This branching strategy uses a combination of feature branches with pull requests.

{{< figure src="/images/feature-branch-pr.svg" alt="Feature Branch Strategy" >}}

* Main branch is protected
* Pull requests must be approved before merge to the main branch.
* We use pull requests to enforce and document our code review process. You can read more about it here: [Code Review Process]({{< relref "/controls/release/code_review" >}})
* Pull request merges should create merge or squash commits. (no fast-forward)

Merges to the main should either be merge commits or squash commits... i.e. no fast-forward merges. This allows us to atomically back out merges should we need to.

#### 2. Production Deployment Branch

The Production Deployment branch is an alternative to the feature-branch/pull-request strategy.

This allows a model similar to trunk-based-development, where code reviews are implemented in the merge to production.

* Production branch is protected
* Pull requests must be approved before merge to production.
* We use pull requests to enforce and document our code review process. You can read more about it here: [Code Review Process]({{< relref "/controls/release/code_review" >}})
* Pull request merges will fast-forward. This means the production branch will always "point" to a commit on the main branch

#### Protected Deployment Branches

To ensure compliance to the code review process, we protect the branch we deploy from (main or production) with the following requirements:

* Merges require at least one approval (two if the strategy is Production Deployment Branch)
* Builds and tests run successfully
* No unresolved merge checks

## Links
- [About commit signature verification — GitHub](https://docs.github.com/en/authentication/managing-commit-signature-verification/about-commit-signature-verification)
- [Signing commits — GitHub](https://docs.github.com/en/authentication/managing-commit-signature-verification/signing-commits)
- [About protected branches — GitHub](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches)
