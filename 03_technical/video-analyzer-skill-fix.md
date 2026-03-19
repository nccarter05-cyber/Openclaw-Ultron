# Video Analyzer Skill — Fix Options

**Problem:** The skill was built for macOS (Homebrew). It won't work on this Linux server as-is.

## Option A — Patch to use existing Python whisper (quick, 10 min)

- Change `REQUIRED_BINS` in `analyze_video.py` to use whisper instead of whisper-cli
- Update the whisper call syntax to match the Python whisper CLI
- Change `MODELS_DIR` path away from `/opt/homebrew/...`
- Remove `uv` dependency
- Works with what's already installed
- Slower than Option B but zero new installs

## Option B — Install whisper.cpp C++ binary (better long-term, 30-60 min)

- Compile or download whisper-cli (whisper.cpp binary) for Linux
- Install `uv` (Python package manager the script uses)
- Fix `MODELS_DIR` path to a Linux location like `/usr/local/share/whisper-cpp`
- whisper.cpp is significantly faster than the Python version for long videos

## Recommendation

- **Option A now** — Get it working quickly
- **Option B later** — Future upgrade once the TikTok cookie issue is also resolved
