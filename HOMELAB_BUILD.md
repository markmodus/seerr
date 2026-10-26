# Homelab Seerr OIDC build

This fork rebases Seerr's experimental OpenID Connect implementation onto upstream Seerr v3.5.1. The identity provider remains the homelab's existing self-hosted Authentik instance; this repository adds the Seerr-side OIDC client and does not embed provider credentials or Authentik configuration.

The publish workflow builds an ARM64 image for the Pi4 only when a `homelab-v*` tag is pushed. It publishes to `ghcr.io/<owner>/seerr`. The image uses Seerr's upstream Dockerfile and includes the source commit in its `COMMIT_TAG` build argument.

Example tag: `homelab-v3.5.1-oidc.1`.

Before deploying an image, verify the package visibility and pull the image on Pi4. Keep the current Seerr configuration backup and the prior image digest available for rollback. OIDC remains experimental upstream, so test it with a copy of the app configuration before replacing the running service.
