# Voice Cloning Toolbox

This repository contains my implementation of the SV2TTS approach with a real-time vocoder. SV2TTS is a deep learning framework in three stages. In the first stage, a digital representation of a voice is created from a few seconds of audio. In the second and third stages, this representation is used as reference to generate speech given arbitrary text.

This project is maintained here and configured for local use. The instructions below explain how to run the toolbox and where to place datasets.

### Papers implemented

- 1806.04558 — SV2TTS — Transfer Learning from Speaker Verification to Multispeaker Text-To-Speech Synthesis
- 1802.08435 — WaveRNN (vocoder) — Efficient Neural Audio Synthesis
- 1703.10135 — Tacotron (synthesizer) — Tacotron: Towards End-to-End Speech Synthesis
- 1710.10467 — GE2E (encoder) — Generalized End-To-End Loss for Speaker Verification

## Heads up

This codebase reflects methods and tooling from its original design era. Newer open-source projects or commercial services may provide higher-quality audio out of the box. Use this repository if you want a local, inspectable implementation.

## Running the toolbox

The toolbox runs on macOS, Linux, and Windows (with appropriate Python and dependencies).

1. Install `ffmpeg` using your system package manager (it is required for reading and writing audio files). Verify installation by running:
```
ffmpeg
```
2. Install `uv` (optional) or use `pip`/`venv` to manage the Python environment. With `pip`:
```
pip install -U uv
```
3. Run one of the following commands depending on your setup:
```
# Run the toolbox with GPU support if available
uv run --extra cuda demo_toolbox.py
# Run the toolbox without GPU
uv run --extra cpu demo_toolbox.py

# Run the command-line interface
uv run --extra cuda demo_cli.py
uv run --extra cpu demo_cli.py
```

`uv` will create a `.venv` directory for an isolated Python environment when used. If you prefer not to use `uv`, create and activate a Python virtual environment and install the requirements.

### (Optional) Pretrained models

Pretrained models are typically downloaded automatically by the toolbox. If automatic download fails, obtain the pretrained models from the project's model storage or your preferred model hosting and place them in the expected `models` directory.

### (Optional) Datasets

For experimenting with the toolbox, a recommended dataset is `LibriSpeech/train-clean-100`. After downloading and extracting, place the contents in `<datasets_root>/LibriSpeech/train-clean-100`, where `<datasets_root>` is a directory of your choosing. You may also use your own recorded audio files instead of downloading public datasets.
