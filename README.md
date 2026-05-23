# Voice Shadowing

A single-page voice training tool. Speak, hear yourself back, repeat.

## How It Works

1. Click **Start** — browser requests microphone access
2. App listens for sound above the threshold (status dot turns amber)
3. Voice detected → recording begins with a ~300ms pre-roll so the first word isn't lost (status dot turns red, waveform bars turn red)
4. Silence held for the configured delay → recording stops and plays back (status dot turns green, waveform bars turn green)
5. After playback + rest delay, the cycle repeats automatically
6. Click **Stop** to end the session

## Settings

| Setting | Range | Description |
|---|---|---|
| Voice threshold | 2–40 | Minimum volume to trigger recording |
| Silence to play back | 0.5–3s | How long silence must last before playback |
| Rest after playback | 0–3s | Pause between playback and next listen cycle |

## Tech

- Vanilla JS, no dependencies
- Web Audio API (`AudioContext`, `AnalyserNode`, `MediaRecorder`)
- Pre-roll recording captures ~300ms before voice threshold is crossed
- AudioContext unlock for iOS Safari via silent buffer playback
- Zero-gain node keeps WebAudio graph active on iOS Safari
- Fallback to `<Audio>` element if `decodeAudioData` fails
- Google Fonts: IBM Plex Mono / IBM Plex Sans

## Usage

Open `index.html` in any modern browser (Chrome, Firefox, Safari, Edge). No build step needed.
