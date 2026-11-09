# interpret: Voice Translator

A one-screen voice translator for phones. Pick "From" and "To", tap the mic, speak, tap again, then tap Play. Built on the Gemini API (Flash-Lite for translation, the phone's own voice for playback, Gemini's voice as a fallback).

The API key is **not** in this code. Each phone stores its own copy after you paste it in Settings. Without a key the app runs in **demo mode**: tapping the mic plays a sample translation with the phone's voice.

**Key guide for users:** [`key-guide.html`](https://www.wong.cpa/interpret/key-guide.html), a step-by-step page in English, 简体中文, 繁體中文, 日本語, Español, Italiano and Français. It opens in the phone's language; add `?lang=zht` (or `zh`, `ja`, `es`, `it`, `fr`, `en`) to force one.

## 1. Turn on GitHub Pages

1. In this repo: **Settings → Pages**.
2. Source: **Deploy from a branch** → Branch: **main** → folder **/ (root)** → Save.
3. After a minute the site is live at `https://www.wong.cpa/interpret/`. (The `wongcpa.github.io` site uses the custom domain `www.wong.cpa`, so project sites are served there too; `https://wongcpa.github.io/interpret/` redirects to it.)

## 2. Set up the Gemini key (once)

1. Create a key at <https://aistudio.google.com/apikey>.
2. Decide free or paid:
   - **Free key:** no bill, but usage limits apply, and as with other free Google services, Google may use what you send (recordings and translations) to improve its products, and people may review it. Not for private or sensitive conversations.
   - **Paid key:** turn on billing for the project in AI Studio. Google doesn't use your data this way, and limits are higher. Normal personal use usually costs very little.
3. In Google Cloud Console → **APIs & Services → Credentials** → open the key → **API restrictions:** restrict it to the *Gemini API*. Google requires Gemini keys to be bound to a service account, so website restrictions aren't available; the key stays private because it's only stored on the phones where you paste it.
4. On a paid key, cap usage: **APIs & Services → Gemini API → Quotas** → set a low daily request limit (a few hundred is plenty for a family). Also add a budget alert under **Billing → Budgets & alerts**; alerts only notify you, while the quota actually stops usage.
5. If a key ever leaks, delete it in Credentials and paste a new one on each phone.

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

- **Interface languages:** English, 简体中文, 繁體中文, 日本語, Español, Italiano and Français. The app opens in the phone's language; change it under Settings → App language.
- **Typing:** type text in the box under the mic and tap Translate; it uses the same voices and Play button. Needs a key (demo mode only plays its samples).
- **Voice picker** (under "To"): Automatic, any phone voice for that language (free), or one of Gemini's 30 named voices (uses the key). Remembered per language. The ▶ button previews; each Gemini preview is generated once and reused.
- **Voice style** (Settings → Advanced): a free-text delivery style such as "dramatic and theatrical, like Moira Rose". When set, every playback uses a Gemini voice, which uses more quota. It changes only the delivery, never the words.
- Models: `gemini-3.5-flash-lite` for translation (falls back to older Flash-Lite models if retired; changeable under Settings → Advanced). `gemini-3.8-flash-lite-tts` / `gemini-3.8-flash-tts` for the fallback voice.
- Recording is capped at 60 seconds.
- To update the app, replace `index.html` in this repo; phones pick it up on next open.
