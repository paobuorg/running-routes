# 跑起来 · 赛道内容

[English](README.en.md) · 中文

本仓库保存跑起来主站使用的赛道档案、双语正文、来源与审阅数据。它是纯内容仓库，不包含网站运行代码、`package.json`、`node_modules` 或构建产物。

## 当前状态

- 首发 16 条赛道：波士顿、UTMB，以及东京、伦敦、柏林、芝加哥、纽约、悉尼、开普敦、北京、上海、西部各州、硬石、香港 100、狂人对角线和巨人之旅。
- 16 条路线已于 2026-10-28 完成 **AI 辅助编辑审阅**并发布（`published`，双语 `approve` 记录与匹配 digest）。审阅者是 `runmap-editorial`，明确标注为 AI 辅助，不是独立或专业审阅；首发路线清单已覆盖 16/16。
- 项目没有远程仓库、正式 Issue 入口或已部署网站。本仓库不声称已经过专业审阅。

## 内容范围

主站只介绍固定核验版本的经典公路马拉松与越野超马赛道，不维护报名、当届日期、即时成绩、商品价格或实时通行状态。赛道版本使用 `courseVersion` 固定，例如 `2024-baa-published-course`，不能把某一年路线当成永久唯一路线。

## 目录

```text
data/entities/{slug}.json          共享事实、赛道版本、来源引用与几何许可
data/sources/{sourceId}.json       来源、定位与支持的结论
data/contributors/{personId}.json  公开作者与审阅者身份
data/reviews/{slug}.{locale}.json  通过审阅后记录内容摘要与决定
content/zh-CN/{slug}.md            中文正文与 frontmatter
content/en/{slug}.md               英文正文与 frontmatter
assets/                            可再分发的轨迹与小型素材
```

`entityId` 形如 `route:boston`，`slug` 使用英文短横线。中英文通过 `entityId` 配对，事实数值只保存在 `data/entities/` 一处。

## 数据口径

- 距离与爬升必须有可定位来源；没有可信爬升时 `elevationGainMeters` 为 `null`，不能填 `0`。
- `mapAnchor` 只是地球定位点，不冒充起点或完整轨迹。
- `geometryAccess` 取 `redistributable`、`official-link` 或 `unavailable`。只有 `redistributable` 才能把轨迹纳入仓库并提供下载，且必须记录许可、署名与来源。
- 赛道页面可见不代表轨迹可以转载。官方页面可支持事实核验，但不自动授予图片、Logo、GPX 或数据库的复制权。
- 来源更新后，中英文正文都要重新核对；只有经过实质审阅才能填写 `reviewedAt`。

## 本地使用

本站内容由 `site-www` 构建时读取。六个工程放在同一父目录时，默认路径会自动指向本仓库；也可以在网站仓库中通过 `ROUTES_CONTENT_DIR` 指定路径。本仓库本身没有安装或构建命令。

预览方式见 [site-www](../site-www/README.md)。构建会校验双语配对、来源、许可、审阅日期与内容摘要，校验失败会阻止发布。

## 许可与纠错

- 新写正文：CC BY 4.0，署名「跑起来 RunUp」。
- 轨迹几何、图片与第三方素材：按各来源条件，逐项记录在实体或来源文件中；没有确认权利的内容不进入仓库。
- 网站代码：MIT，位于三个 `site-*` 仓库。

发现事实或来源问题时，请在托管仓库建立后通过 Issue 或 Pull Request 说明具体段落、来源与建议修改。当前没有可用的公开 Issue 地址，不提供虚构邮箱。贡献流程见 [CONTRIBUTING.md](CONTRIBUTING.md)。

最后核对日期：2026-10-28。
