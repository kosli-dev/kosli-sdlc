---
title: Drift Detection
summary: "Infrastructure and configuration are continuously monitored for drift from the approved baseline defined as code, detecting unauthorised or unintended changes."
weight: 60
control_code: SDLC-CTRL-0018
level: 1
doc-status: Draft
type: DET
areas:
  - change
nist-sp-800-53r5_references:
  - id: cm-2
    note: Baseline configuration — drift detection identifies deviations from the documented infrastructure baseline.
  - id: cm-3
    note: Configuration change control — detects unauthorised changes that bypass the formal change management process.
  - id: cm-6
    note: Configuration settings — ensures runtime configuration matches the approved settings defined as code.
  - id: si-4
    note: System monitoring — continuous monitoring of infrastructure for unauthorised modifications.
  - id: ca-7
    note: Continuous monitoring — drift detection is a key component of the continuous compliance monitoring strategy.
  - id: si-7
    note: Software and information integrity — detects tampering or unintended modifications to infrastructure and configuration.
soc2-type2_references:
  - id: cc7.2
    note: Requires monitoring for anomalies indicative of security events; drift detection identifies unexpected changes to running environments.
  - id: cc7.3
    note: Requires evaluation of detected anomalies; drift detection alerts enable investigation of whether changes are authorised.
  - id: cc8.1
    note: Requires only authorised changes in production; drift detection identifies when the running state diverges from the approved configuration.
mitigates:
  - configuration_drift
  - insider_threat
  - environment_breach
related_mitigations:
  - SDLC-CTRL-0005
  - SDLC-CTRL-0016
  - SDLC-CTRL-0012
---
# {{% param "title" %}}
{{< area_head >}}

## Description
Even when infrastructure is defined as code and applied through automation, configuration drift can occur through manual interventions, failed deployments, or external changes. Drift detection continuously compares the actual state of infrastructure and configuration against the approved baseline, identifying deviations that may indicate unauthorised access, operational errors, or compliance violations.

Drift detection complements the preventative control of defining infrastructure as code (SDLC-CTRL-0005) by providing a detective layer that identifies when the actual state diverges from the declared state, regardless of how the change occurred.

{{< figure src="/images/infrastructure-drift-detection.png" alt="Infrastructure change and drift detection: the Terraform pipeline attests changes to Kosli while drift detection snapshots the statefile, enabling continuous monitoring of desired versus actual state" >}}

## Requirements
* Production infrastructure MUST be continuously monitored for configuration drift from the approved baseline
* Detected drift MUST generate alerts to the appropriate response channels
* Drift events MUST be recorded with details of what changed, when, and the expected versus actual state
* Drift MUST be remediated by either updating the infrastructure code or reverting the unauthorised change
* Drift detection SHOULD be automated and run at regular intervals

## How we implement this control

* We use Kosli environment monitoring to detect drift in our runtime environments
* Drift alerts are delivered to our Slack channels for immediate review
* Detected drift is investigated and resolved by either updating the infrastructure code or reverting the change

{{< compliance_refs >}}

## Links
- [Kosli — Environment Monitoring](https://docs.kosli.com/getting_started/environments/)
- [Terraform — Detecting Drift](https://developer.hashicorp.com/terraform/tutorials/state/resource-drift)
