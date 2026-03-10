---
name: wechatsync
description: Publish and sync articles to 27+ content platforms (Zhihu, Juejin, CSDN, Toutiao, Weibo, Xiaohongshu, Bilibili, WordPress, etc.) from Markdown or HTML files. Use when the user wants to publish, sync, cross-post, or distribute articles to Chinese content platforms, blogging sites, or self-hosted blogs. Also use when checking platform login status or extracting articles from web pages.
allowed-tools: Bash(wechatsync *)
---

# WechatSync

Publish and sync Markdown/HTML articles to 27+ content platforms via CLI.

## Prerequisites

1. Install CLI: `npm install -g @wechatsync/cli`
2. Install Chrome extension: https://www.wechatsync.com/#install
3. Enable "MCP Connection" in extension settings, get Token
4. Set env: `export WECHATSYNC_TOKEN="your-token"`
5. Log in to target platforms in browser

## Commands

### Sync

```bash
wechatsync sync article.md -p juejin              # single platform
wechatsync sync article.md -p juejin,zhihu,csdn   # multiple platforms
wechatsync sync article.md -p juejin -t "Title"   # custom title
wechatsync sync article.md -p juejin --cover ./cover.png  # cover image
wechatsync sync article.md -p juejin --dry-run     # preview only
```

### Platforms & Auth

```bash
wechatsync platforms          # list all platforms
wechatsync platforms --auth   # show login status
wechatsync auth zhihu         # check single platform
```

### Extract

```bash
wechatsync extract              # extract from current browser page
wechatsync extract -o article.md  # save to file
```

## Platform IDs

zhihu, juejin, csdn, jianshu, toutiao, weibo, bilibili, xiaohongshu, baijiahao, weixin, yuque, douban, sohu, xueqiu, woshipm, dayu, yidian, 51cto, sohufocus, imooc, oschina, segmentfault, cnblogs, x, eastmoney, smzdm, netease, wordpress, typecho

## Notes

- Images auto-uploaded to target platform CDN (PNG, JPG, GIF, WebP, SVG)
- Markdown title extracted from front matter `title` or first `# heading`
- Articles sync as **drafts** by default — user reviews before publishing

## Workflow

1. Check login: `wechatsync platforms --auth`
2. Sync: `wechatsync sync <file> -p <platform1>,<platform2>`
3. Report results with draft URLs

Example prompts:
- "Sync this article to Juejin and Zhihu"
- "Which platforms am I logged into?"
- "Extract the article from browser and save it"
- "把这篇文章同步到掘金和知乎"
