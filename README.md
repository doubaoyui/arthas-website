# Arthas Website (Hugo)

这个子项目用于快速搭建 Arthas 官网（下载页）。

## What

- 静态站点生成：Hugo
- 目标：提供 Arthas 的 Windows / macOS 下载入口（纯静态，适合挂在 Nginx 上）

## Why

- Hugo 构建快、部署简单（任何静态托管都行）。
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

### 后台（可选）

本仓库目前以“纯静态官网”为目标：不包含后台登录/写库能力。

### 下载数据维护

下载按钮来自 `data/downloads.yaml`，可以：

- 直接改文件提交

### 部署（Nginx/任意静态托管）

1) 本地构建：

```bash
hugo --gc --minify
```

2) 把生成的 `public/` 目录内容上传到服务器的站点根目录（例如 `/var/www/arthas-website`）
3) Nginx 配置静态目录即可
