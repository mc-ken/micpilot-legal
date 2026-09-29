# GitHub Pages 站点

这个目录就是对外发布的静态站点，包含两页：

| 文件 | 用途 |
| --- | --- |
| `index.html` | 英文产品落地页（可放 Gumroad 购买链接） |
| `privacy.html` | 英文隐私政策（Chrome 商店和 Gumroad 都要填这个网址） |
| `style.css` | 两页共用的样式 |
| `.nojekyll` | 告诉 GitHub Pages 不要用 Jekyll 处理，避免下划线开头的文件被忽略 |

## 重要：不要用主仓库发布

GitHub 免费版的 Pages **只支持公开仓库**。如果主仓库是公开的，你的扩展和中继源码就全部公开了。

正确做法是新建一个**只放法务页面的公开仓库**，例如 `micpilot-legal`：

```bash
# 在项目根目录执行
cd docs
git init
git add .
git commit -m "Add product page and privacy policy"
git branch -M main
git remote add origin https://github.com/<你的用户名>/micpilot-legal.git
git push -u origin main
```

然后在该仓库的 Settings → Pages 里，把 Source 设为 **Deploy from a branch**，
Branch 选 `main`，Folder 选 `/ (root)`，保存。

一两分钟后你会拿到一个形如
`https://<你的用户名>.github.io/micpilot-legal/` 的地址，
隐私政策就是 `https://<你的用户名>.github.io/micpilot-legal/privacy.html`。

## 发布前检查清单

1. 打开 `privacy.html`，把所有黄色高亮的 `[方括号]` 换成真实内容：
   `[YOUR NAME OR COMPANY]`、`[YOUR CONTACT EMAIL]`、两个日期。
2. 打开 `index.html`，替换 `[GUMROAD PRODUCT LINK]`、`[YOUR CONTACT EMAIL]`、`[YOUR NAME OR COMPANY]`。
3. 确认没有残留的 `[` 字符：在仓库里搜一下 `[YOUR` 和 `[GUMROAD`。
4. 手机上也打开一次，确认排版正常。
5. 把 `privacy.html` 的完整网址填到：
   - Chrome Web Store 开发者后台的「Privacy policy URL」
   - Gumroad 商品的「Privacy policy」字段
6. 删掉 `privacy.html` 顶部那段 `<!-- 发布前替换 -->` 注释。

## 另一种做法：主仓库是私有的

如果不想开新仓库，也可以让主仓库保持私有，仅把这一页托管到
Cloudflare Pages 或 Netlify 的免费版（支持私有仓库构建），效果一样，链接换成它们的域名即可。

## 自定义域名（可选）

想用自己的域名（例如 `micpilot.app`），在仓库 Settings → Pages → Custom domain 里填域名，
然后在域名商那边加一条 CNAME 记录指向 `<你的用户名>.github.io`。
GitHub 会自动签发 HTTPS 证书，勾选 Enforce HTTPS 即可。
