# 贡献说明

本仓库只接收赛道内容、来源与审阅数据。网站代码、工具实现和设计资源分别在 `site-www`、`site-knowledge` 与 `site-tools`。

## 提交前

1. 确认选题不与已有 `entityId` 重复；一条赛道的一个版本对应一个实体。
2. 为距离、爬升、方向、起点与路线版本找到可定位来源，记录 `sourceId`、URL 或 DOI、定位段与支持的结论。
3. 中英文都写成独立正文，不把机器翻译直接当英文成稿；两种语言的事实必须一致。
4. 没有可信爬升时保留 `null`，不要用 `0` 填平。地图锚点不得冒充轨迹。
5. 只使用确认可再分发的轨迹、图片或 Logo；否则记录官方链接并设 `geometryAccess` 为 `official-link` 或 `unavailable`。

## 审阅与状态

状态为 `draft`、`in-review`、`published`、`withdrawn`。新内容从 `draft` 开始，完成双语、来源与许可检查后进入 `in-review`。`published` 需要两种语言都有作者与审阅者，并存在 `approve` 审阅记录；`reviewedAt` 不能由格式化、翻译或重建自动填写。内容改变后必须重新审阅。

## 校验

在 `site-www` 运行内容校验和构建。校验器会检查双语配对、来源引用、几何许可、审阅日期与内容摘要。失败时修正内容，不绕过检查。

## 来源与礼貌

- 不复制官方赛道地图、Logo、GPX 或数据库，除非来源明确允许。
- 不把个人轨迹直接公开；先移除时间、设备、住址和起点附近的敏感位置，并取得授权。
- 纠错请指出具体段落、现有来源与建议来源。没有公开 Issue 地址时，不虚构邮箱或联系人。

---

# Contributing

This repository accepts route content, sources and review data only. Site code, tool implementations and design assets live in `site-www`, `site-knowledge` and `site-tools`.

Before submitting, check that the `entityId` is unique, locate sources for distance, elevation, direction, start point and course version, and write both languages independently. Keep unknown elevation as `null`, do not present a map anchor as a track, and only include geometry or images whose redistribution rights are confirmed.

New entities start as `draft`, move to `in-review` after bilingual and rights checks, and to `published` only with authors, reviewers and an `approve` review record in both languages. Re-run the `site-www` content validation and build after changes. Do not bypass a failed check.
