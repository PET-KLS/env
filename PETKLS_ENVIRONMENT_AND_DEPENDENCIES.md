# Environment and dependency notes

## Scope

This package retains the supplied environment captures, package versions and Conda package inventories. Duplicate PET-KLS YAML content was consolidated, personal installation prefixes removed, and a personal HPC output path and source notebook sharing identifiers removed from the public Colab manifest. No dependency versions were upgraded.

The source notes describe an x86-64 Linux HPC capture (RHEL 8.10, glibc 2.28, Conda 24.1.2 with libmamba) and a source commit dated 8 September 2026. These platform details are reported provenance, not independently verified by this package.

## Reconstruction limits

- `pet_kls_environment.yml` combines Conda dependencies with a pinned pip section. It is the most complete supplied installation specification.
- `pet_kls_explicit.txt` records platform-specific Conda package URLs; it does not include the pip section.
- Conda JSON inventories are audit records, not installation files. Entries from pip are identified by their recorded channel/platform.
- `brainmaps_environment.yml` and its inventory contain the base runtime only. Additional scientific dependencies must be captured from the environment actually used for those analyses.
- No `brainviz` files, separate pip-freeze snapshots or `brainmaps` explicit snapshot were supplied. This package does not fabricate them.
- The Colab manifest is static source inspection. Recorded imports and installation commands do not prove which versions executed successfully.
- Atlas resources, normative maps and participant data must be obtained and configured separately. This repository contains no analysis inputs.

## Local checks after installation

```bash
conda run -n pet_kls python -c "import bct, brainspace, dtaidistance, enigmatoolbox, networkx, neuromaps, nibabel, nilearn, numpy, pandas, pygam, scipy, sklearn, statsmodels, surfplot; print('Imports OK')"
conda run -n brainmaps python --version
```

Imports check availability only. Confirm numerical reproducibility by running the analysis workflow and comparing its outputs with reference results. Recreating the environments and running these import checks were not performed while preparing this publication package.

## Updating the archive

After activating each analysis environment, export its YAML, Conda JSON inventory, platform-specific explicit snapshot and pip inventory together. Remove local prefixes and nonportable build paths before publication. Keep environments separate unless the combined workflow is revalidated.
