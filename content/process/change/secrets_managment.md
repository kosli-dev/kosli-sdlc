---
title: Secrets Management
level: 1
weight: 30
tldr: Build and runtime secrets are stored securely and documented appropriately
rationale: Leaked secrets such as api keys, cryptography keys, identity tokens
  are a common attack scenario.
areas: 
 - change
---
# {{% param "title" %}}
{{< area_head >}}

## Background

Secrets must be stored in a secure way, and a documented in a central place.
[Cryptographic failures are the second highest risk in the OWASP top ten](https://owasp.org/Top10/A02_2021-Cryptographic_Failures/) 
so rigor and process is essential.

{{< figure src="/images/secrets-management.svg" alt="Change Records" >}}

## How we implement this control

### Infrastructure secrets
* We use AWS secrets manager to store infrastructure secrets.
* Infrastructure secrets are handled with a separate [terraform-server repository](https://github.com/kosli-dev/terraform-server)
together with other server information.
* The update, creation and deletion of secrets is described in [secrets/README.md](https://github.com/kosli-dev/terraform-server/blob/master/secrets/README.md). 
* We use a set of helper programs to update the secrets for the different servers. In addition to updating
the secrets, the helper program also:
   * Tracks which server the secret was updated for.
   * When and by who was the secrete updated.
   * When does the secrete expire.
* We have a daily [GitHub job](https://github.com/kosli-dev/terraform-server/actions/workflows/secret-expire-check.yml)
that checks if any secrete will expire within the next month.
* If a secrete is going to expire soon a message is sent to our dedicated [slack channel](https://kosli-internal.slack.com/archives/C07P4AUQGHH)

### CI workflow secrets
* We use GitHub action secrets to store CI workflow secrets.
* CI workflow secretes are either **repository secretes** or **organization secretes**.
* Repository secretes are tracked in the repository where they are used.
* Organization secretes are tracked in the [server repository](https://github.com/kosli-dev/server).
* In every repository that uses CI workflow secretes there is a `secrets` directory. It contains a
`README.md` file with general information and one file per secret. The file gives detailed information
about how to get a new secret and how to update them. It also contains
   * When and by who was the secrete updated.
   * When does the secrete expire.
* In every repository there is a daily GitHub job that checks if any secrete will expire within the next month.
* If a secrete is going to expire soon a message is sent to our dedicated [slack channel](https://kosli-internal.slack.com/archives/C07P4AUQGHH)
