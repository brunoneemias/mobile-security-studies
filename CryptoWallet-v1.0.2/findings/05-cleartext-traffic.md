# 05 — android:usesCleartextTraffic

## Status: ✅ Secure

---

## What was checked

Whether the APK allows unencrypted (HTTP) network traffic via the `android:usesCleartextTraffic="true"` flag or a permissive Network Security Configuration.

---

## Commands Used

```bash
grep -i "cleartextTraffic\|networkSecurityConfig" output_dir/AndroidManifest.xml
find output_dir/res -name "network_security_config.xml"
```

## Result

The flag `android:usesCleartextTraffic` was **not present** in the manifest, and no permissive Network Security Config was found.

On Android 9+ (API 28+), cleartext traffic is **blocked by default** when this flag is absent.

---

## Why it matters

If cleartext traffic is allowed, the app can send and receive data over plain HTTP, making it vulnerable to:

- **Man-in-the-Middle (MitM) attacks** — an attacker on the same network can intercept and modify traffic
- **Credential and token theft** — sensitive data transmitted in plaintext can be read directly
- **Session hijacking** — session tokens exposed in HTTP can be captured and reused

For a crypto wallet, transmitting any data in plaintext would be a critical risk.

---

## Recommendation

No action needed. Ensure future versions maintain this behavior and do not introduce cleartext exceptions in `network_security_config.xml`.

---

## References

- [Android Docs — Network Security Configuration](https://developer.android.com/privacy-and-security/security-config)
- [OWASP MASVS — MSTG-NETWORK-2](https://mas.owasp.org/MASVS/controls/MASVS-NETWORK-2/)
