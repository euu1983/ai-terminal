# AI Terminal — Privacy Policy v2 DRAFT

**Status**: DRAFT — awaiting yisheng review + 三生 final approve before deploy  
**Deploy target**: `https://ai-terminal.org/privacy.html` (GitHub Pages: `github.com/euu1983/ai-terminal`, main branch)  
**Last updated**: 2026-05-17  
**Applies to**: AI Terminal **iOS app (org.aiterminal.app)** and **Android app (org.aiterminal.app)**

---

# AI Terminal — Privacy Policy

*Last updated: 2026-05-17 · Applies to AI Terminal iOS app (org.aiterminal.app) and Android app (org.aiterminal.app)*

## Who We Are

AI Terminal lets you remotely control terminal sessions on your computer from your phone. This policy explains how we handle your data.

## Data We Collect

| Data | Purpose | Stored |
|------|---------|--------|
| Device identifier (Android ID / iOS identifierForVendor) | Identify your device for pairing persistence and 14-day free trial calculation | Relay server |
| Public key (E2E encryption) | Establish encrypted channel between your phone and computer; relay cannot decrypt | Relay server + paired computer daemon |
| Device name | Display in device management UI (e.g. "Xiaomi 13 Pro", "iPhone 15") | Paired computer daemon + local device |
| Push token (FCM on Android / APNs on iOS) | Wake your computer via push notification when offline | Relay server |
| Subscription status | Validate Google Play (Android) / App Store (iOS) subscription | Relay server |

## Optional Telemetry & Feedback (Opt-in)

The following data is collected **only if you enable it** in *Settings → Privacy*. All three toggles are **OFF by default**; first-launch consent dialog respects your choice (declining keeps everything off).

| Data | Purpose | Processor | Region |
|------|---------|-----------|--------|
| Anonymous usage events (DAU, session length, feature use counters — no input content) | Understand how features are used to prioritize improvements | Google Firebase Analytics | Google global infrastructure |
| Crash reports (stack trace, device state, sanitized — sensitive paths/keys/IPs scrubbed before send) | Identify and fix crashes | Google Firebase Crashlytics | Google global infrastructure |
| User-submitted feedback (description, optional logs and screenshot, sanitized via 18+ regex client-side and again server-side) | Process user-reported bugs and suggestions | Our own feedback endpoint | Asia + Americas (low-latency multi-region) |

**Sanitization:** Before any logs or feedback text leaves your device, the client runs an 18-rule regex scrub that strips: API keys (Anthropic, OpenAI, Google, AWS, GitHub PATs), JWT tokens, file paths containing usernames, private network IPs, email addresses, phone numbers. The same scrub runs server-side as a second layer.

**Anonymity:** Telemetry uses a randomly generated install UUID (not Android ID / iOS identifierForVendor, not your device identifier). We do not link telemetry to your subscription or pairing identity. You can wipe and regenerate the install UUID at any time via *Settings → Privacy → Reset Telemetry ID*.

**Opt-out:** Toggle off in *Settings → Privacy* at any time. Past data submitted while opt-in cannot be retroactively recalled (technical limitation), but no further data will be sent.

## Data We Do NOT Collect

- **Terminal command content / AI conversation content** — End-to-end encrypted (X25519 + AES-256-GCM). Only your phone and paired computer can decrypt. Neither the relay server nor we can see them.
- **Personal identity** — We do not require account signup; we do not collect your name, email, phone number, or persistently log IP address (IP is only used for TCP connection setup).
- **Location** — No GPS or network location collected.
- **Contacts / SMS / call logs** — We don't request these permissions.
- **Advertising identifiers** — No ad SDKs integrated.

## Permission Usage

### Android Permissions

| Permission | Purpose |
|------------|---------|
| Camera (CAMERA) | Scan QR code on computer screen for first-time pairing. We do not record, upload, or store any camera content. |
| Media / Files (READ_MEDIA_IMAGES / READ_EXTERNAL_STORAGE) | Used when you actively select an image or file to upload. We only read files you explicitly choose. |
| Network (INTERNET / ACCESS_NETWORK_STATE) | Connect to relay server and your computer daemon. |
| WiFi (ACCESS_WIFI_STATE / CHANGE_WIFI_MULTICAST_STATE) | LAN auto-discovery of your computer daemon (mDNS), so you don't have to type IP. |
| Foreground Service (FOREGROUND_SERVICE / FOREGROUND_SERVICE_DATA_SYNC) | Background download service for large files, prevents Android from killing transfer. |
| Boot completed (RECEIVE_BOOT_COMPLETED) | Auto-reconnect after device reboot (you can disable in system settings). |
| Background (REQUEST_IGNORE_BATTERY_OPTIMIZATIONS / WAKE_LOCK) | Keep long connection alive for real-time push from computer. |

### iOS Permissions

| Permission (Info.plist key) | Purpose |
|-----------------------------|---------|
| NSCameraUsageDescription | Scan QR code on computer screen for first-time pairing. We do not record, upload, or store any camera content. |
| NSPhotoLibraryUsageDescription | Used when you actively select an image or file to upload. We only access files you explicitly choose. |
| NSFaceIDUsageDescription | Optional biometric authentication to protect app access. Biometric data never leaves your device (processed by iOS Secure Enclave only). |
| APNs push notification (UserNotifications) | Wake your computer via Apple Push Notification service when offline. Functionally equivalent to FCM on Android. |
| iOS Keychain | Store pairing keys and credentials securely. Equivalent to Android Keystore. Data protected by iOS hardware security. |

**Note on encryption export compliance:** `ITSAppUsesNonExemptEncryption` is set to `false` in the app. The app uses standard HTTPS and platform-provided encryption APIs (iOS CommonCrypto / Security framework), which qualify for the encryption exemption under U.S. Export Administration Regulations.

## Data Sharing

We do **NOT** share your data with advertisers, data brokers, or insurers.

**Subprocessors** (only if you opt in to telemetry/crash reports):

- **Google Firebase** — Analytics and Crashlytics events. Subject to [Google's Privacy Policy](https://policies.google.com/privacy). You can opt out anytime in *Settings → Privacy*.
- **Apple APNs** (iOS) — Push notification delivery. Subject to [Apple's Privacy Policy](https://www.apple.com/legal/privacy/). Token is used only for notification delivery.
- **Our feedback endpoint** — only the bug reports you explicitly submit. Stored on access-controlled servers, retained 90 days then auto-purged.

Exception: When legally required (e.g. court subpoena), we will disclose the minimum required by law.

## Third-Party Services

| Service | Purpose | Their Privacy Policy |
|---------|---------|----------------------|
| Google Play Services / FCM (Android) | Push notifications | [policies.google.com/privacy](https://policies.google.com/privacy) |
| Apple APNs (iOS) | Push notifications | [apple.com/legal/privacy](https://www.apple.com/legal/privacy/) |
| Google Play Billing (Android) | Subscription payment | [policies.google.com/privacy](https://policies.google.com/privacy) |
| App Store / StoreKit (iOS) | Subscription payment | [apple.com/legal/privacy](https://www.apple.com/legal/privacy/) |
| Cronet / URLSession | HTTP client (Android: Cronet; iOS: URLSession — local library, no independent service) | N/A |

## Data Retention

- Device ID + public key: Records on relay server are auto-cleaned within 90 days after you delete the app.
- Local data (Android SharedPreferences / iOS UserDefaults + Keychain): Deleted when you uninstall the app. Keychain data may persist across reinstalls on iOS — you can clear it via *Settings → Reset All Data*.
- Push token (FCM / APNs): Auto-invalidated by Google / Apple when you uninstall.

## Children's Privacy

This app is not intended for children under 13. We do not knowingly collect data from children.

## Your Rights

- **Access**: View your device ID in the app's "Manage Devices" page.
- **Delete**: Uninstalling the app clears local data; contact us (email) to remove records on the relay server.
- **Decline**: You may deny any permission, but features (e.g. QR pairing, file transfer) will be unavailable.

## Policy Updates

This policy may be updated. Significant changes will be notified in-app. Continued use after updates implies consent.

## Contact

For questions or data requests: [contact@ai-terminal.org](mailto:contact@ai-terminal.org)
