<p align="center"><img src="https://raw.githubusercontent.com/stackrox/kube-linter/main/images/logo/KubeLinter-horizontal.svg" width="360"></p>

# kube-linter-action - KubeLinter GitHub Action

This is a GitHub action for scanning Kubernetes YAML files and Helm charts in your GitHub workflow with [kube-linter](https://github.com/stackrox/kube-linter).

## Quickstart

1. Copy [.github/workflows/kube-linter-sample.yml](https://github.com/stackrox/kube-linter-action/tree/main/.github/workflows/kube-linter-sample.yml) file to `.github/workflows` directory in your repo.
2. Adjust scan `directory` to the location where your Kubernetes or Helm files are. See Parameters below.

The new workflow will run every time there's a new push to the repo.  
Workflow will fail if kube-linter detects issues. You'll find issues in the output of `kube-linter-action`.

### Example

```yaml
      - name: Scan repo with kube-linter
        uses: stackrox/kube-linter-action@v1.0.4
        with:
          directory: yamls
          config: .kube-linter/config.yaml
          format: sarif
          output-file: kube-linter.sarif
```

### Parameters

| Parameter name | Required? | Description |
| --- | --- | --- |
| `directory` | **(required)** | Path of file or directory to scan, absolute or relative to the root of the repo. |
| `config` | (optional) | Path to a [configuration file](https://docs.kubelinter.io/#/configuring-kubelinter) if you wish to use a non-default configuration. |
| `format` | (optional) | Output format. Allowed values: `sarif`, `plain`, `json`. Default is `plain`. |
| `output-file` | (optional) | Path to a file where kube-linter output will be stored. Default is `kube-linter.log`. File will be overwritten if it exists. |
| `version` | (optional) | kube-linter release version to use, e.g. "0.2.4". The latest available version is used by default. |
