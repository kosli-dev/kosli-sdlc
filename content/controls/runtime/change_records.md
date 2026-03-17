---
title: Change Records
summary: "All systems and services maintain a permanent record of changes, providing a forensic history of all deployments to production."
weight: 10
control_code: SDLC-CTRL-0012
level: 1
doc-status: Draft
type: DET
areas:
  - change
nist-sp-800-53r5_references:
  - id: cm-3
    note: Configuration change control — requires all changes to be recorded, including what changed, when, and by whom.
  - id: au-3
    note: Content of audit records — change records must capture sufficient detail to reconstruct the sequence of events.
  - id: au-6
    note: Audit record review, analysis, and reporting — change records form the basis for ongoing review of deployment activity.
  - id: au-12
    note: Audit record generation — the system must automatically generate change records for all deployments.
  - id: si-12
    note: Information management and retention — change records must be retained in accordance with applicable policies.
soc2-type2_references:
  - id: cc8.1
    note: Requires a record of all changes to production; change records provide the audit trail of what was deployed, when, and by whom.
  - id: cc7.2
    note: Requires monitoring of system components for anomalies; change records enable detection of unauthorised or unexpected deployments.
  - id: cc4.1
    note: Requires monitoring activities to ascertain whether controls are functioning; change records provide evidence for control effectiveness reviews.
mitigates:
  - insider_threat
  - unauthorised_deployment
  - audit_and_compliance_failure
related_mitigations:
  - SDLC-CTRL-0016
  - SDLC-CTRL-0013
  - SDLC-CTRL-0010
---
# {{% param "title" %}}
{{< area_head >}}

## Description
Change records provide the audit trail required to meet change management obligations. By automatically logging all deployments and changes to production systems, the organisation maintains a permanent, tamper-evident record of what was deployed, when, and by whom.

This forensic history supports incident investigation, compliance reporting, and ongoing assurance that only approved software reaches production. Combined with deployment controls, change records enable both proactive gating and retrospective analysis of all changes.

{{< figure src="/images/change-records.svg" alt="Change records" >}}

## Requirements
* All deployments to production systems MUST be automatically recorded
* Change records MUST capture the artefact identity, deployment time, environment, and the actor who triggered the deployment
* Change records MUST be retained permanently or in accordance with applicable retention policies
* Change records MUST be protected from unauthorised modification or deletion
* Change records SHOULD be linked to the corresponding approval and compliance evidence

## How we implement this control

* We monitor production systems and automatically record a forensic history of all changes in Kosli using [environment monitoring](https://docs.kosli.com/getting_started/environments/)
    * Environment records can be found here: https://app.kosli.com/kosli/environments/

{{< compliance_refs >}}

## Links
- [Kosli — Environments](https://docs.kosli.com/getting_started/environments/)
- [NIST SP 800-53r5 CM-3: Configuration Change Control](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-53r5.pdf)
