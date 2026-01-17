# Voicemode Parameters Reference

## API Signature

```python
converse(
    message: str,
    listen: bool = True,
    options: dict = None
)
```

## Core Parameters

### message (required)
**Type:** string
The message to speak to the user.

### listen
**Type:** boolean (default: true)
Whether to listen for a voice response after speaking.

### options
**Type:** dict (optional)
Additional parameters passed as a dictionary. All options below go in this dict.

**Example:**
```python
converse("Hello!", listen=True, options={"skip_tts": True, "speed": 1.5})
```

---

## Options Reference

All parameters below are passed via the `options` dict.

### Timing Options

#### listen_duration_max
**Type:** number (default: 120.0 seconds)
Maximum time to listen for response.

#### listen_duration_min
**Type:** number (default: 2.0 seconds)
Minimum recording time before silence detection can stop.

### Voice & TTS Options

#### voice
**Type:** string (optional)
Override TTS voice selection. Examples: nova, shimmer, alloy (OpenAI); af_sky, af_sarah (Kokoro)

#### tts_provider
**Type:** "openai" | "kokoro" (optional)
TTS provider selection. Usually let system auto-select.

#### tts_model
**Type:** string (optional)
TTS model: tts-1, tts-1-hd, gpt-4o-mini-tts

#### tts_instructions
**Type:** string (optional)
Tone/style instructions for emotional speech. Requires tts_model="gpt-4o-mini-tts"

#### speed
**Type:** number (0.25 to 4.0, optional)
Speech playback rate. 1.0 = normal.

### Audio & Silence Detection Options

#### disable_silence_detection
**Type:** boolean (default: false)
Disable automatic silence detection.

#### vad_aggressiveness
**Type:** integer 0-3 (optional)
Voice Activity Detection strictness. 0=least, 3=most aggressive.

#### skip_tts
**Type:** boolean (optional)
Skip text-to-speech, listen only.

#### chime_enabled
**Type:** boolean (optional)
Enable/disable audio feedback chimes.

#### audio_format
**Type:** string (optional)
Audio format: pcm, mp3, wav, flac, aac, opus

---

## Migration from Legacy API

```python
# Old (no longer works)
converse("Hello", wait_for_response=False, speed=1.5)

# New
converse("Hello", listen=False, options={"speed": 1.5})
```
