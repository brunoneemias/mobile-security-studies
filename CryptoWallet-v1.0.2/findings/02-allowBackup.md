# 02 — android:allowBackup

## Status: ⚠️ Vulnerable — Medium Severity

---

## What was checked

Whether `android:allowBackup="true"` is present in the `AndroidManifest.xml`, allowing internal app data to be extracted via ADB backup.

---

## Command Used

```bash
grep -i "allowBackup" output_dir/AndroidManifest.xml
```

## Result

```xml
android:allowBackup="true"
```

The flag is **present and enabled**.

---

## Why it matters

With `allowBackup="true"`, anyone with physical access to the device and ADB enabled can extract the app's internal data:

```bash
adb backup -noapk com.cryptowallet.app
```

This can expose:

- `SharedPreferences` files (may contain tokens, keys, settings)
- SQLite databases (transaction history, user data)
- Internal files stored in the app's private directory

For a crypto wallet app, this is especially critical as it could expose sensitive financial data or authentication secrets.

---

## Recommendation

Set `android:allowBackup="false"` in the `AndroidManifest.xml`:

```xml
<application
    android:allowBackup="false"
    ...>
```

If backup is needed for legitimate purposes, use `android:fullBackupContent` with an exclusion rules file to block sensitive data.

---

## References

- [Android Docs — android:allowBackup](https://developer.android.com/guide/topics/manifest/application-element#allowbackup)
- [OWASP MASVS — MSTG-STORAGE-8](https://mas.owasp.org/MASVS/controls/MASVS-STORAGE-8/)
