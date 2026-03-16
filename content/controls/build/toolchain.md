---
title: Controlled Build Environment
summary: "Build environments are defined as code, ephemeral, and auditable, providing resilience against supply chain attacks."
weight: 30
control_code: SDLC-CTRL-0003
level: 3
doc-status: Draft
type: PREV
areas:
  - build
nist-sp-800-53r5_references:
  - id: sa-10
    note: Requires the development environment to be configured and controlled.
  - id: sa-11
    note: Developer testing and evaluation — controlled build environments ensure consistent and reproducible test conditions.
  - id: sa-15
    note: Development process, standards, and tools — mandates use of controlled development tools and environments.
  - id: cm-2
    note: Baseline configuration — ephemeral build environments defined as code establish a known baseline for every build.
  - id: cm-6
    note: Configuration settings — build environment configuration must be defined as code and version-controlled.
  - id: si-7
    note: Software and information integrity — immutable build containers prevent tampering during the build process.
soc2-type2_references:
  - id: cc8.1
    note: Requires controlled change management infrastructure; a controlled build environment ensures reproducible, auditable builds.
  - id: cc6.1
    note: Requires logical access controls; maps to restricting who can modify build pipelines and CI/CD configuration.
  - id: cc7.1
    note: Requires detection of anomalous activity; controlled build environments limit the blast radius of compromised components.
mitigates:
  - supply_chain_compromise
related_mitigations:
  - SDLC-CTRL-0002
  - SDLC-CTRL-0001
---
# {{% param "title" %}}
{{< area_head >}}

## Description
Builds that are scripted and executed in ephemeral, controlled build environments are more resilient against software supply chain attacks. Defining build environments as code protects against interference that can occur during the build and distribution processes.

Using immutable container images to define the build environment enables auditing of the build toolchain, as well as security scanning and version control of the environment itself. Ephemeral environments ensure that no persistent state from previous builds can influence subsequent builds.

## Requirements
* Build environments MUST be defined as code and stored in version control
* Build steps MUST be scripted and reproducible
* Build environments SHOULD be ephemeral — created fresh for each build and destroyed afterwards
* Build environment definitions SHOULD use immutable container images where possible
* Build artefact fingerprints MUST be recorded for traceability

## How we implement this control

* Our official builds occur in GitHub pipelines defined as code
* Each step runs in an immutable container
* Each build fingerprint is stored using [Binary Provenance]({{< ref "binary_provenance.md" >}})

{{< figure src="/images/defined-toolchain.svg" alt="Toolchain" >}}

{{< hint info >}}
You can learn more about build security levels defined in the [SLSA specification](https://slsa.dev/spec/v0.1/requirements#scripted-build).
{{< /hint >}}

{{< compliance_refs >}}

## Links
- [SLSA Build Requirements](https://slsa.dev/spec/v0.1/requirements#scripted-build)
- [GitHub Actions — Using containers](https://docs.github.com/en/actions/using-jobs/running-jobs-in-a-container)
