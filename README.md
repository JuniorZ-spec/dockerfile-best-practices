# dockerfile-best-practices

Minimal, multi-stage Dockerfile templates that follow the basics that actually matter for image size and security: multi-stage builds, non-root user, pinned base image, no dev dependencies in the final layer.

## What's here

- `node/Dockerfile` — Node.js app, `npm ci` in a build stage, runtime image ships only `node_modules` + `dist`
- `python/Dockerfile` — Python app, dependencies installed with `--user` in a build stage and copied over

Both run as a non-root user and expose one port.

## Lint

```bash
hadolint node/Dockerfile
hadolint python/Dockerfile
```

`.hadolint.yaml` ignores DL3018 (pin apk versions) since these images don't call `apk add`.
