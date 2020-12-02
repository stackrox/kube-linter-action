# kube-linter-action

# kube-linter-action GitHub action

This is a GitHub action for scanning Kubernetes deployment files with [kube-linter](https://github.com/stackrox/kube-linter).  This includes both the action itself (.github/actions) and sample GitHub workflow (.github/workflows) and a test YAML.

Quick deployment:

1.  Create a new GitHub repo.
2.  Push all files from the `sample` directory into the repo.
3.  The `kube-linter.yml` workflow will run as an action every time there's a new push to this repo.

The action takes two parameters.

```
      - name: Scan repo
        id: kube-lint-repo
        uses: stackrox/kube-linter-action@v0.0.1
        with:
          directory: yamls
          config: .kube-linter/config.yaml
```

* `directory` is mandatory -- this is the directory of deployment files to scan.  
* `config` is optional -- this is the path to a [configuration file](https://github.com/stackrox/kube-linter/blob/main/config.yaml.example) if you wish to use a non-default configuration.