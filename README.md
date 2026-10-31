# PET-KLS environments

Recorded software environments and dependency inventories for the [PET-KLS](https://github.com/PET-KLS) analyses, including the [spatiotemporal brain-map pipeline](https://github.com/PET-KLS/Spatiotemporal_microstructure_gradients).

## Environment files

| Environment | Python | Specification | Package inventory |
| --- | --- | --- | --- |
| `pet_kls` | 3.13.2 | [YAML](pet_kls_environment.yml) · [Linux Conda package snapshot](pet_kls_explicit.txt) | [JSON](pet_kls_conda_packages.json) |
| `brainmaps` | 3.10.18 | [YAML](brainmaps_environment.yml) | [JSON](brainmaps_conda_packages.json) |

`pet_kls` records the scientific stack, including graph analysis, statistical modelling and neuroimaging tools. The supplied `brainmaps` capture contains only the base Python runtime and system libraries; it does not provide a complete scientific brain-mapping environment. A separate `brainviz` environment is mentioned in earlier records but its files are not included in this package.

## Recreate

These captures originate from Linux x86-64. The YAML files retain recorded versions and Linux-specific dependencies, so they are not guaranteed to solve on other platforms. Personal installation prefixes have been removed.

```bash
conda env create --file pet_kls_environment.yml
conda activate pet_kls
```

For the captured base `brainmaps` environment:

```bash
conda env create --file brainmaps_environment.yml
```

The explicit snapshot restores **Conda packages only** on compatible Linux systems:

```bash
conda create --name pet_kls_conda_snapshot --file pet_kls_explicit.txt
```

It excludes pip-installed scientific packages. Use the YAML for the combined Conda/pip specification. The explicit snapshot pins package URLs and builds but is not a full runtime or data lock.

## Other records

- [Environment notes](PETKLS_ENVIRONMENT_AND_DEPENDENCIES.md): scope, checks and reconstruction limits.
- [Colab dependency/configuration manifest](COLAB_DEPENDENCY_CONFIG_MANIFEST.json): indexed imports, installation commands and configuration expressions from the source notebook; this is a static inventory, not an executable configuration or package lock.
- [SHA256SUMS](SHA256SUMS): checksums for the packaged files.

The Colab record reports Python 3.12.13, separately from the Conda environments. Notebook installation commands can change its runtime; do not assume it is equivalent to either Conda capture.

## Citation and licence

Please cite this environment archive using [CITATION.cff](CITATION.cff), alongside the PET-KLS analysis software, associated study and relevant methods. Repository-authored documentation and configuration are available under the [MIT License](LICENSE). Listed third-party software and datasets retain their own licences.
