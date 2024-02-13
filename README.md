# Build and push multi platform docker images

A Github Action used to build multiplatform docker images and push them to a Docker container registry.

# Table of Contents

- [Build and push multi platform docker images](#build-and-push-multi-platform-docker-images)
- [Table of Contents](#table-of-contents)
- [Example usage](#example-usage)
- [Compatibility](#compatibility)
  - [v1.0](#v10)

# Example usage

https://github.com/lojoh/build-and-push-multi-platform-docker-images-action/blob/01a10fd6985b9e2443a0ce013839551be0839dd4/example_workflow.yml

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
