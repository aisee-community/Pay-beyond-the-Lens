# Pay beyond the Lens

**Contactless payment authentication through AiSee — scan, confirm, done.**

Pay beyond the Lens lets a user complete a payment by scanning a QR code with **AiSee**, triggering authentication automatically, and confirming with a simple double-click — no unlocking a separate payment app, no manual code entry.

## How it works

1. **Scan** — Point AiSee at the merchant's QR code.
2. **Authenticate** — AiSee recognizes the code and automatically triggers the authentication flow.
3. **Confirm** — Double-click to confirm, and the payment is completed.

This flow is designed to minimize the number of manual steps between "I want to pay" and "payment done," particularly for hands-busy or accessibility-focused use cases where fumbling with a phone screen is a real barrier.

## Tech stack

- **Kotlin / Java** — Android application layer
- **Gradle (Kotlin DSL)** — build system
- **[`voice-activation-uart`](https://github.com/aisee-ai/voice-activation-uart)** — git submodule handling voice-activation over UART, used to trigger and confirm actions hands-free alongside the double-click gesture

## Getting started

### Prerequisites
- Android Studio (recent stable version)
- JDK 17+
- An AiSee-compatible device for on-device testing (the QR scan → auth → payment flow depends on it)

### Clone and build

```bash
# Clone with submodules — the voice-activation module won't be populated otherwise
git clone --recurse-submodules https://github.com/aisee-community/Pay-beyond-the-Lens.git
cd Pay-beyond-the-Lens

# If you already cloned without --recurse-submodules:
git submodule update --init --recursive

# Build
./gradlew build
```

Open the project in Android Studio and run it on a connected AiSee device to test the full scan → authenticate → confirm flow.

## Project structure

```
Pay-beyond-the-Lens/
├── app/            # Main Android application (Kotlin/Java)
├── gradle/          # Gradle wrapper files
├── vad_module/     # Voice-activation submodule (aisee-ai/voice-activation-uart)
└── build.gradle.kts
```

## Contributing

Issues and pull requests are welcome. If you're proposing a change to the authentication or payment-confirmation flow specifically, please open an issue first to discuss the approach, given the sensitivity of that path.

## License

See [LICENSE](LICENSE) for details.
