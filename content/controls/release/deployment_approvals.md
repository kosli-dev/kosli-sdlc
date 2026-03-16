---
title: Deployment Approvals
summary: "All deployments to production are approved by someone other than the person making the change, meeting segregation of duties requirements."
weight: 40
control_code: SDLC-CTRL-0010
level: 1
doc-status: Draft
type: PREV
areas:
  - process
nist-sp-800-53r5_references:
  - id: cm-3
    note: Configuration change control — requires formal approval of changes before deployment to production.
  - id: ac-5
    note: Separation of duties — the person approving deployment must be different from the person making the change.
  - id: cm-5
    note: Access restrictions for change — limits who can authorise and execute deployments to production.
  - id: au-12
    note: Audit record generation — deployment approvals must be recorded as part of the change audit trail.
  - id: ca-7
    note: Continuous monitoring — deployment approval is a gate in the continuous assurance process.
soc2-type2_references:
  - id: cc8.1
    note: Requires changes to be authorised before migration to production; deployment approvals enforce formal sign-off prior to release.
  - id: cc3.4
    note: Requires evaluation of changes for risks; deployment approval gates ensure compliance checks pass before production deployment.
mitigates:
  - insider_threat
  - unauthorised_deployment
related_mitigations:
  - SDLC-CTRL-0007
  - SDLC-CTRL-0013
---
# {{% param "title" %}}
{{< area_head >}}

## Description
Segregation of duties is a common requirement in regulated or high-security development environments. It means that a developer cannot deploy their own changes without approval from someone who both understands what is changing and accepts the risk of the change.

Deployment approval controls form a key role in the secure software development lifecycle. Their purpose is to ensure that risks around change are managed and that change is an active decision. In highly sensitive software systems, more than one approver may be required.

{{< figure src="/images/deployment-approvals.svg" alt="Deployment Approvals" >}}

## Requirements
* All deployments to production MUST be approved by at least one person other than the author of the change
* The approver MUST understand the nature and scope of the change
* Deployment approvals MUST be recorded in an audit trail
* Approval evidence MUST be linked to the specific artefact being deployed
* For highly sensitive systems, more than one approver SHOULD be required

## How we implement this control

* We use git tags to trigger and record deployment approvals
* CI/CD pipelines generate attestations for [Kosli approvals](https://docs.kosli.com/getting_started/approvals/)

{{< compliance_refs >}}

## Links
- [Kosli — Approvals](https://docs.kosli.com/getting_started/approvals/)
- [NIST SP 800-53r5 AC-5: Separation of Duties](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-53r5.pdf)
