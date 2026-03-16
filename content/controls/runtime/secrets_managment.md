---
title: Secrets Management
weight: 30
control_code: SDLC-CTRL-0014
level: 1
doc-status: Draft
type: PREV
areas:
  - change
nist-sp-800-53r5_references:
  - id: ia-5
    note: Authenticator management — covers the lifecycle of credentials including creation, distribution, storage, rotation, and revocation.
  - id: sc-12
    note: Cryptographic key establishment and management — requires secure generation, distribution, storage, and destruction of cryptographic keys.
  - id: sc-28
    note: Protection of information at rest — secrets must be encrypted at rest in the secrets management system.
  - id: ac-3
    note: Access enforcement — access to secrets must be restricted based on role and environment.
  - id: au-12
    note: Audit record generation — secret access and rotation events must be logged.
mitigates:
  - credential_and_secret_exposure
  - insider_threat
  - environment_breach
related_mitigations:
  - SDLC-CTRL-0006
  - SDLC-CTRL-0015
---
# {{% param "title" %}}
{{< area_head >}}

## Summary
Build and runtime secrets are stored securely in dedicated secrets management systems, with documented ownership, rotation schedules, and access controls.

## Description
Secrets — such as API keys, cryptographic keys, and identity tokens — must be stored securely and documented in a central place. [Cryptographic failures are the second highest risk in the OWASP top ten](https://owasp.org/Top10/A02_2021-Cryptographic_Failures/), so rigour and process is essential.

Effective secrets management requires secure storage, strict access controls, regular rotation with expiry monitoring, and clear documentation of each secret's purpose, ownership, and update procedures. Secrets must be scoped per environment and injected at runtime rather than stored in source code.

{{< figure src="/images/secrets-management.svg" alt="Secrets Management" >}}

## Requirements
* All secrets MUST be stored in a dedicated secrets management system, not in source code or configuration files
* Secrets MUST be scoped per environment (dev, test, prod)
* Secrets MUST be rotated periodically with documented rotation schedules
* Expiring secrets MUST trigger automated alerts before expiry
* Access to secrets MUST be restricted based on role and environment
* Secret access and rotation events MUST be logged for audit purposes
* New secrets MUST be documented with ownership, purpose, and update procedures

## How we implement this control

### Infrastructure secrets

- We use AWS Secrets Manager to store infrastructure secrets.
- Infrastructure secrets are handled with a separate [terraform-server repository](https://github.com/kosli-dev/terraform-server) together with other server information.
- The update, creation and deletion of secrets is described in [secrets/README.md](https://github.com/kosli-dev/terraform-server/blob/master/secrets/README.md).
- We use a set of helper programs to update the secrets for the different servers. In addition to updating the secrets, the helper program also:
  - Tracks which server the secret was updated for.
  - When and by whom the secret was updated.
  - When does the secret expire.
- We have a daily [GitHub job](https://github.com/kosli-dev/terraform-server/actions/workflows/secret-expire-check.yml) that checks if any secret will expire within the next month.
- If a secret is going to expire soon a message is sent to our dedicated [Slack channel](https://kosli-internal.slack.com/archives/C07P4AUQGHH).
- Every 3 months we check if any new infrastructure secrets have been added. In the [server repository](https://github.com/kosli-dev/server) there is a `bin/check_new_secrets.sh` script that will do the check and tell you if any secrets have been added.
- The evidence that we ran the check for new secrets is recorded in the [secrets-updated](https://app.kosli.com/kosli/flows/secrets-updated/trails/) flow.
- We have a daily [GitHub job](https://github.com/kosli-dev/server/actions/workflows/check-new-secrets.yml) that checks if it is more than three months since last time we checked for new secrets.

### CI workflow secrets

- We use GitHub Action secrets to store CI workflow secrets.
- CI workflow secrets are either **repository secrets** or **organisation secrets**.
- Organisation and repository secrets are tracked in the [secrets repository](https://github.com/kosli-dev/secrets).
- The secrets repository contains a README.md file with general information and one file per secret. Each file gives detailed information about how to get a new secret and how to update them. It also contains:
  - When and by whom the secret was updated.
  - When does the secret expire.
- The secrets repository has a daily GitHub job that checks if:
  - any secret will expire within the next month
  - any new secrets have been added
- If a secret is going to expire soon a message is sent to our dedicated [Slack channel](https://kosli-internal.slack.com/archives/C07P4AUQGHH).

## Links
- [OWASP Secrets Management Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Secrets_Management_Cheat_Sheet.html)
- [OWASP Top 10 — A02:2021 Cryptographic Failures](https://owasp.org/Top10/A02_2021-Cryptographic_Failures/)
- [AWS Secrets Manager](https://aws.amazon.com/secrets-manager/)
