---
title: Runtime Workload Monitoring
summary: "Production workloads are continuously monitored to detect and alert on any non-compliant or unauthorised changes in real time."
weight: 50
control_code: SDLC-CTRL-0016
level: 1
doc-status: Draft
type: DET
areas:
  - change
nist-sp-800-53r5_references:
  - id: ca-7
    note: Continuous monitoring — runtime workload monitoring provides real-time compliance assurance across all environments.
  - id: si-4
    note: System monitoring — requires monitoring of production systems for unauthorised changes and anomalous behaviour.
  - id: cm-8
    note: System component inventory — workload monitoring maintains a live inventory of all running components.
  - id: ir-4
    note: Incident handling — non-compliant workload alerts feed directly into incident response processes.
  - id: au-6
    note: Audit record review — forensic history of workload changes supports ongoing analysis and reporting.
soc2-type2_references:
  - id: cc7.2
    note: Requires monitoring of system components for anomalies; workload monitoring detects abnormal resource usage and service degradation.
  - id: cc7.3
    note: Requires evaluation of security events; monitoring and alerting enable timely investigation and response to incidents.
  - id: a1.2
    note: Requires environmental protections and monitoring of infrastructure; workload monitoring provides visibility into service availability and health.
mitigates:
  - unauthorised_deployment
  - supply_chain_compromise
  - configuration_drift
  - environment_breach
related_mitigations:
  - SDLC-CTRL-0013
  - SDLC-CTRL-0012
  - SDLC-CTRL-0018
---
# {{% param "title" %}}
{{< area_head >}}

## Description
Ensuring that risks are controlled in the value stream is the first level of software process compliance. Beyond this, it is important to have a monitoring process in place to ensure that unknown or non-compliant workloads are identified in production.

Runtime workload monitoring provides a forensic history of all changes to production environments, enabling retrospective analysis of what was running at any point in time. Combined with deployment controls, it creates a closed-loop compliance system that both prevents and detects unauthorised changes.

{{< figure src="/images/production-integrity.png" alt="Production integrity: runtime workloads and pipeline events are recorded to Kosli for continuous monitoring of production integrity" >}}

## Requirements
* All production workloads MUST be continuously monitored for compliance status
* Non-compliant or unauthorised workloads MUST generate alerts
* A forensic history of all workload changes MUST be maintained
* Monitoring MUST cover all runtime environments including containers, serverless functions, and storage
* Alert notifications MUST be delivered to the appropriate response channels

## How we implement this control

- A full forensic history of all container runtimes, lambda functions and S3 buckets are recorded using [Kosli environments](https://www.kosli.com/blog/kosli-a-flight-data-recorder-for-your-runtime-environments/) and can be found here: https://app.kosli.com/kosli/environments/
- Unauthorised or non-compliant workloads are recorded and create alerts in our Slack channels

{{< compliance_refs >}}

## Links
- [Kosli — Environment Monitoring](https://docs.kosli.com/getting_started/environments/)
- [Kosli — A Flight Data Recorder for Your Runtime Environments](https://www.kosli.com/blog/kosli-a-flight-data-recorder-for-your-runtime-environments/)
