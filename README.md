# Colab Remotion Video Pipeline

An automated, cloud-based programmatic video production pipeline for high-retention educational science content, built with Python, React/Remotion 4.0, Deepgram, and FFmpeg.

## Overview
High-retention explainer videos typically require powerful local GPUs and hours of manual keyframing. This pipeline automates the entire workflow inside Google Colab (with optional scaling to AWS Lambda):
- **Automated Voiceover:** Chunks scripts and generates studio narration via the Prompt2Voice API (`eleven_v4`), with bass EQ and silence trimming via FFmpeg.
- **Millisecond Audio Sync:** Uses Deepgram (`nova-2`) to extract word-level timestamps (`deepgram_timestamps.json`) for exact subtitle highlighting and 3–4 second visual cuts.
- **Direct HD Asset Sourcing:** Fetches topic-matched HD stock video clips via the Pixabay API.
- **Programmatic Motion Graphics:** Renders kinetic typography, glassmorphic HUD overlays, and dynamic camera movements using React and Remotion 4.0.

## Tech Stack
- **Orchestration:** Python 3, Google Colab
- **Video Engine:** React 18, Remotion 4.0 (`@remotion/cli`, `@remotion/renderer`)
- **Audio & Media:** Prompt2Voice API, Deepgram API (`nova-2`), Pixabay API, FFmpeg

## Setup
1. Open the pipeline in Google Colab (T4 GPU recommended for faster rendering).
2. Add your API keys (`PROMPT2VOICE_API_KEY`, `DEEPGRAM_API_KEY`, `PIXABAY_API_KEY`) as environment variables.
3. Run `pipeline.py` to generate audio, sync timestamps, download assets, and build `scenesData.js`.
4. Render with Remotion:
   ```bash
   npx remotion render entry.jsx QuantumConsciousnessMasterclass final_video.mp4 --public-dir=./public --concurrency=4 --gl=angle
