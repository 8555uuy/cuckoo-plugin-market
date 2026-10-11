# cuckoo-plugin-market

Cuckoo Code 插件市场的**目录源**（curated `plugins.json`）。

## 这是什么

Cuckoo Code 客户端的「插件市场」页从这里拉取插件列表。
数据由 GitHub Actions **每日自动同步**（扫描 `topic:cuckoo-plugin` 的仓库）。

## 数据源

- **唯一真相源**：GitHub topic `cuckoo-plugin`
- 想上架？给你的仓库打上 `cuckoo-plugin` topic，推送后次日自动出现
- 想更快？提 Issue 或直接 PR 改 `plugins.json`

## plugins.json 结构

```
{
  "name": "cuckoo-plugin-market",
  "updated": "2026-10-11",
  "count": 8,
  "categories": { "platform": { "en": "Platform", "zh": "平台接入" }, ... },
  "plugins": [
    {
      "id": "owner/repo",
      "name": "插件名",
      "description": "简介",
      "category": "platform",
      "version": "1.0.0",
      "minAppVersion": "0.8.8",
      "stars": 1,
      "cover": "封面图 URL",
      "screenshots": ["截图 URL"],
      "defaultBranch": "main",
      "url": "https://github.com/owner/repo"
    }
  ]
}
```

## 封面图

优先级：`screenshots.json` → README 第一张图 → GitHub 自动 OpenGraph 图。
作者**什么都不做也有封面**。

想自定义截图，在仓库根加 `screenshots.json`：
```json
{ "screenshots": ["assets/demo-1.png", "https://.../demo-2.png"] }
```

## 分类

`platform` / `tools` / `ui` / `agents` / `skills` / `workflow` / `fun` / `other`
（脚本按仓库名+描述关键词自动归类）

## 本地重新生成

```bash
node scripts/sync-market.mjs --out plugins.json
```
