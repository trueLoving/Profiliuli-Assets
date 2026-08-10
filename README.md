# profiliuli-assets

[Profiliuli](https://github.com/trueLoving/Profiliuli) 的静态资源仓库：背景视频、项目演示、经历图片、简历等媒体文件集中存放于此，由主站通过 URL 引用，避免把大体积资源塞进站点仓库。

[English](#english) | [中文](#中文)

---

## 中文

### 用途

| 主站仓库 | 资源仓库 |
|----------|----------|
| `Profiliuli` — 站点代码与配置 | `profiliuli-assets` — 图片 / 视频 / PDF |

主站不再把大文件放在 `public/`，改为指向本仓库的稳定 URL。

### 目录结构

```text
profiliuli-assets/
├── background/
│   └── video/          # 桌面壁纸：.mp4 + 同名 .webp poster
├── projects/
│   ├── asair/
│   ├── pixuli/
│   ├── profiliuli/
│   └── stationuli/     # 项目截图与 demo 视频
├── experiences/        # 教育 / 工作经历配图
├── resume/             # resume-en.pdf / resume-zh.pdf
├── me.webp             # 头像
└── favicon.ico
```

### 使用方式

推荐用 **jsDelivr**（有 CDN 缓存；提交后可能有短延迟）：

```text
https://cdn.jsdelivr.net/gh/trueLoving/profiliuli-assets@main/<path>
```

示例：

```text
https://cdn.jsdelivr.net/gh/trueLoving/profiliuli-assets@main/background/video/Honkai-Star-Rail-QHD.mp4
https://cdn.jsdelivr.net/gh/trueLoving/profiliuli-assets@main/me.webp
https://cdn.jsdelivr.net/gh/trueLoving/profiliuli-assets@main/resume/resume-zh.pdf
```

也可使用 GitHub raw（无 CDN，适合临时调试）：

```text
https://raw.githubusercontent.com/trueLoving/profiliuli-assets/main/<path>
```

主站配置示例：

```ts
const ASSETS_BASE =
  'https://cdn.jsdelivr.net/gh/trueLoving/profiliuli-assets@main';

const avatar = `${ASSETS_BASE}/me.webp`;
const wallpaper = `${ASSETS_BASE}/background/video/Honkai-Star-Rail-QHD.mp4`;
```

生产环境建议把 `@main` 换成 **commit SHA 或 tag**（如 `@v1.0.0`），避免 CDN 缓存到旧文件。

### 约定

1. **路径稳定**：已对外引用的路径不要随意改名或挪动；必须变更时同步改主站配置。
2. **成对资源**：视频壁纸提供同名 `.mp4` + `.webp` poster。
3. **命名**：小写、短横线或原有产品目录名；避免空格与中文文件名。
4. **体积**：大视频先压缩再提交；优先 WebP / 合理码率的 MP4。
5. **本仓只放静态资源**，不放站点源码或密钥。

### 本地预览

```bash
# 用任意静态服务器看目录，例如：
npx serve .
```

### License

代码与仓库结构采用 MIT（若适用）。  
媒体素材版权归原作者 / 权利人所有；商用或二次分发前请自行确认授权。部分壁纸 / demo 仅供个人站点展示。

---

## English

Static media for [Profiliuli](https://github.com/trueLoving/Profiliuli): wallpapers, project demos, experience images, resumes. Kept out of the site repo and consumed via URL.

### Layout

Same as above (`background/`, `projects/`, `experiences/`, `resume/`, `me.webp`, `favicon.ico`).

### Consume via jsDelivr

```text
https://cdn.jsdelivr.net/gh/trueLoving/profiliuli-assets@main/<path>
```

Pin to a tag or commit SHA in production instead of `@main`.

### Conventions

Keep paths stable, ship video + WebP poster pairs, use lowercase filenames, optimize before commit, assets only (no app source or secrets).

### License

MIT for repo scaffolding where applicable. Media rights remain with their owners; verify before redistribution.
