---
title: System Access Controls
weight: 40
control_code: SDLC-CTRL-0015
level: 1
doc-status: Draft
type: PREV
areas:
  - change
nist-sp-800-53r5_references:
  - id: ac-2
    note: Account management — governs provisioning, review, and revocation of access to production systems.
  - id: ac-3
    note: Access enforcement — requires consistent enforcement of access controls on all production environments.
  - id: ac-6
    note: Least privilege — access to runtime environments must be limited to the minimum necessary for the task.
  - id: ac-17
    note: Remote access — remote access to production systems must be controlled, monitored, and encrypted.
  - id: au-3
    note: Content of audit records — all access activities must be logged with sufficient detail for forensic analysis.
  - id: au-12
    note: Audit record generation — the system must generate audit records for all access to production environments.
  - id: ia-2
    note: Identification and authentication — all users must be uniquely identified and authenticated before accessing production systems.
mitigates:
  - unauthorised_system_access
  - insider_threat
  - environment_breach
related_mitigations:
  - SDLC-CTRL-0014
  - SDLC-CTRL-0016
---
# {{% param "title" %}}
{{< area_head >}}

## Summary
All access to runtime environments requires authentication via SSO and generates full audit trails for review.

## Description
As part of normal software development, it can be necessary to gain remote access to runtime environments for debugging, running migration scripts, or inspecting the behaviour of running systems. This access must be limited to authorised personnel, and all activities performed must have full audit trails.

Access controls ensure that only authenticated, authorised individuals can interact with production systems, and that every session is logged for forensic analysis and compliance reporting.

## Requirements
* All access to production environments MUST require authentication via single sign-on (SSO) or equivalent identity provider
* All access sessions MUST generate audit trails recording who accessed what, when, and what actions were performed
* Access MUST be limited to authorised personnel on a least-privilege basis
* Access audit trails MUST be reviewed regularly
* Remote access to production systems MUST be encrypted

## How we implement this control

* Any remote shell session requires SSO authentication and full audit trails are logged in Kosli here: https://app.kosli.com/kosli/audit-trails
* This forms part of our [System Access Control Policy](https://app.drata.com/policy-builder/18)
* All access audit trails are reviewed

## Links
- [NIST SP 800-53r5 AC-17: Remote Access](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-53r5.pdf)
- [OWASP Access Control Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Access_Control_Cheat_Sheet.html)
