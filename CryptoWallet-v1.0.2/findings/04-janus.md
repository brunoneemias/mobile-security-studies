# 04 — Janus Vulnerability (CVE-2017-13156)

## Status: ✅ Not Vulnerable

---

## What was checked

Whether the APK is susceptible to the Janus vulnerability, which affects apps signed **exclusively with v1** (JAR signing).

---

## Command Used

```bash
apksigner verify --verbose CryptoWallet-v1.0.2.apk | grep "v1 scheme\|v2 scheme"
```

## Result

```
Verified using v1 scheme (JAR signing): true
Verified using v2 scheme (APK Signature Scheme v2): true
```

Since the APK is signed with **v2 in addition to v1**, devices running Android 7.0+ will validate the v2 signature, making it **not vulnerable** to Janus.

---

## What is Janus?

The Janus vulnerability (CVE-2017-13156) allows an attacker to prepend a malicious DEX file to a signed APK without invalidating its v1 signature. This enables:

- Replacing a legitimate app with a trojaned version
- Bypassing the signature verification on the Android package manager

**Condition for exploitation:** The app must be signed only with v1 AND installed on Android 5.0–8.0 (API 21–26).

---

## Vulnerability Matrix

| Signing | Android < 7.0 | Android 7.0+ |
|---------|--------------|--------------|
| v1 only | ⚠️ Vulnerable | ⚠️ Vulnerable |
| v1 + v2 | ⚠️ Vulnerable* | ✅ Safe |
| v2 only | ✅ Safe | ✅ Safe |

*On Android < 7.0, v2 is ignored and only v1 is checked.

---

## Recommendation

No action needed for the current target audience. If support for Android < 7.0 is required, consider dropping v1 entirely or documenting the accepted risk.

---

## References

- [CVE-2017-13156](https://www.cvedetails.com/cve/CVE-2017-13156/)
- [Android Security Bulletin — December 2017](https://source.android.com/docs/security/bulletin/2017-12-01)
