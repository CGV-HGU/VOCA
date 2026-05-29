# VOCA: A VLM-Optimized Call Approach for Zero-Shot Navigation Using Target-Context Cues

### Zero-Shot Navigation Using Target-Context Cues

This repository contains the official code for **VOCA: A VLM-Optimized Call Approach for Zero-Shot Navigation Using Target-Context Cues**.

## Main Entry Points

- `objnav_benchmark.py`: ObjectNav evaluation with the VOCA planner.
- `metrics_summary.py`: Metric summary from the evaluation CSV.
- `evaluate_policy.py`: Pixel navigation policy evaluation.

## Configuration

Paths and model settings are configured through environment variables or CLI arguments. Common variables:

```bash
export VOCA_DATA_ROOT=/path/to/data
export VOCA_CHECKPOINT_DIR=/path/to/checkpoints
export VOCA_POLICY_CHECKPOINT=/path/to/pixelnav_A.ckpt
export VOCA_YOLOE_CHECKPOINT=/path/to/yoloe-11l-seg.pt
export VOCA_DEVICE=cuda:0
export VOCA_LLM_BACKEND=gemini
```

Run ObjectNav evaluation:

```bash
python objnav_benchmark.py --eval_episodes 400
```
