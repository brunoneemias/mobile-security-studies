# 03 — APK Signature Scheme v2

## Status: ✅ Secure

---

## What was checked

Whether the APK is signed using the APK Signature Scheme v2 (or higher), which provides stronger integrity guarantees than the legacy v1 (JAR signing) scheme.

---

## Command Used

```bash
apksigner verify --verbose CryptoWallet-v1.0.2.apk
```

## Result

```
Verified using v1 scheme (JAR signing): true
Verified using v2 scheme (APK Signature Scheme v2): true
Verified using v3 scheme (APK Signature Scheme v3): false
```

The APK is signed with **both v1 and v2**, meaning it is protected on Android 7.0+ while maintaining compatibility with older devices.

---

## Why it matters

APK Signature Scheme v2 covers the entire APK file (including the ZIP structure), making it significantly harder for an attacker to tamper with the package without invalidating the signature.

v1 alone leaves gaps in ZIP metadata that can be exploited (see finding 04 — Janus vulnerability).

---

## Recommendation

No action needed. Optionally consider adding v3 signing to support key rotation on Android 9+.

---

## References

- [Android Docs — APK Signature Scheme v2](https://source.android.com/docs/security/features/apksigning/v2)
- [apksigner documentation](https://developer.android.com/tools/apksigner)
