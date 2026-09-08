# 深海听觉 · 潮汐交响 / Deep Blue Symphony

一段由潮声引路的海底漫游交互站点。

## 快速开始

### 1. 在你电脑上直接打开看（最简单）

双击 `deep-blue-symphony.html`（或 `index.html`），浏览器会自动打开。整个站点立刻可玩。

> 如果浏览器限制了 `file://` 协议导致图片不显示，按下面方法 2 起一个本地服务。

### 2. 一键起本地静态服务器（推荐改东西时用）

在项目文件夹里右键 → "在终端中打开" → 粘贴下面任一行：

```bash
python -m http.server 8080        # 用系统自带的 Python
npx --yes serve -p 8080          # 或用 Node（首次需联网下包）
```

然后浏览器开 <http://localhost:8080>。

### 3. 一键部署到公网（让任何人通过链接访问）

任选一个，**纯网页操作、不用装软件**：

| 平台 | 步骤 | 耗时 |
|---|---|---|
| **Netlify Drop** | 打开 <https://app.netlify.com/drop> → 把整个文件夹拖进去 → 等几秒 → 拿到 `xxx.netlify.app` 公网链接 | 30 秒 |
| **Vercel** | 打开 <https://vercel.com/new> → 用 GitHub 登录 → 拖入文件夹 → Deploy | 1 分钟 |
| **Cloudflare Pages** | 打开 <https://pages.cloudflare.com> → "Upload assets" → 拖入 zip | 1 分钟 |
| **GitHub Pages** | push 到 GitHub 仓库 → Settings → Pages → 选 main 分支根目录 → 拿到 `xxx.github.io` 链接 | 2 分钟 |
| **腾讯云 EdgeOne Pages** | 打开 <https://edgeone.ai/pages> → 拖入文件夹 → 部署 | 1 分钟 |

> 任何平台生成的公网链接，**发给别人都能开**，都不需要登录。

## 文件结构

```
deep-blue-symphony/
├── README.md                     ← 你正在看的
├── deep-blue-symphony.html       ← 主入口（默认）
├── index.html                    ← 同上（部署平台找这个）
└── assets/
    ├── tingting-clean.png        ← 首页角色（背景已转透明）
    ├── scene-radio-nook.jpg      ← 04 收音机阅读角
    ├── scene-cozy-kitchen.jpg    ← 03 温馨厨房
    ├── scene-stargazing.jpg      ← 01 山顶观星
    ├── scene-ocean-bedroom.jpg   ← 02 海景卧室
    ├── expression-sheet.jpg      ← 表情延展图鉴
    ├── scene-extension.jpg       ← 小场景延展图鉴
    └── costume-sheet.jpg         ← 换装延展图鉴
```

## 在你电脑上编辑

### 改文字 / 改交互（编辑 HTML 即可）

任何编辑器都行：
- **新手友好**：VSCode（<https://code.visualstudio.com/>）、Sublime Text、HBuilder
- **直接**：记事本 / Notepad++

打开 `deep-blue-symphony.html`，搜下面这些关键词就能找到对应位置：

| 想改什么 | 搜索关键词（在 HTML 里） |
|---|---|
| 4 个场景的标题、故事文案 | `sections = [` |
| 章节小标题 / 段落正文 | `chapterTitle`、`chapterText` |
| 表情 6 张图的标签文字 | `const expressions = [` |
| 小场景 4 张图的标签文字 | `const miniScenes = [` |
| 整体配色（金色 / 深蓝 / 字体） | `#d8cab0` / `#0c1518` / `Playfair Display` |
| 弹窗尺寸 / 是否可裁切图片 | `.scene-card`、`.express-sheet`、`.x-sheet` |

保存 → 浏览器刷新就能看到新效果。

### 换图片

直接**用同名文件覆盖** `assets/` 里对应的图就行（保持文件名一致、保持 `.jpg` / `.png` 后缀一致）：

| 想换什么 | 替换 |
|---|---|
| 首页角色 | `assets/tingting-clean.png`（建议 4:1 宽图、JPG/PNG 转好的透明 PNG） |
| 4 个场景图 | `assets/scene-*.jpg`（建议 4:1 宽图、JPG） |
| 表情图鉴 | `assets/expression-sheet.jpg` |
| 小场景图鉴 | `assets/scene-extension.jpg` |
| 换装图鉴 | `assets/costume-sheet.jpg` |

替换后刷新页面即生效。

### 关键设计约定

- **图片不能被裁** ← 这是用户明确要求。所有 `<img>` 都用 `object-fit:contain` + `height:auto`，**不要改成 `cover`**
- **角色 PNG 的黑底要转透明** ← 在 `tingting-clean.png` 替换前，先用 PS/PIL 把黑色背景去掉
- **改表情/小场景/换装标签时，要看图上的中文** ← 不要自己起新名字

## 进阶 / 其他需求

如需添加动画、改交互逻辑、生成单文件版（一张 HTML 内联所有图，方便邮件发送）等，告诉我。
