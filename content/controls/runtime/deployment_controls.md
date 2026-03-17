---
title: Deployment Controls
summary: "Deployment controls are enforced in the pipeline and at runtime to ensure only compliant, approved software is deployed to production."
weight: 20
control_code: SDLC-CTRL-0013
level: 1
doc-status: Draft
type: PREV
areas:
  - change
nist-sp-800-53r5_references:
  - id: cm-3
    note: Configuration change control — deployment controls enforce that only approved changes reach production.
  - id: cm-5
    note: Access restrictions for change — deployment gates restrict which artefacts are permitted in production.
  - id: sa-10
    note: Developer configuration management — ensures that the software built and tested is the same software deployed.
  - id: si-7
    note: Software and information integrity — deployment controls verify artefact integrity before allowing deployment.
  - id: ca-7
    note: Continuous monitoring — runtime compliance monitoring alerts on non-compliant workloads.
soc2-type2_references:
  - id: cc8.1
    note: Requires controlled migration of changes to production; deployment controls enforce that only compliant artifacts are deployed.
  - id: cc6.1
    note: Requires logical access controls; deployment controls restrict who and what can deploy to production environments.
mitigates:
  - unauthorised_deployment
  - supply_chain_compromise
  - vulnerable_software_in_production
related_mitigations:
  - SDLC-CTRL-0010
  - SDLC-CTRL-0002
  - SDLC-CTRL-0016
---
# {{% param "title" %}}
{{< area_head >}}

## Description
Deployment controls automatically ensure that only software which has gone through the complete Software Development Lifecycle reaches production. This can be implemented as a gate in the CI/CD pipeline, as an admission controller in the runtime environment, or ideally both.

Pipeline gates verify that all required attestations (tests, reviews, scans, approvals) are present and passing before allowing deployment. Runtime monitoring provides a second layer of assurance, alerting when non-compliant or unauthorised workloads are detected in production.

{{< figure src="/images/deployment-controls.svg" alt="Deployment Controls" >}}

## Requirements
* Deployment pipelines MUST verify that all required compliance attestations are present and passing before deploying to production
* Artefact identity MUST be verified using cryptographic hashes at the point of deployment
* Non-compliant or unauthorised workloads in production MUST generate alerts
* Deployment controls SHOULD be implemented both as pipeline gates and runtime admission controls

## How we implement this control

* We use [Kosli's assert artifact command](https://docs.kosli.com/client_reference/kosli_assert_artifact/) prior to deployment
* We use [Kosli's environment monitoring]({{< ref "workload_monitoring.md" >}}) to alert on non-compliant workloads

{{< compliance_refs >}}

## Links
- [Kosli — Assert Artifact](https://docs.kosli.com/client_reference/kosli_assert_artifact/)
- [Kosli — Environment Monitoring](https://docs.kosli.com/getting_started/environments/)
