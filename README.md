# GitHub Pages 起步模板

一个不依赖任何外链的单文件个人站。除 `index.html` 外零依赖，CSS 全内联，深色/浅色自动适配。

## 目录

```
index.html    站点本体，所有内容都在这个文件里改
.nojekyll     告诉 GitHub 不要用 Jekyll 处理，保证文件原样发出
README.md     本文件，可以删掉或保留
```

## 三步上线

### 1. 建仓库

在 GitHub 新建仓库，**名字必须是 `<你的用户名>.github.io`**，可见性选 **Public**。

> 名字对不上，就会变成 `https://用户名.github.io/仓库名/` 这样的子路径。
> 免费账户只能用公开仓库发布 Pages，私有仓需要 Pro。

### 2. 推代码

在本目录下执行（把 `你的用户名` 换成实际的）：

```bash
git init
git add .
git commit -m "init"
git branch -M main
git remote add origin https://github.com/你的用户名/你的用户名.github.io.git
git push -u origin main
```

### 3. 开启 Pages

仓库 → **Settings** → 左侧 **Pages**：

- Source 选 `Deploy from a branch`
- Branch 选 `main`，目录选 `/ (root)`
- 点 **Save**

等 1–2 分钟，访问 `https://你的用户名.github.io`。

## 要改的地方

在 `index.html` 里搜这几处替换：

| 位置 | 改成 |
|---|---|
| `<title>` 和两处 `og:title` | 你的名字 |
| `<meta name="description">` 和 `og:description` | 你的介绍，会显示在分享卡片上 |
| `<h1>` | 你的名字 |
| `.lede` | 一句话介绍 |
| `.links` 里的三个 `href` | 你的 GitHub / 博客 / 邮箱 |
| 「项目」下的三个 `<li>` | 你的项目，不需要就整段删掉 |
| 「关于」里的两段 `<p>` | 你的介绍 |
| 页脚 | 名字 |

改完 `git add . && git commit -m "update" && git push`，一分钟内自动生效。

## 加自己的域名（可选）

1. 仓库 Settings → Pages → Custom domain 填域名并保存
2. 在域名 DNS 里按 GitHub 文档当页列出的 IP 配 A 记录，`www` 配 CNAME
3. 等生效后勾上 **Enforce HTTPS**

> A 记录的 IP 会变，照 [GitHub 官方文档](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)当页的列表填，别抄二手博客。
> 保存 Custom domain 后仓库里会多一个 `CNAME` 文件，要跟着提交，别删。

## 几个坑

- **样式丢了**：多半是引入了相对路径的 CSS，或者仓库名不是 `<用户名>.github.io` 却把资源写成了 `/css/x.css` 绝对路径。
- **推送后不更新**：Pages 有构建频率软限制（10 次/小时）。等几分钟再看，别反复推。
- **找不到 Pages 入口**：先确认仓库是 Public。
- **国内打不开**：`.github.io` 在大陆访问不稳定，属正常现象，不是配置问题。
