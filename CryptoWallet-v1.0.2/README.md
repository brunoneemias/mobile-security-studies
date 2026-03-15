# 🔐 CryptoWallet v1.0.2 — Static Security Analysis

> Android APK static analysis focused on common misconfigurations and signing vulnerabilities.

---

## Summary

| Field | Details |
|-------|---------|
| **Target** | CryptoWallet v1.0.2 |
| **Type** | Android APK |
| **Analysis Type** | Static |
| **Date** | March 2026 |
| **Tools** | apktool, apksigner |

---

## Findings Overview

| # | Check | Result | Severity |
|---|-------|--------|----------|
| 01 | [debuggable=false](./findings/01-debuggable.md) | ✅ Secure | — |
| 02 | [allowBackup=true](./findings/02-allowBackup.md) | ⚠️ Vulnerable | Medium |
| 03 | [Signature Scheme v2](./findings/03-signature-v2.md) | ✅ Secure | — |
| 04 | [Janus Vulnerability](./findings/04-janus.md) | ✅ Not Vulnerable | — |
| 05 | [Cleartext Traffic](./findings/05-cleartext-traffic.md) | ✅ Secure | — |

---

## Methodology

```
1. Decompile APK
   └── apktool d CryptoWallet-v1.0.2.apk -o output_dir

2. Inspect AndroidManifest.xml
   └── grep flags: debuggable, allowBackup, usesCleartextTraffic

3. Verify signing schemes
   └── apksigner verify --verbose CryptoWallet-v1.0.2.apk

4. Evaluate Janus exposure
   └── Check if only v1 signing is present
```

---

## Detailed Findings

See the [findings/](./findings/) folder for individual write-ups on each check.

---

## References

- [OWASP MASVS](https://mas.owasp.org/MASVS/)
- [CVE-2017-13156 — Janus Vulnerability](https://www.cvedetails.com/cve/CVE-2017-13156/)
- [Android Manifest Documentation](https://developer.android.com/guide/topics/manifest/manifest-intro)
