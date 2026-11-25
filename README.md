# DSHA Native Runtime (Android)

Android 原生运行时包，供 DSHA 在无 root 的 arm64 设备上运行 DeepSeek Harness 的 Node 树使用。
本仓库**只做分发与说明**：不含 App 源码、模块化方案或内部记录。

## 当前版本

- Release：`r1`
- 资产：`pkg-r1.zip`，120,889,177 B
- SHA-256：`35701db4231153200cd61b740090ecf88e98f75f1a23e5e60c4e1f3bf348c489`
- DSH：`0.2.2-rc.1`
- dshRuntime：`c1bd68330a10776f304a92a19d8f82c184c1abf523275a9e28dbb2c2e764e4fe`

## 包里有什么

- 打过 Android 补丁的 DSH 树、依赖库、根证书、内置插件
- **不含** `libnode.so` / `librg.so`：Android 只允许执行宿主 APK 的 `nativeLibraryDir`，这两个文件由 App 提供

## 校验

```bash
sha256sum pkg-r1.zip
# 35701db4231153200cd61b740090ecf88e98f75f1a23e5e60c4e1f3bf348c489
```

## 使用

解压到应用私有目录，按 `native-runtime.json` 的 `entry` / `verifiedFiles` 逐文件校验后再启动。
不要直接执行包内 ELF。细节见 [docs/native-runtime.md](docs/native-runtime.md)。

## 状态

- 实验性质，未做完整真机验收；不保证可用或安全，不要用于敏感数据。
- 欢迎开 issue / PR 折腾；也可以直接 fork。

## License

MIT，见 [LICENSE](LICENSE)。包内第三方组件许可见压缩包内 `licenses/` 与 [NOTICE.md](NOTICE.md)。
