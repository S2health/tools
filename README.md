# tools repo
S2 tools, mainly scripts.

## adlc scripts
### adlc_export_json
Script to generate flat JSON, including JSON OPTs from a model repository in which models are found under `/models`. Uses the `adlc` CLI version of ADL Workbench.

**Trigger event**: any change to `/models` on `main` branch in the source repo.

**Usage**: `adlc_export_json --source_repo <source_repo>`

**Working directory**: run from parent directory of Git repos

**Output**: Writes the following in the source repo:

* JSON files at `/build/models/flat/json`; (/build is .gitignored)
* log file to `/build/models/logs/adlc_export_json.log`;
* build manifest at `/build/models/build_manifest.csv`;

Example:
```
$ adlc_export_json --source_repo S2-models
```

### adlc_run_exports
Script to export ADL2 OPTs, various reports, and terminology bindings, from a model repository in which models are found under `/models`. Uses the `adlc` CLI version of ADL Workbench.

**Trigger event**: any change to `/models` on `main` branch in the source repo.

**Usage**: `adlc_run_exports --source_repo <source_repo>`

**Working directory**: run from parent directory of Git repos

**Output**: Writes output to source repo in various directories: `/reports`, `/opts`, `/term_bindings`

Example:
```
$ adlc_run_exports --source_repo S2-models
```

### s2_gen_synth_data-all
Script to generate synthesized data from ADL2 OPTs in the source repo directory `/opts`. Uses the `s2` CLI tool found in `Medical-tools` repo.

**Trigger event**: any change to `/opts` on `main` branch in the source repo.

**Usage**: `s2_gen_synth_data-all --source_repo <source_repo>`

**Working directory**: run from parent directory of Git repos

**Output**: Writes output to S2-test-data repo in `/synth/<source repo>`, 

Example:
```
$ s2_gen_synth_data-all --source_repo S2-models
```
