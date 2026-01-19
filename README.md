# Arthas Website (Hugo + Decap CMS)

这个子项目用于快速搭建 Arthas 官网（下载页 + 内容管理）。

## What

- 静态站点生成：Hugo
- 内容管理：Decap CMS（原 Netlify CMS）
- 目标：提供 Arthas 的 Windows / macOS 下载入口，并且让非开发同学也能在后台更新下载链接/版本信息。

## Why

- Hugo 构建快、部署简单（Netlify/Cloudflare Pages/GitHub Pages 都行）。
- Decap CMS 能直接把内容/数据写回 Git 仓库，改动可审计、可回滚。

## How

### 本地开发

1) 安装 Hugo（建议 Extended 版本）
2) 在本目录运行：

```bash
hugo server -D
```

站点默认在 `http://localhost:1313/`。

> 小提醒：如果你本机还没装 Hugo，会看到 `hugo: The term 'hugo' is not recognized`，先装一下就好啦～

### CMS（Decap）后台入口

启动站点后访问：

`/admin/`

本项目默认使用 Netlify 的 `git-gateway`（需要在 Netlify 控制台启用 Identity + Git Gateway）。

如果你更想用 GitHub OAuth（不依赖 Netlify Identity），可以把 `static/admin/config.yml` 里的 backend 改成 `github` 并填写 `repo`。

### 下载数据维护

下载按钮来自 `data/downloads.yaml`，可以：

- 直接改文件提交
- 或用 `/admin/` 后台改（推荐）

### Netlify 部署

把这个目录作为 Netlify site 的 root：

- Build command: `hugo --gc --minify`
- Publish directory: `public`

也可以直接用 `netlify.toml`（已提供）。

#### 用 Decap CMS（Netlify Identity）需要做的额外设置

1) Netlify Site settings → Identity：Enable
2) Identity → Services：Enable `Git Gateway`
3) （推荐）Identity → Registration：设置邀请制/白名单，避免公开注册
4) 部署完成后访问：`https://<your-site>.netlify.app/admin/`

如果你不想依赖 Netlify Identity，请把 `static/admin/config.yml` 的 backend 改为 `github` 并配置 OAuth（需要额外创建 GitHub OAuth App）。
