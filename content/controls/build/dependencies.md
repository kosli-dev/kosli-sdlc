---
title: Dependency Management
summary: "Every dependency is defined securely, managed, and auditable as part of the software development lifecycle."
weight: 40
control_code: SDLC-CTRL-0004
level: 1
doc-status: Draft
type: PREV
areas:
  - build
nist-sp-800-53r5_references:
  - id: sa-9
    note: External system services — third-party dependencies are external services/components that must be managed and controlled.
  - id: sa-12
    note: Supply chain protection — dependency management controls the inputs to the build process.
  - id: sa-22
    note: Unsupported system components — dependencies must be actively maintained and not end-of-life.
  - id: cm-8
    note: System component inventory — all dependencies must be catalogued and traceable.
  - id: sr-4
    note: Provenance — requires tracking the origin and integrity of software components.
  - id: cm-7
    note: Least functionality — only necessary dependencies should be included.
soc2-type2_references:
  - id: cc8.1
    note: Requires changes to be authorised and tested; dependency management ensures third-party components are explicitly declared and reviewed.
  - id: pi1.3
    note: Requires processing integrity; pinned and verified dependencies prevent unexpected behaviour from upstream changes.
  - id: cc7.2
    note: Requires monitoring of system components; maps to tracking dependency versions and known vulnerabilities.
mitigates:
  - supply_chain_compromise
  - vulnerable_software_in_production
related_mitigations:
  - SDLC-CTRL-0002
  - SDLC-CTRL-0021
---
# {{% param "title" %}}
{{< area_head >}}

## Description
Inputs to the build process — including third-party libraries, container base images, and other source code — can introduce security and quality issues. Dependencies must be explicitly defined, controlled, and transparent to maintain the integrity of the software supply chain.

During build, these inputs can be recorded as the software bill of materials alongside binary provenance, enabling traceability of all components included in a release.

## Requirements
* All dependencies MUST be explicitly defined in version-controlled dependency files (e.g. `go.mod`, `requirements.txt`, `package.json`, `Dockerfile`)
* Dependencies MUST comply with licensing requirements agreed by {{% param "company" %}}
* Lock files MUST be used to ensure reproducible builds and prevent silent dependency changes
* Dependencies SHOULD be recorded as a software bill of materials when recording [binary provenance]({{< relref "/controls/build/binary_provenance" >}})
* Container base images MUST be explicitly versioned and pinned

## How we implement this control

We define these dependencies in the source code, at the application level and if relevant, at the Docker image level.

| Application | Dependencies |
| ----------- | ------------ |
| CLI | [Golang Dependencies](https://github.com/kosli-dev/cli/blob/main/go.mod) |
| Server | [Python Dependencies](https://github.com/kosli-dev/server/blob/master/src/requirements.txt) <br/> [Docker Dependencies](https://github.com/kosli-dev/server/blob/master/Dockerfile) <br /> [NPM Dependencies](https://github.com/kosli-dev/server/blob/master/package.json) |
| Slack Application | [Python Dependencies](https://github.com/kosli-dev/slack-auth-app/blob/main/src/requirements.txt) <br/> [Docker Dependencies](https://github.com/kosli-dev/slack-auth-app/blob/main/Dockerfile) |

{{< figure src="/images/dependency-management.svg" alt="Dependency Management" >}}

{{< compliance_refs >}}

## Links
- [OWASP Dependency-Check](https://owasp.org/www-project-dependency-check/)
- [CycloneDX SBOM Standard](https://cyclonedx.org/)
- [SPDX SBOM Standard](https://spdx.dev/)
