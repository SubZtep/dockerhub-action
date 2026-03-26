# dockerhub-action

Build and Release to Docker Hub

## Setup

Set action parameters in the workflow file or [repository secrets and variables](./settings/secrets/actions).

| Action parameter name | Value / Default              |
| --------------------- | ---------------------------- |
| checkout_ref          | `main`                       |
| dockerhub_username    | _[username]_                 |
| dockerhub_token       | _[generated token]_          |
| dockerhub_repository  | _[user/repo]_                |
| docker_platforms      | `linux/amd64,linux/arm64/v8` |
| docker_context        | `.`                          |
| dockerfile            | `Dockerfile`                 |
| version               | `latest`                     |

---

_TBC._
