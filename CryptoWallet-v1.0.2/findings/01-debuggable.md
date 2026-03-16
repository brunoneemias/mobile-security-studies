# 01 — android:debuggable

## Status: ✅ Secure

---

## What was checked

Whether the APK was compiled with `android:debuggable="true"` in the `AndroidManifest.xml`.

---

## Command Used

```bash
apktool d CryptoWallet-v1.0.2.apk -o output_dir
grep -i "debuggable" output_dir/AndroidManifest.xml
```

## Result

The flag was **not present** in the manifest, which means it defaults to `false`. This is the correct behavior for a release build.

---

## Why it matters

If `android:debuggable="true"` is set in a production app, an attacker with physical or ADB access to the device can:

- Attach a debugger to the running process
- Inspect memory and extract sensitive data (keys, tokens, credentials)
- Bypass security controls

---

## Recommendation

No action needed. Ensure the production pipeline always uses release builds with this flag absent or explicitly set to `false`.

---

## References

- [Android Docs — android:debuggable](https://developer.android.com/guide/topics/manifest/application-element#debug)
- [OWASP MASVS — MSTG-RESILIENCE-2](https://mas.owasp.org/MASVS/controls/MASVS-RESILIENCE-2/)
