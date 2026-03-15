# 📱 mobile-security-studies

> Personal notes and findings from my mobile security studies — Android APK analysis, tools and methodology.

---

## About

This repository is a personal diary of my studies in mobile security.  
Each folder contains a real analysis I performed, documenting the tools used, methodology, and findings — focused on learning and understanding common Android vulnerabilities.

> ⚠️ All APKs analyzed here were used strictly for educational purposes.

---

## Studies

| # | Target | Type | Date |
|---|--------|------|------|
| 01 | [CryptoWallet v1.0.2](./CryptoWallet-v1.0.2/) | Static Analysis | 2026-03 |

---

## Methodology

All static analyses follow this general flow:

1. Decompile APK with `apktool`
2. Inspect `AndroidManifest.xml` for misconfigurations
3. Verify signing schemes with `apksigner`
4. Check for known vulnerabilities (CVEs)
5. Document findings with severity and recommended fix

---

## Tools Used

- [apktool](https://apktool.org/) — APK decompilation
- [apksigner](https://developer.android.com/tools/apksigner) — Signature verification
- [jadx](https://github.com/skylot/jadx) — Java/Kotlin decompiler
- [MobSF](https://mobsf.github.io/Mobile-Security-Framework-MobSF/) — Automated analysis framework

---

## References

- [OWASP Mobile Top 10](https://owasp.org/www-project-mobile-top-10/)
- [Android Security Documentation](https://developer.android.com/privacy-and-security/security-tips)
- [CVE Details](https://www.cvedetails.com/)
