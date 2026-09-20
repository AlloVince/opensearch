# opensearch

Custom OpenSearch image with the analysis plugins used by YinXing search.

## Build

```bash
docker build -t allovince/opensearch:3.8.0 .
```

The image is pinned to OpenSearch `3.8.0`, matching the NAS compatibility
baseline.

## Release

GitHub Actions automatically builds and pushes the public Docker Hub image
`allovince/opensearch`:

- Push to `main` publishes `allovince/opensearch:staging`.
- Push a version tag such as `3.8.0` publishes
  `allovince/opensearch:3.8.0`.

The Docker Hub repository must be created as a public repository, and the
GitHub repository must define `DOCKER_USERNAME` and `DOCKER_PASSWORD` Actions
secrets.

To publish a version tag after the image has been built and verified:

```bash
git tag -a 3.8.0 -m "OpenSearch 3.8.0"
git push origin 3.8.0
```
