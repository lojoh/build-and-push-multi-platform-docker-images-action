# Build and push multi platform docker images

A Github Action used to build multiplatform docker images and push them to a Docker container registry.

# Table of Contents

- [Build and push multi platform docker images](#build-and-push-multi-platform-docker-images)
- [Table of Contents](#table-of-contents)
- [Example usage](#example-usage)
  - [build-and-push-multiplatform-docker-images](#build-and-push-multiplatform-docker-images)

# Example usage

## build-and-push-multiplatform-docker-images

```yaml
- name: Build a multiplatform Docker container and push it to Docker container registry
  uses: lojoh/gh-action-build-and-push-multi-platform-docker-images@v1.0
  with:
    docker-args: --build-arg GitHubPackagesAccessToken=${{ secrets.GITHUB_TOKEN }}
    docker-context: .
    docker-file: src/DemoApp/Dockerfile
    docker-registry: ghcr.io/lojoh
    github-token: ${{ secrets.GITHUB_TOKEN }}
    image-name: multi-platform-demo-app
    platform: linux/arm64,linux/amd64
    tag: ${{ env.tag }}
```
