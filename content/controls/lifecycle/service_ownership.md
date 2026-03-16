---
title: Service Ownership
weight: 50
control_code: SDLC-CTRL-0011
level: 1
doc-status: Draft
type: DET
areas:
  - lifecycle
nist-sp-800-53r5_references:
  - id: pm-10
    note: Authorisation process — requires clear identification of who is responsible for each system.
  - id: cm-8
    note: System component inventory — service ownership provides a registry of live services and their responsible owners.
  - id: ir-4
    note: Incident handling — clear ownership enables rapid incident response by identifying the responsible team.
  - id: pl-2
    note: Security and privacy plans — ownership assignment ensures accountability for each service's security posture.
mitigates:
  - audit_and_compliance_failure
  - environment_breach
related_mitigations:
  - SDLC-CTRL-0016
  - SDLC-CTRL-0012
---
# {{% param "title" %}}
{{< area_head >}}

## Summary
All services running in production environments have registered ownership, ensuring clear accountability for maintenance, support, and security.

## Description
In any governance system, risks are managed by controls, but humans are ultimately responsible. In diverse software landscapes, a register of service ownership is essential for multiple reasons:

* **Knowledge** — who understands how this service works, and how can I get help?
* **Incident response** — alerts are firing for a service, who do I contact? What has changed lately?
* **Audit** — who is responsible for ensuring the SDLC is followed for this service?

Service ownership maps live systems to the teams and individuals accountable for them, including links to source code repositories, documentation, and operational metadata.

## Requirements
* Every service running in production MUST have a registered owner
* Ownership records MUST include the responsible team or individual, source code location, and operational metadata
* Ownership information MUST be kept up-to-date and reviewed periodically
* Ownership records SHOULD be accessible from a single location

## How we implement this control

At this stage, as we have a relatively simple system and a single tech team, simply recording the services in [Kosli's environment monitoring]({{< ref "workload_monitoring.md" >}}) meets this need.

{{< figure src="/images/secrets-management.svg" alt="Service Ownership" >}}

## Links
- [Kosli — Environments](https://docs.kosli.com/getting_started/environments/)
