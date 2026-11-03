# Power

Power 项目的静态欢迎页。纯 HTML/CSS，无构建步骤。

## 本地预览

```bash
# 任选其一
npx serve .
python3 -m http.server 8000   # 然后访问 http://localhost:8000
```

## 部署

推送到 `main` 分支后，Vercel / Cloudflare Pages（Git 集成）会自动构建并发布。

```bash
git add -A && git commit -m "update" && git push origin main
```
