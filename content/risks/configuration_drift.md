---
title: "Configuration Drift"
weight: 80
risk_id: SDLC-RISK-0008
risk_key: configuration_drift
description: "Infrastructure or application configuration diverges from its known, approved state, causing undetected changes in security posture or behaviour."
mitigations:
  - name: "Infrastructure and Config Management"
    url: "/controls/build/infrastructure_and_config_management/"
  - name: "Version Control"
    url: "/controls/build/versioncontrol/"
  - name: "Deployment Controls"
    url: "/controls/runtime/deployment_controls/"
  - name: "Change Records"
    url: "/controls/runtime/change_records/"
---

# {{% param "title" %}}
{{< risk_head >}}


## Description
Configuration Drift occurs when the actual state of infrastructure, application configuration, or deployment environments diverges from the known, approved, and version-controlled state. This divergence can result from manual changes applied directly to production systems, emergency fixes that are never reconciled with the source of truth, inconsistent configuration management practices, or failures in infrastructure-as-code pipelines. Configuration drift is particularly insidious because changes accumulate silently over time, creating a growing gap between what the organisation believes is running and what is actually deployed. This gap undermines security controls, complicates incident response, and erodes confidence in the environment's integrity.

- **Manual production changes** - Ad hoc modifications applied directly to production infrastructure or application configuration outside the standard change management process
- **Unreconstructed emergency fixes** - Hotfixes or emergency changes applied during incidents that are never backported to the source of truth in version control
- **Infrastructure-as-code divergence** - Drift between declared infrastructure definitions and the actual state of cloud resources, network configurations, or security groups
- **Environment inconsistency** - Development, staging, and production environments falling out of alignment, leading to untested configuration combinations reaching production
- **Untracked configuration drift** - Changes to feature flags, runtime parameters, database schemas, or third-party integrations that are not captured in version control or change records

## Consequences
The consequences of configuration drift materializing for a financial institution can be severe:

- **Silent Security Degradation:** Drifted configurations can inadvertently weaken security controls—opening firewall rules, disabling encryption, relaxing authentication policies, or exposing services to unauthorised networks—without any alert or record.

- **Unpredictable System Behaviour:** Applications running with configuration that differs from the tested and approved state may exhibit unexpected behaviour, data processing errors, or transaction failures that are difficult to diagnose.

- **Failed Disaster Recovery:** Recovery procedures based on version-controlled configuration will restore systems to a state that differs from what was actually running, potentially causing data loss, service failures, or incomplete recovery.

- **Regulatory Non-Compliance:** Regulators expect that organisations can demonstrate the current state of their systems and that changes are controlled and auditable. Configuration drift directly undermines this expectation and can trigger findings in regulatory examinations.

- **Complicated Incident Response:** When the actual state of systems is unknown or differs from documentation, incident responders cannot reliably assess the scope of a compromise or determine whether specific controls were in place at the time of an incident.

- **Increased Operational Risk:** Teams making changes based on stale documentation or incorrect assumptions about the current environment are more likely to cause outages, introduce conflicts, or break dependent services.

- **Erosion of Trust in Automation:** When manual changes routinely override automated configuration management, teams lose confidence in infrastructure-as-code processes, leading to a cycle of increasing manual intervention and further drift.
