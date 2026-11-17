# 怎么让内容被 AI 引用（GEO 实操）

> **一句话答案**：AI 引用的是"**结构清晰、可被抓取、答案在前**"的页面。做法是：自有静态站 + GitHub 镜像 + 结构化数据 + 放行爬虫，然后反复测量。

## 什么叫 GEO

GEO（Generative Engine Optimization）＝让你的内容出现在 AI 搜索的回答和引用里。
和 SEO 的区别：SEO 争排名，GEO 争"被摘进去当答案"。

## 实测数据（2026-11-17，20 条 query）

在 AI 搜索（秘塔）上跑 20 条目标 query：

| 指标 | 结果 |
|---|---|
| 我方域名被引用 | **0 次** |
| 被引用的同行源 | `github.com/easychen/…`（开源方法论） |
| 高频引用平台 | bilibili、cnblogs、豆瓣、搜狐、腾讯新闻、opcwiki.net |
| 我方品牌词出现 | 1/20（且指的是上游方法论，不是我们） |

结论：**不是内容不够，是内容不在 AI 的检索层里。**

## 四件事，按顺序做

### 1. 自有静态站（必须）

- 纯静态 HTML，不要 SPA——多数 AI 爬虫不执行 JS
- 每页只回答一个问题，第一段就是结论
- 每页 500–1500 字，带数据、步骤、坑

### 2. GitHub 镜像（最快见效）

基线里被引用的就是 GitHub 的 markdown。做法：
- 一个公开仓库，每个问题一个 `.md`
- README 做目录
- 英文文件名（URL 更干净）

### 3. 放行爬虫 + 给目录

```
/robots.txt   → 允许 GPTBot / OAI-SearchBot / PerplexityBot / ClaudeBot /
                Bytespider / Baiduspider / Bingbot
/llms.txt     → 给 AI 的目录：每个链接回答什么问题
/sitemap.xml  → 提交到百度、Bing、Google 三个站长平台
```

### 4. 结构化数据

每页加 `Article` + `FAQPage` 的 JSON-LD，让 AI 直接拿到"问题 + 答案"。

## 怎么衡量

固定 20 条 query，每两周跑一次同样的测试，记录：

- 是否出现我方品牌词
- 是否引用我方域名
- 引用源里出现了哪些新平台

只有重复测量，才能知道改动有没有用。

## 常见误区

- 以为发在语雀/飞书就"有知识库了"——登录墙，AI 抓不到
- 以为堆关键词就行——AI 摘的是答案段落，不是关键词密度
- 只发平台不发自有站——流量和引用都归平台

## 延伸阅读

- [如何建立个人品牌](personal-brand.md)
- [AI 视频流水线怎么做](ai-video-pipeline.md)
