# Arthas Website (Hugo + Decap CMS)

这个子项目用于快速搭建 Arthas 官网（下载页）。

## What

- 静态站点生成：Hugo
- 目标：提供 Arthas 的 Windows / macOS 下载入口（纯静态，适合挂在 Nginx 上）

## Why

- Hugo 构建快、部署简单（Netlify/Cloudflare Pages/GitHub Pages 都行）。
- 纯静态 + Nginx：部署与运维成本最低、稳定性最好。

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

本仓库目前以“纯静态官网”为目标，不需要后台登录/写库。
（目录里保留了 `/admin/` 的静态文件，后续如果你想再启用 CMS 再说也行。）

### 下载数据维护

下载按钮来自 `data/downloads.yaml`，可以：

- 直接改文件提交

### Netlify 部署

把这个目录作为 Netlify site 的 root：

- Build command: `hugo --gc --minify`
- Publish directory: `public`

也可以直接用 `netlify.toml`（已提供）。
