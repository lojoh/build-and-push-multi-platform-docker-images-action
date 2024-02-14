# Build and push multi platform docker images

A Github Action used to build multiplatform docker images and push them to a Docker container registry.

# Table of Contents

- [Build and push multi platform docker images](#build-and-push-multi-platform-docker-images)
- [Table of Contents](#table-of-contents)
- [Example usage](#example-usage)
- [Compatibility](#compatibility)
  - [v1.0](#v10)

# Example usage

See an example workflow file here: [example_workflow.yml](https://github.com/lojoh/build-and-push-multi-platform-docker-images-action/blob/main/example_workflow.yml).

Preview:

```yaml
- name: Build Docker container and push it to GitHub Packages
  uses: lojoh/build-and-push-multi-platform-docker-images-action@1.0
  with:
    docker-args: --build-arg GitHubPackagesAccessToken=${{ secrets.PAT }} --build-arg ReleaseVersion=${{ steps.version.outputs.version }}
    docker-context: .
    docker-file: src/DemoApp/Dockerfile
    docker-registry: ghcr.io/lojoh
    github-token: ${{ secrets.PAT }}
    image-name: multi-platform-demo-app
    tag: 1.2.3
    platform: linux/arm64,linux/amd64
```

Be sure to update your Dockerfile with ARG BUILDPLATFORM and use it as demonstrated below:

```Dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base
USER app
WORKDIR /app
ARG BUILDPLATFORM
FROM --platform=$BUILDPLATFORM mcr.microsoft.com/dotnet/sdk:8.0 AS build
```

# Compatibility

## [v1.0](https://github.com/lojoh/gh-action-build-and-push-multi-platform-docker-images/releases/tag/1.0)

Supported runners:

- `ubuntu-latest`
- other runners are not tested but may work.

Supported frameworks & languages:

- `.NET 7`
- `.NET 8`
- other frameworks or languages are not tested but may work.
