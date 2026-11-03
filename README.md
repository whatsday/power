# Power

Power 项目的静态欢迎页。纯 HTML/CSS，无构建步骤。

## 分支模型

| 分支 | 作用 |
|---|---|
| `main` | 源代码分支（日常开发都提交到这里） |
| `publish` | 干净的发布分支，**只含站点文件**，由 CI 自动同步管理，请勿手动修改 |

自动化流程：

```
push main ──> GitHub Actions (publish-pages.yml)
             ──> 同步站点文件到 publish 分支（剔除 .github / README 等）
             ──> Cloudflare Pages（Git 集成，生产分支 = publish）自动部署上线
```

以后引入构建步骤（`npm run build` → `dist/`）后，CI 会**自动改发 `dist/` 产物**，流程无需改动。

## 本地预览

```bash
# 任选其一
npx serve .
python3 -m http.server 8000   # 然后访问 http://localhost:8000
```

## 首次部署（一次性）

在 Cloudflare 控制台：Workers & Pages → Create → Pages → **Connect to Git**（GitHub 授权；若仓库为私有，需给 Cloudflare Pages GitHub App 勾选本仓库）→ 选择 `whatsday/power`：

- Branch to import: `publish`（Production branch = `publish`）
- Build command: **留空**
- Build output directory: `.`

之后每次 push `main` 都会自动重新部署，无需任何本地凭据。
