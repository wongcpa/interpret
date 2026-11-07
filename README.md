# Translate

A one-screen voice translator for phones. Pick "From" and "To", tap the mic, speak, tap again, then tap Play. Built on the Gemini API (Flash-Lite for translation, the phone's own voice for playback, Gemini's voice as a fallback).

The API key is **not** in this code. Each phone stores its own copy after you paste it in Settings.

## 1. Turn on GitHub Pages

1. In this repo: **Settings → Pages**.
2. Source: **Deploy from a branch** → Branch: **main** → folder **/ (root)** → Save.
3. After a minute the site is live at `https://wongcpa.github.io/<repo-name>/`.

## 2. Set up the Gemini key (once)

1. Create a key at <https://aistudio.google.com/apikey>.
2. Set up billing on that project in AI Studio (paid tier: higher limits, prompts not used for training).
3. In Google Cloud Console → **APIs & Services → Credentials** → open the key:
   - **API restrictions:** restrict to *Generative Language API*.
   - **Application restrictions:** *Websites* → add `https://wongcpa.github.io/*`.
4. In **Billing → Budgets & alerts**, add a small monthly budget alert (for example, $5).

## 3. Set up each phone (once)

1. Open the site link in **Safari** (iPhone) or **Chrome** (Android).
2. Add it to the home screen:
   - iPhone: Share → **Add to Home Screen**.
   - Android: ⋮ menu → **Add to Home screen** / **Install app**.
3. Open it from the home screen. Tap the gear, paste the key, tap **Save key** (it tests the key).
4. Tap the mic once and allow microphone access.

### Optional: install phone voices (faster, free playback)

If a phone lacks a voice for a language, the app uses Gemini's voice instead and shows a tip.

- iPhone: Settings → Accessibility → Spoken Content → Voices → add *Chinese (Hong Kong)* and *Spanish (Spain)*.
- Android: Settings → search "Text-to-speech" → choose **Speech Services by Google** as the engine → its settings → **Install voice data** → add Cantonese (Hong Kong) and Spanish (Spain). Samsung phones may default to Samsung's engine; switch it to Google.

Menu names vary by phone and OS version.

## Notes

- Models: `gemini-3.5-flash-lite` for translation (falls back to older Flash-Lite models if retired; changeable under Settings → Advanced). `gemini-3.8-flash-lite-tts` / `gemini-3.8-flash-tts` for the fallback voice.
- Recording is capped at 60 seconds.
- To update the app, replace `index.html` in this repo; phones pick it up on next open.
