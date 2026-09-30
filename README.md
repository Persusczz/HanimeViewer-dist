# HanimeViewer 更新分发仓库

本仓库**只放构建产物**（`update.json` 与各版本 APK），**不含任何源码**。
源码在私有仓库中，不对公众开放。

## 这个仓库是干什么的

应用内的「检查更新」直接读取本仓库根目录的 `update.json`：

| 通道 | 地址 |
|---|---|
| GitHub Pages | `https://wanttosleep2005.github.io/HanimeViewer-dist/update.json` |
| GitHub raw | `https://raw.githubusercontent.com/Wanttosleep2005/HanimeViewer-dist/main/update.json` |
| jsDelivr | `https://cdn.jsdelivr.net/gh/Wanttosleep2005/HanimeViewer-dist@main/update.json` |

各版本的安装包放在 [Releases](../../releases)，命名固定为
`Han1meViewer-v<版本号>.apk`。

## 为什么源码和产物要分开

源码仓库是**私有**的，而私有仓库的 raw / jsDelivr / Pages / Releases
对外**全部需要鉴权** —— 客户端没法匿名拉取。
于是把两者拆开：**源码留私有仓库，产物放这个公开仓库**。

## 发布流程

由本地脚本发布（本仓库**不使用 GitHub Actions**）：
`build/publish_release.py`（在源码仓库里），步骤为
构建 APK → 创建 Release 并上传 → 更新本仓库的 `update.json`。
