# Evergarden 项目总结

## 项目概述

个人独立开发者主页，日系清新风格，使用 Astro + Tailwind CSS 构建，部署于 Cloudflare Pages。

- 线上地址：https://evergarden-czt.pages.dev/
- GitHub 仓库：https://github.com/mortis-sys/Evergarden

## 技术栈

| 技术 | 用途 |
|------|------|
| Astro v6 | 静态网站框架 |
| Tailwind CSS v4 | 样式框架 |
| Git | 版本控制 |
| GitHub | 代码托管 |
| Cloudflare Pages | 自动部署 |

## 项目结构

```
personal-site/
├── src/
│   ├── assets/
│   │   └── bg.png          # 背景图
│   ├── pages/
│   │   └── index.astro     # 首页（单页多界面切换）
│   └── styles/
│       └── global.css      # 全局样式（Inter字体 + Tailwind + 界面切换动画）
├── .mcp.json               # MCP 服务器配置
├── astro.config.mjs
├── package.json
└── tsconfig.json
```

## 当前实现进度

### 导航系统
- 固定顶部导航栏，左侧标题「雾籽米的 Evergarden」，右侧 6 个导航按钮
- 向下滚动时自动隐藏，向上滚动时显示（`duration-500 ease-in-out`）
- 点击按钮切换主界面，当前页面高亮

### 6 个界面模块
| 导航 | 内容 |
|------|------|
| 首页 | Hero（四句诗紧凑版）+ 关于我 + 音乐播放 + 项目预览 + 照片墙预览 + 杂谈预览 |
| 项目 | 4 张项目卡片（游戏 / QQ Agent / AI 实验 / 本站） |
| 杂谈 | 3 篇带日期标签的文章 |
| 照片墙 | 6 张图片占位格 |
| 动漫 | 4 部动画推荐 |
| 游戏交流 | 4 个话题卡片 |

### 首页模块详情
- Hero 区：`min-h-[60vh]`，四句诗 `max-w-xl` 紧凑居中
- 关于我：头像 + 介绍 + AI/Game Dev/UI Design 标签
- 音乐播放：播放器 UI（占位，后续对接 API）
- 项目：4 卡片横排，悬停上移效果
- 照片墙：6 宫格 emoji 占位
- 杂谈：3 条目带分类标签和日期

### 设计语言
- 毛玻璃质感：`bg-white/70 + backdrop-blur-xl`
- 卡片圆角：`rounded-3xl`
- 渐变：`from-blue-500 via-violet-500 to-blue-400`
- 蓝白紫配色

## 已安装的 MCP 服务器

配置文件：`personal-site/.mcp.json`

| MCP | 命令 | API Key |
|-----|------|---------|
| Context7 | `npx @upstash/context7-mcp@latest` | 不需要（免费） |
| GitHub | `npx @modelcontextprotocol/server-github` | 需要 `GITHUB_TOKEN` |
| Cloudflare | `npx cloudflare-mcp-server` | 需要 `CLOUDFLARE_API_TOKEN` |
| Playwright | `npx @playwright/mcp@latest`（全局已配置） | 不需要 |

### Windows 配置要点

- 命令必须用 `cmd` + `/c` 包裹
- 配置文件必须是项目根目录的 `.mcp.json`
- 路径使用正斜杠（forward slashes）

## 已安装的 Claude Code Skills（16 个）

| Skill | 来源 | 用途 |
|-------|------|------|
| frontend-design | anthropics/skills | 前端 UI 设计 |
| find-skills | vercel-labs/skills | 搜索更多 Skill |
| brainstorming | obra/superpowers | 头脑风暴 |
| dispatching-parallel-agents | obra/superpowers | 并行任务分发 |
| executing-plans | obra/superpowers | 执行计划 |
| finishing-a-development-branch | obra/superpowers | 完成开发分支 |
| receiving-code-review | obra/superpowers | 接收代码审查 |
| requesting-code-review | obra/superpowers | 请求代码审查 |
| subagent-driven-development | obra/superpowers | 子代理驱动开发 |
| systematic-debugging | obra/superpowers | 系统化调试 |
| test-driven-development | obra/superpowers | 测试驱动开发 |
| using-git-worktrees | obra/superpowers | Git worktree 工作流 |
| using-superpowers | obra/superpowers | Superpowers 总入口 |
| verification-before-completion | obra/superpowers | 完成前验证 |
| writing-plans | obra/superpowers | 编写计划 |
| writing-skills | obra/superpowers | 编写自定义 Skill |

## 常用命令

```bash
# 启动开发服务器
npm run dev

# 构建
npm run build

# 预览构建结果
npm run preview

# 查看 MCP 状态（在 Claude Code 中）
/mcp

# 查看诊断
/doctor
```

## 网络代理说明

当前环境配置了 HTTP 代理 `127.0.0.1:7890`（Clash/V2Ray）用于访问外网。
- git 走代理，但 SSL 握手有问题，安装 Skill 时需临时取消代理
- 直连 GitHub 可用，npx/npm 也可用

## 下一阶段计划

1. Hero 区进一步高级化
2. 页面组件化
3. 动态背景
4. 动画系统
5. 字体系统
6. Apple 风 UI 统一
7. 游戏展示区
8. 更完整的个人主页结构

## 学习目标

以"边做边学"方式掌握：
- Tailwind CSS / Astro / 现代 UI 设计
- 响应式开发 / 组件化开发 / 动效设计
- 独立开发者网站设计
