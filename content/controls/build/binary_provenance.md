---
title: Artifact Binary Provenance
summary: "Every software artefact running in a production system has known provenance, established through cryptographic content-addressable identities."
weight: 20
control_code: SDLC-CTRL-0002
level: 1
doc-status: Draft
type: DET
areas:
  - build
nist-sp-800-53r5_references:
  - id: sa-10
    note: Requires tracking of configuration items including built software artefacts.
  - id: cm-8
    note: System component inventory — binary provenance provides a verifiable record of every artefact deployed.
  - id: si-7
    note: Software, firmware, and information integrity — cryptographic hashes detect unauthorised modification of artefacts.
  - id: sa-12
    note: Supply chain protection — provenance links artefacts to their source, mitigating substitution attacks.
  - id: au-10
    note: Non-repudiation — content-addressable identities provide tamper-evident proof of what was built and deployed.
  - id: cm-3
    note: Change tracking — provenance records tie each artefact to the specific commit and build that produced it.
soc2-type2_references:
  - id: pi1.3
    note: Requires processing to be complete, accurate, and timely; binary provenance verifies that deployed artifacts match what was built and tested.
  - id: cc8.1
    note: Requires authorised and tested changes; provenance attestations confirm that artifacts originate from the controlled build pipeline.
  - id: cc7.2
    note: Requires monitoring for anomalies; provenance verification detects tampered or substituted artifacts before deployment.
mitigates:
  - supply_chain_compromise
  - unauthorised_deployment
related_mitigations:
  - SDLC-CTRL-0001
  - SDLC-CTRL-0003
  - SDLC-CTRL-0013
---
# {{% param "title" %}}
{{< area_head >}}

## Description
Software identity is defined using the cryptographic hash of the software itself. Using the SHA256 digest of a software binary means that if a single byte in the software changes, it will have a different identity. This ensures that one software artefact cannot be qualified and a different one deployed in its place.

Binary provenance creates a provable chain of custody from commit to build to production. It establishes verifiable evidence of what was built, when, and from which source — enabling traceability across the entire software development lifecycle.

Human-friendly identifiers such as semantic versions or git commit references are useful for navigation but are fallible. Cryptographic hashes provide the tamper-proof identity required for security and compliance purposes.

## Requirements
* Every software artefact MUST be identified by its cryptographic hash (SHA256 digest)
* The provenance record MUST link the artefact to the specific git commit that produced it
* The following evidence MUST be recorded for each artefact:
  * The SHA256 of the artefact (docker image, zip file, etc.)
  * A human-readable name
  * The git commit that produced it
  * The git repository state (clean, unstaged files, etc.)
  * A URL to the build log
  * The build environment information
* A software bill of materials SHOULD be recorded alongside provenance data
* Human-friendly identifiers (semver, tags) SHOULD NOT be used as the sole means of identifying software for security and compliance purposes

## How we implement this control

We use Kosli to record every official build in our CI system. The audit trails for our binary provenance can be found here: https://app.kosli.com/kosli/flows/

{{< figure src="/images/binary-provenance.svg" alt="Binary Provenance" >}}

{{< compliance_refs >}}

## Links
- [SLSA Provenance](https://slsa.dev/provenance)
- [Kosli — Artifact Provenance](https://docs.kosli.com/getting_started/artifacts/)
- [Content-addressable storage — Wikipedia](https://en.wikipedia.org/wiki/Content-addressable_storage)
