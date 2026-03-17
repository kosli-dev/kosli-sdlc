---
title: Quality Assurance
summary: "Functionality of software is assured through systematic testing prior to production deployment."
weight: 20
control_code: SDLC-CTRL-0008
level: 1
doc-status: Draft
type: PREV
areas:
  - process
nist-sp-800-53r5_references:
  - id: sa-11
    note: Developer testing and evaluation — requires testing and evaluation of software as part of the development process.
  - id: sa-15
    note: Development process, standards, and tools — mandates defined testing processes and quality standards.
  - id: si-2
    note: Flaw remediation — testing identifies flaws that must be remediated before deployment.
  - id: cm-4
    note: Impact analysis — testing validates that changes do not introduce regressions or unintended side effects.
soc2-type2_references:
  - id: cc8.1
    note: Requires changes to be tested before deployment to production; quality assurance provides the automated and manual verification of software correctness.
  - id: pi1.3
    note: Requires processing to be complete, accurate, and timely; automated tests verify that software behaves as intended before release.
  - id: pi1.5
    note: Requires outputs to be reviewed for completeness and accuracy; quality gates confirm software meets acceptance criteria prior to deployment.
mitigates:
  - vulnerable_software_in_production
  - audit_and_compliance_failure
related_mitigations:
  - SDLC-CTRL-0007
  - SDLC-CTRL-0013
---
# {{% param "title" %}}
{{< area_head >}}

## Description
Every change has the potential to introduce regressions in functionality. Testing and qualifying software prior to deployment manages the risk of production issues. The level of testing and qualification corresponds to the risk appetite for a particular system.

Testing can be either manual or automated, however automated approaches such as unit testing provide significant advantages: less manual work, more consistent testing, faster lead times, improved knowledge sharing, and automated test results documentation. Regardless of the approach, testing must be systematic and test results documented.

## Requirements
* All software delivered to customers, or with potential to impact customer data, MUST be tested prior to deployment
* Test results MUST be documented and linked to the artefact under test
* Automated testing SHOULD be preferred over manual testing where feasible
* Test coverage goals SHOULD be defined and enforced via automated ratchets
* Test results MUST be recorded in the compliance audit trail prior to deployment approval

## How we implement this control

For any software delivered to customers, or with potential to impact customer data, we test all software prior to deployment/release. Our main testing method favours automated tests, both on the unit and integration level. (As of this time, our server software has over 95% branch coverage).

* We perform automated testing as part of our CI/CD pipelines
* We record the automated test results against the code and artefacts in our [Kosli Flows](https://app.kosli.com/kosli/flows/)
* We control that tests are passing and test results are stored prior to deployment

In addition, we perform these controls which are optional but good practice:

* We have a test coverage ratchet that fails if a coverage goal is not met
* This ratchet fails the pipeline
* A manual intervention is required to lower the coverage goal

{{< compliance_refs >}}

## Links
- [OWASP Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
- [Kosli — Attestations](https://docs.kosli.com/getting_started/attestations/)
