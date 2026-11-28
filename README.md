# IBLinker 发布仓库（IBLinker-publish）

本仓库存放 **IBLinker** Android App 的正式构建产物（APK），由源码仓库 `tansor/IBLinker` 的 `build.sh` 自动发布，供 App 内「设置 → 检查更新」拉取。

> 源码仓库：[tansor/IBLinker](https://github.com/tansor/IBLinker)

## 内容

- `IBLinker_release_YYYYMMDD_HHMM.apk`：每次发布的 APK（**仅保留最近 1 个版本**，旧版本自动清理）。
- `latest.json`：始终指向最新版本，字段如下：

```json
{
  "versionName": "20261123.1145",
  "versionCode": 202611231145,
  "downloadUrl": "https://raw.githubusercontent.com/tansor/IBLinker-publish/main/IBLinker_release_20261123_1145.apk",
  "fileName": "IBLinker_release_20261123_1145.apk",
  "releaseNotes": "自动构建发布",
  "publishedAt": "2026-11-23T11:45:00+08:00",
  "size": 20123456
}
```

## 版本规则

- `versionName` / 文件名：`yyyyMMdd.hhmm`（如 `20261123.1145`）
- `versionCode`：`yyyyMMddHHmm`（整数，如 `202611231145`）

## 自动更新机制

App 在「设置 → 检查更新」时匿名读取本仓库的 `latest.json`：

1. 若 app 版本已是最新 → 不下载。
2. 若本地已缓存最新 APK 且高于 app 版本 → 直接拉起安装（不重复下载）。
3. 否则下载最新 APK 并安装；本地始终只保留一个最新 APK。

## 手动安装

点击仓库中唯一的 `IBLinker_release_*.apk` 下载安装即可（需允许「安装未知应用」）。
