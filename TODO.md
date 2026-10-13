# TODO — Image Captioning AI

## Current state (verified from the code, not just the README)
This one's actually solid: FastAPI + PyTorch/Transformers (BLIP) backend, React/Vite frontend, Docker Compose, a working `.github/workflows/ci.yml`, and a real `test_main.py` with 2 properly mocked tests (`test_health_check`, `test_caption_endpoint_mocked`).
- The GitHub repo's one-line description said "Generate simple captions for images using a CNN and a basic language model" — stale, didn't match the actual BLIP-based architecture. **Already fixed** to reflect the real stack.
- `test_audio_generation_mocked` in `backend/test_main.py` sets up all its mocks (gTTS, file write side effect) but ends in `pass` — it never actually asserts anything. It's the one incomplete piece in an otherwise solid test file.
- The "Offline Fallback Design" section in the README is explicitly a proposal (ONNX Runtime + quantized MobileNet in-browser), not implemented. That's fine, but worth labeling clearly as "planned" so a reader doesn't assume it's shipped.
- No screenshot/GIF/demo link anywhere despite having a full working frontend — for an accessibility-focused captioning tool, showing the actual UI (and ideally the audio output) is the single most convincing thing you could add.

## Improvements, roughly in priority order
1. **Finish `test_audio_generation_mocked`** — add real assertions (e.g. that the audio file was written, that the response includes it) instead of ending on `pass`.
2. **Add a demo screenshot or short screen-recording GIF to the README** — a captioned image + the audio player in the UI. This is the highest-leverage single addition given how visual/audio-driven the product is.
3. **Label the offline/ONNX fallback section as "Planned" explicitly** in the README, so it reads as a roadmap item, not a shipped feature.
4. **Surface the CI badge** in the README (the workflow already exists and runs, it's just not shown) — cheap, makes the repo look actively maintained.
5. **Note GPU vs CPU inference time** in the README (e.g. "~2s on GPU, ~Ns on CPU") — the current "Limitations" section mentions latency but gives no concrete numbers.
