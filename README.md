# 🚀 Docker Build & Push Action

Build and push multi-architecture Docker images with ease.

## Features

- Multi-arch builds (amd64 + arm64)
- Build cache (GitHub Actions cache)
- Auto versioning from Git tags

## Example Usage

GitHub workflow in a repo:

```yaml
- name: Build Docker image
  uses: subztep/dockerhub-action@v1
  with:
    dockerhub_username: ${{ vars.DOCKERHUB_USERNAME }}
    dockerhub_token: ${{ secrets.DOCKERHUB_TOKEN }}
    dockerhub_repository: subztep/jai
    version: 1.0.0
```

## Versioning

- Push to main → :latest
- Push a git tag → :1.0.0 + :latest

Example:

```sh
git tag v1.0.0
git push origin v1.0.0
```

## Inputs

| Name                 | Description                   | Default                   |
| -------------------- | ----------------------------- | ------------------------- |
| dockerhub_username   | Docker Hub username           | required                  |
| dockerhub_token      | generated token on Docker Hub | required                  |
| dockerhub_repository | Image name _[user/repo]_      | required                  |
| version              | Image tag                     | `latest`                  |
| push_latest          | Also push `:latest`           | `true`                    |
| platforms            | Target platforms              | `linux/amd64,linux/arm64` |
| docker_context       | Build context                 | `.`                       |
| dockerfile           | Dockerfile path               | `Dockerfile`              |
| build_args           | Docker build arguments        | `""`                      |
| checkout_ref         | Git ref to checkout           | `""`                      |
| sbom                 | Attach an SBOM attestation    | `true`                    |
| provenance           | Provenance attestation _[false, mode=min, mode=max]_ | `mode=max` |
| cache_scope          | GHA cache scope; set a unique value per image when building several images from one repo | `dockerhub_repository` |


## Multi-arch support

Images are built for:
- linux/amd64
- linux/arm64
  
Works on:
- Apple Silicon 🍎
- Linux servers 🐧
- Cloud platforms ☁️

## Notes

- Uses Docker Buildx under the hood
- Cache is automatically reused across builds
- No need to manually manage platforms
