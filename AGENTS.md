# OpenSearch image

## Purpose

This repository builds the custom OpenSearch base image used by the local
development stack and, later, by the NAS deployment.

## Boundaries

- Keep image build configuration and release documentation here.
- Keep Compose, runtime configuration, ports, and persistent data in
  `local.ops` or `nas.ops`.
- Do not include application mappings, indexes, or data migrations here.

## Verification

- Build the image with the pinned OpenSearch version.
- Verify the installed analysis plugins are present.
- Do not commit generated image layers or local data.

## Git

Do not commit unless explicitly requested.
