# n8n-root
Containerfiles for n8n: same as upstream, but rootful.

n8n is great, but its Dockerfiles assume that it will be deployed using rootful
docker, so user privileges will be dropped and the server will be executed as
`node` user. This is Ok for the general use-case.

If the container is run in rootless mode (e.g. using [podman](https://podman.io)
or [rootless docker](https://docs.docker.com/engine/security/rootless/)), there
is no need for that and it will actually complicate things a bit.

This repo provides a Containerfile to build a n8n container image running as
root, to be used in rootless environments. Keeping it up-to-date with upstream
is done as a best-effort basis. PR are welcome.

## Building

You can build an image with e.g.

```
VERSION="0.156.0" podman build --build-arg N8N_VERSION=$VERSION -t myn8n:$VERSION .
```

We (manually) upload some images on Docker Hub: https://hub.docker.com/r/dvisionlab/n8n-root
