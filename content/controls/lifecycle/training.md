---
title: Training
summary: "All team members complete annual security awareness training covering the OWASP Top 10, ensuring a security-conscious development workforce."
weight: 30
control_code: SDLC-CTRL-0017
level: 1
doc-status: Draft
type: PREV
areas:
  - lifecycle
nist-sp-800-53r5_references:
  - id: at-2
    note: Literacy training and awareness — requires security awareness training for all personnel.
  - id: at-3
    note: Role-based training — requires training tailored to the individual's role and responsibilities in the SDLC.
  - id: at-4
    note: Training records — requires documentation and retention of training completion.
  - id: pm-13
    note: Security and privacy workforce — requires maintaining a security-aware development workforce.
soc2-type2_references:
  - id: cc1.4
    note: Requires the entity to attract, develop, and retain competent individuals; training ensures personnel have the skills to fulfil their security responsibilities.
  - id: cc2.2
    note: Requires communication of responsibilities to internal personnel; security awareness training ensures staff understand their role in maintaining controls.
mitigates:
  - insider_threat
  - vulnerable_software_in_production
  - credential_and_secret_exposure
related_mitigations:
  - SDLC-CTRL-0007
  - SDLC-CTRL-0006
---
# {{% param "title" %}}
{{< area_head >}}

## Description
Security awareness reduces the likelihood of negligent or accidental insider threats and ensures every team member understands their responsibilities in the software development lifecycle. Training covers the most common security risks and their implications for software development and operations.

New employees and members of the tech team receive this training as part of the onboarding process, and all team members refresh their knowledge at least annually.

## Requirements
* All team members MUST complete security awareness training covering the OWASP Top 10 at least annually
* New employees MUST complete security awareness training as part of onboarding
* Training completion MUST be documented in an audit trail
* Training content SHOULD be reviewed and updated annually to reflect current threats

## How we implement this control

* The team study the [OWASP Top 10 security risks](https://owasp.org/www-project-top-ten/) and discuss their implications for our software development and operations, at least annually.
* The activity and participants are logged in a Kosli audit trail.
* For new employees the OWASP Top 10 is done together with one of the other team members.

{{< compliance_refs >}}

## Links
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [NIST SP 800-53r5 AT-2: Literacy Training and Awareness](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-53r5.pdf)
