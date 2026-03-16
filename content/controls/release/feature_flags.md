---
title: Feature Flags
summary: "Feature flags provide controlled, gradual exposure of new functionality in production, enabling safe releases and rapid rollback without redeployment."
weight: 55
control_code: SDLC-CTRL-0023
level: 1
doc-status: Draft
type: PREV
areas:
  - change
nist-sp-800-53r5_references:
  - id: cm-3
    note: Configuration change control — feature flags allow changes to be released incrementally and rolled back without deploying new code.
  - id: cm-4
    note: Impact analysis — feature flags enable controlled exposure to subsets of users, allowing impact assessment before full rollout.
  - id: si-7
    note: Software and information integrity — feature flags decouple deployment from release, ensuring code is deployed once and toggled safely.
  - id: sa-11
    note: Developer testing and evaluation — feature flags support A/B testing and canary releases as part of ongoing validation in production.
  - id: cp-10
    note: System recovery — feature flags provide an immediate rollback mechanism without requiring redeployment.
soc2-type2_references:
  - id: cc8.1
    note: Requires controlled change management; feature flags provide a mechanism to release and roll back functionality without new deployments.
  - id: cc7.2
    note: Requires monitoring for anomalies; feature flags enable incremental rollout with monitoring at each stage, limiting blast radius.
  - id: cc3.4
    note: Requires evaluation of changes for risk; feature flags allow gradual exposure to assess risk before full release.
mitigates:
  - vulnerable_software_in_production
  - unauthorised_deployment
related_mitigations:
  - SDLC-CTRL-0010
  - SDLC-CTRL-0013
  - SDLC-CTRL-0016
---
# {{% param "title" %}}
{{< area_head >}}

## Description
Feature flags (also known as feature toggles) decouple deployment from release by allowing new functionality to be toggled on or off in production without deploying new code. This provides a critical safety mechanism: code can be deployed in a disabled state, gradually rolled out to subsets of users, and instantly rolled back if issues are detected.

In a regulated software development lifecycle, feature flags serve as a preventative control by ensuring that new functionality can be released incrementally and with oversight. They reduce the risk associated with big-bang releases and provide a rapid remediation path that does not require emergency deployments or hotfixes.

Feature flags also support progressive delivery patterns such as canary releases, percentage-based rollouts, and user-targeted releases, all of which reduce the blast radius of a defective or vulnerable change.

## Requirements
* Feature flag changes MUST be auditable, with a record of who changed a flag, when, and why
* Feature flags MUST support instant rollback — disabling a flag should take effect immediately without redeployment
* Access to modify feature flags in production MUST be restricted to authorised personnel
* Long-lived feature flags SHOULD be reviewed periodically and retired when the feature is fully released
* Feature flag state SHOULD be monitored, with alerts for unexpected flag changes in production
* Feature flags SHOULD support gradual rollout patterns (percentage-based, user-targeted, or environment-based)

## How we implement this control

We use [LaunchDarkly](https://launchdarkly.com/) as our feature flag management platform.

* **Audit trail** — LaunchDarkly maintains a full audit log of all flag changes including who made the change, what changed, and when.
* **Access control** — Flag modification permissions are managed through LaunchDarkly's role-based access control, integrated with our SSO provider.
* **Gradual rollout** — We use LaunchDarkly's targeting rules and percentage rollouts to control exposure of new features before full release.
* **Instant rollback** — Disabling a flag in LaunchDarkly takes effect immediately across all connected services without redeployment.
* **Flag lifecycle** — We periodically review active flags and retire those associated with fully released features to reduce technical debt.

{{< compliance_refs >}}

## Links
- [LaunchDarkly — Feature Flag Best Practices](https://launchdarkly.com/blog/feature-flag-best-practices/)
- [LaunchDarkly — Audit Log](https://docs.launchdarkly.com/home/members/audit-log)
- [NIST SP 800-53r5 CM-3: Configuration Change Control](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-53r5.pdf)
