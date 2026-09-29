# GitHub Pages 站点

**已经发布上线：**

| | |
| --- | --- |
| 仓库 | https://github.com/mc-ken/micpilot-legal （公开） |
| 落地页 | https://mc-ken.github.io/micpilot-legal/ |
| **隐私政策** | **https://mc-ken.github.io/micpilot-legal/privacy.html** |

隐私政策那个地址就是填到 Chrome Web Store 后台「Privacy policy URL」和
Gumroad 商品「Privacy policy」字段的内容。已开启强制 HTTPS。

## 这个目录是源文件

本目录保存的是源文件，发布仓库里是它们的副本。改完这里的文件后，同步过去即可自动更新线上站点：

```bash
# 第一次先克隆发布仓库
git clone https://github.com/mc-ken/micpilot-legal.git ~/micpilot-legal

# 以后每次改完 docs/ 里的文件，同步并推送
cp docs/index.html docs/privacy.html docs/style.css docs/.nojekyll docs/README.md ~/micpilot-legal/
cd ~/micpilot-legal
git add -A && git commit -m "Update site" && git push
```

推上去后一两分钟线上就会更新（Pages 需要重新构建一次）。

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

## 为什么单独开仓库

GitHub 免费版的 Pages **只支持公开仓库**，而本项目的主目录包含扩展和中继的全部源码。
如果把主仓库公开，付费版想卖的东西就白送了。所以法务页面单独放一个公开仓库，
主项目保持私有。

## 自定义域名（可选）

想用自己的域名（例如 `micpilot.app`），在 GitHub 仓库的 Settings → Pages → Custom domain 里填域名，
然后在域名商那边加一条 CNAME 记录指向 `<你的用户名>.github.io`。
GitHub 会自动签发 HTTPS 证书，勾选 Enforce HTTPS 即可。
