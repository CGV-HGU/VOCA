# VOCA Repository Cleanup Notes

This note tracks the work needed before publishing the VOCA code repository.

Paper title:

**VOCA: A VLM-Optimized Call Approach for Zero-Shot Navigation Using Target-Context Cues**

## Goals

- Make naming consistent across files, classes, scripts, and documentation.
- Make the repository runnable by other researchers.
- Separate paper-specific benchmark code from reusable VOCA modules.
- Document datasets, checkpoints, API keys, and expected outputs clearly.

## Naming Cleanup

- Use `VOCA` as the project name everywhere.
- Replace old names such as `ISA` in documentation, comments, logs, and scripts.
- Use `objnav_benchmark.py` as the main ObjectNav evaluation entrypoint.
- Align class names with the paper terminology:
  - `VLMPlanner`
  - `PolicyAgent`
  - VOCA planner / VOCA agent naming, if appropriate.
- Standardize output names such as metrics CSVs, video folders, and temporary trajectory paths.

## Suggested Repository Structure

```text
VOCA/
  README.md
  REPO_CLEANUP.md
  requirements.txt
  configs/
  scripts/
  voca/
    planner/
    policy/
    perception/
    utils/
  checkpoints/
  data/
  outputs/
```

Notes:

- `voca/` should contain importable project code.
- `scripts/` should contain runnable commands such as evaluation and metric summary scripts.
- `configs/` should contain Habitat, model, and benchmark configuration files.
- `checkpoints/`, `data/`, and `outputs/` should usually be ignored by git, with README instructions explaining where to download or place files.

## README Checklist

- Add paper title and short abstract-style description.
- Add installation instructions.
- Add dataset setup instructions for HM3D / Habitat.
- Add checkpoint setup instructions.
- Add environment variables for API keys and model providers.
- Add one minimal evaluation command.
- Add expected output files and metrics.
- Add citation block.
- Add license note.

## Code Cleanup Checklist

- Move hard-coded paths into config files or CLI arguments.
- Remove hard-coded GPU setting from module import time:
  - `CUDA_VISIBLE_DEVICES`
  - model device strings such as `cuda:0`
- Replace `from constants import *` with explicit imports from `settings.py`.
- Ensure temporary output directories are configurable.
- Avoid failing when `./tmp/trajectory_X` already exists.
- Add `if __name__ == "__main__":` guards for runnable scripts.
- Make LLM provider selection explicit.
- Add clear errors for missing checkpoints, datasets, and API keys.

## Reproducibility Checklist

- Pin or document Python version.
- Create `requirements.txt` or `environment.yml`.
- Document Habitat-Sim / Habitat-Lab versions.
- Document YOLOE checkpoint source.
- Document policy checkpoint source.
- Document LLM/VLM model versions used in the paper.
- Add a small smoke-test command if possible.

## GitHub Hygiene

- Add `.gitignore`.
- Keep generated files out of git:
  - videos
  - logs
  - temporary trajectories
  - checkpoints
  - datasets
  - caches
- Check that no API keys or private paths are committed.
- Add license.
- Add citation information.

## Immediate Next Steps

- [x] Rename documentation from old project names to VOCA.
- [x] Add `.gitignore`.
- [x] Add VOCA-specific ignore rules for generated outputs, datasets, and checkpoints.
- [x] Split hard-coded paths, devices, checkpoints, and LLM backend defaults into `settings.py`.
- [x] Rename implementation-mismatched GPT-4V planner naming to VLM planner naming.
- [x] Rename LLM backend modules/functions to `gemini_request.py`, `ollama_request.py`, `text_response`, and `vision_response`.
- [x] Rename Habitat config utilities to `habitat_config.py`.
- [ ] Add a minimal `requirements.txt` or environment note.
- [ ] Refactor `objnav_benchmark.py` into a cleaner evaluation entrypoint.
- [x] Update README with setup and run commands.
