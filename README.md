# Poker44-gen17-tuner-synth15

Minimal release repository for Poker44 miner runtime scoring.

This repository is a standalone miner variant prepared for gen17 synth rollout with an overlay tuner fitted on labeled public benchmark chunks.

## Quick start

```bash
git clone https://github.com/tomkaba/poker44-miner-gen17-tuner-synth15.git
cd poker44-miner-gen17-tuner-synth15
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
pip install -e .
```

## Run Miner

```bash
python neurons/miner.py
```

or legacy wrapper:

```bash
./start_miner.sh HOTKEY_ID[,HOTKEY_ID2,...]
```

## Implementation

- Scorer entrypoint: poker44/miner_heuristics.py
- Overlay synth scorer: models/score_chunk.py
- Entry point: neurons/miner.py
- Tuner config: models/tuner.json
- Local base synth runtime: models/base_runtime/
- Base pre artifact: models/base_runtime/pre_artifact/
- Active math artifacts: pf boost, post penalty, post boost
- Local math helpers: export_benchmark_phase1_dataset.py, gen17_math_1_pf.py, gen17_math_1_pf_boost.py, gen17_math_1_post.py, gen17_math_1_post_boost.py
- Base release lineage: gen17_synth15 overlay tuner fit999

Manifest implementation SHA256 is computed from:

- models/score_chunk.py
- models/tuner.json
- models/base_runtime/score_chunk.py
- models/base_runtime/synth_manifest.json
- models/base_runtime/pre_artifact/*
- optional models/base_runtime/pf_* and models/base_runtime/post_* model.json files that are packaged for this release
- export_benchmark_phase1_dataset.py
- gen17_math_1_pf.py
- gen17_math_1_pf_boost.py
- gen17_math_1_post.py
- gen17_math_1_post_boost.py
- neurons/miner.py
- poker44/miner_heuristics.py
- runtime files tracked in repository
