# Native runtime package contract

## Layout

- `native-runtime.json` — manifest: entry, verifiedFiles, patches, plugins, archive digest
- `lib/` — shared libraries (libc++, OpenSSL, ICU, SQLite, zlib, …)
- `etc/tls/cert.pem` — root certificates
- `licenses/` — third-party copyright files
- `node_modules/` — DSH tree with Android patches applied
- `dsha-plugins/` — managed built-in plugins
- `dsha-tools/dsha-app.cjs` — host bridge helper

## Host requirements

- Android arm64, API 30+
- `libnode.so` and `librg.so` provided by the host APK in `nativeLibraryDir`
- Extract into app-private storage, verify every file in `verifiedFiles`, then start `entry`

## Integrity

- Archive: see `native-runtime.lock.json`
- Per-file digests: `native-runtime.json` → `verifiedFiles`
- Refuse to start if any digest or the DSH runtime digest mismatches

## License

MIT for this repo. The archive contains third-party components; see `licenses/` and `NOTICE.md`.
