---
name: wechatsync
description: Publish and sync articles to 27+ content platforms (Zhihu, Juejin, CSDN, Toutiao, Weibo, Xiaohongshu, Bilibili, WordPress, etc.) from Markdown or HTML files. Use when the user wants to publish, sync, cross-post, or distribute articles to Chinese content platforms, blogging sites, or self-hosted blogs. Also use when checking platform login status or extracting articles from web pages.
---

# WechatSync

Publish and sync articles to 27+ content platforms from the command line.

## Prerequisites

1. Install CLI: `npm install -g @wechatsync/cli`
2. Install Chrome extension: https://www.wechatsync.com/#install
3. Enable "MCP Connection" in extension settings and get your Token
4. Set environment variable: `export WECHATSYNC_TOKEN="your-token"`
5. Log in to target platforms in your browser

## Commands

### Sync Articles

```bash
# Sync to a single platform
wechatsync sync article.md -p juejin

# Sync to multiple platforms
wechatsync sync article.md -p juejin,zhihu,csdn

# Specify title
wechatsync sync article.md -p juejin -t "My Article Title"

# Add cover image
wechatsync sync article.md -p juejin --cover ./cover.png

# Dry run (preview without syncing)
wechatsync sync article.md -p juejin --dry-run
```

### List Platforms

```bash
# List all platforms
wechatsync platforms

# Show login status
wechatsync platforms --auth
```

### Check Auth Status

```bash
# Check all platforms
wechatsync auth

# Check a single platform
wechatsync auth zhihu
```

### Extract Article

```bash
# Extract from current browser page
wechatsync extract

# Save to file
wechatsync extract -o article.md
```

## Supported Platforms

| Platform | ID | Category |
|----------|----|----------|
| Zhihu (知乎) | zhihu | Social |
| Juejin (掘金) | juejin | Tech |
| CSDN | csdn | Tech |
| Jianshu (简书) | jianshu | General |
| Toutiao (头条号) | toutiao | General |
| Weibo (微博) | weibo | Social |
| Bilibili (B站) | bilibili | General |
| Xiaohongshu (小红书) | xiaohongshu | Social |
| Baijiahao (百家号) | baijiahao | General |
| WeChat (微信公众号) | weixin | Social |
| Yuque (语雀) | yuque | Tech |
| Douban (豆瓣) | douban | General |
| Sohu (搜狐号) | sohu | General |
| Xueqiu (雪球) | xueqiu | Finance |
| Woshipm (人人都是产品经理) | woshipm | Product |
| Dayu (大鱼号) | dayu | General |
| Yidian (一点号) | yidian | General |
| 51CTO | 51cto | Tech |
| Sohu Focus (搜狐焦点) | sohufocus | Real Estate |
| iMooc (慕课网) | imooc | Tech |
| OSChina (开源中国) | oschina | Tech |
| SegmentFault | segmentfault | Tech |
| Cnblogs (博客园) | cnblogs | Tech |
| X (Twitter) | x | Global |
| Eastmoney (东方财富) | eastmoney | Finance |
| SMZDM (什么值得买) | smzdm | General |
| Netease (网易号) | netease | General |
| WordPress | wordpress | Self-hosted |
| Typecho | typecho | Self-hosted |

## Image Handling

- Local images are automatically uploaded to the target platform's CDN
- Cross-platform image re-hosting is automatic
- Supported formats: PNG, JPG, GIF, WebP, SVG

## Article Format

Supports Markdown and HTML files. For Markdown, the title is extracted from:
1. YAML front matter `title` field
2. First `# heading`

## Examples

User: "Sync this article to Juejin and Zhihu"
Steps:
1. Check login status: `wechatsync platforms --auth`
2. Sync: `wechatsync sync <file> -p juejin,zhihu`

User: "Which platforms am I logged into?"
Run: `wechatsync platforms --auth`

User: "Extract the current article from browser"
Run: `wechatsync extract -o article.md`

User: "把这篇文章同步到掘金和知乎"
Steps:
1. `wechatsync platforms --auth`
2. `wechatsync sync <file> -p juejin,zhihu`
