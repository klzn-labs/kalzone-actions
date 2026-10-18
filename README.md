# kalzone-actions

Public GitHub Actions workflows for [Kalzone](https://platform.kalz.one).

## build.yml

The reusable workflow every Kalzone service calls to build its image. Kalzone
dispatches the caller workflow in the service repo; this workflow builds and
pushes the image with registry credentials Kalzone hands it over OIDC, then
reports the digest back.

```yaml
jobs:
  build:
    uses: klzn-labs/kalzone-actions/.github/workflows/build.yml@main
    with:
      release_id: ${{ inputs.release_id }}
      image: ${{ inputs.image }}
      platform_url: ${{ inputs.platform_url }}
```

Kalzone only accepts build callbacks from this exact workflow, so keep the
`uses:` path as written.
