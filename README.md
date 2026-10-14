# IRON AI — Android starter source

IRON is a Kotlin + Jetpack Compose Android assistant prototype with an original, calm, cinematic personality. Spoken replies begin with “Yes, my King.” It is inspired by dark-fantasy assistant vibes, not a clone of a copyrighted character or actor voice.

## Included in this build
- Dark sci-fi IRON interface.
- Text chat with a local demo fallback.
- Tap-to-talk using Android SpeechRecognizer (requires microphone permission and an installed recognition service).
- Android TextToSpeech with lower pitch/rate; the actual voice depends on voices installed on the phone.
- Gemini text generation through the Gemini REST API when a key is configured.
- Prompt Forge shortcut that sends a prompt-engineering request to Gemini.
- Opens Android Settings from inside IRON.
- AI / Video shortcut opens Gemini in the browser; this is not native video generation.
- Circle Search button is a placeholder; real screenshot capture, selection/cropping, and vision upload are not implemented.

## Not implemented yet (do not assume these work)
- Always-on “Hey IRON” wake word. This build uses tap-to-talk only. Reliable wake-word support needs a dedicated on-device wake engine, an explicitly started foreground microphone service, a persistent notification, battery testing, and permissions. Android restricts background microphone use.
- Native Circle-to-Search / screen selection. Requires a user-consented MediaProjection flow or an appropriate accessibility-based integration, followed by image cropping and Gemini vision requests.
- Native video generation. The shortcut opens Gemini; actual video rendering requires a supported video model/service, account access, and possibly separate billing/API credentials.
- Full control of every phone feature. Android intentionally blocks silent unrestricted control. App launching, system settings, and approved actions can be added; sensitive actions must require permission/confirmation.
- A true actor or character voice. IRON uses Android TTS settings; voice quality depends on installed voices. No voice cloning is included.

## Configure Gemini
1. Get an API key from Google AI Studio.
2. Copy `local.properties.example` to `local.properties` (or edit your existing local.properties) and set `GEMINI_API_KEY=your_key`.
3. Sync Gradle and build. Never share an APK/source with a key embedded in it: keys embedded in a mobile app can be extracted. For public distribution, use a backend that protects the key.

## Build
- Open the project folder in Android Studio and allow Gradle sync.
- For phone-only builds, use a compatible Android IDE such as AndroidIDE if it supports this Gradle/Compose project. Some mobile IDEs may not support all required Gradle plugins.
- Select Build > Build APK(s), or use the IDE's equivalent build action.
- Install the debug APK and grant microphone permission when prompted.

## Security / permissions
IRON does not silently capture your screen or continuously listen for a wake word in this build. It only starts speech recognition after you tap the microphone. Settings opens through an Android system intent.
