# :gear: action-setup-kengine

[![Documentation][docs_badge]][docs]
[![License][license_badge]][license]
![](https://github.com/khulnasoft/action-setup-kengine/workflows/Tests/badge.svg)

> Setup the Kengine CLI in Github actions

## About
This action sets up the [Kengine CLI](https://kengine.khulnasoft.com/docs/cli/install/) in Github Actions.

This action can be run on `ubuntu-latest`, and `macos-latest` GitHub Actions runners, and will install and expose a specified version of the `kengine` CLI on the runner environment.

## Usage

Create a marker for every new deployment

```yaml
steps:
  - uses: khulnasoft/action-setup-kengine@v0.0.1
    with:
      kengine-api-key: ${{ secrets.KENGINE_API_KEY }} # Can be imported from Github Actions Secrets
  - name: 📍Create marker
    run: |
      kengine mark \
      --name Deployment \
      --url "${{ github.server_url }}/${{ github.repository }}/actions/runs/${{ github.run_id }}" \
      --metadata '${{ toJson(github) }}' \
      --service ${{ github.repository }}
```

The marker will be available on the timeline when you query your telemetry daya

![](./assets/marker.png)


## Inputs
The actions supports the following inputs:

- `kengine-api-key`: The API key to use with the Kengine CLI. You can get your API key  in the [Kengine console](https://console.kengine.khulnasoft.com)
- `version`: The version of `kengine` to install, defaulting to the latest version

## Contributing

Feel free to submit PRs or to fill issues. Every kind of help is appreciated. 

Kindly check our [Contributing](Contributing.md) guide on how to propose
bugfixes and improvements, and submitting pull requests to the project.

## License

&copy; Kengine Limited, 2023

Distributed under MIT License (`The MIT License`).

See [LICENSE](LICENSE) for more information.

<!-- Badges -->

[docs]: https://kengine.khulnasoft.com/docs/
[docs_badge]: https://img.shields.io/badge/docs-reference-blue.svg?style=flat-square
[license]: https://opensource.org/licenses/MIT
[license_badge]: https://img.shields.io/github/license/kengine/cli.svg?color=blue&style=flat-square&ghcache=unused
