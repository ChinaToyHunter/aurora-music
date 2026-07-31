# Aurora Music

> Apple 风格的 iPad 音乐播放器概念原型，使用原生 HTML、CSS 与 JavaScript 构建。

[在线体验](https://chinatoyhunter.github.io/aurora-music/) · [报告问题](https://github.com/ChinaToyHunter/aurora-music/issues) · [提出建议](https://github.com/ChinaToyHunter/aurora-music/issues)

Aurora Music 是一个无需构建步骤的单文件音乐播放器 Web 原型。它以柔和渐变、半透明玻璃面板和 iPad 横屏布局为核心，提供本地音频导入、歌词同步、播放队列、收藏、深浅色主题，以及多个在线内容入口的探索性集成。

> [!NOTE]
> 本项目定位为**可交互的播放器概念原型**，是未完成的在线音乐播放器，仅供参考

## ✨ 功能特性

### 播放体验

- Apple 风格 iPad 音乐播放器界面
- 底部迷你播放器与全屏播放视图
- 播放 / 暂停 / 上一首 / 下一首
- 播放进度、拖动跳转与音量控制
- 播放队列管理
- 收藏歌曲
- 深色 / 浅色主题切换
- 浏览器媒体控制支持（Media Session API）
- 自动保存播放进度、队列、主题、音量和收藏状态

### 本地音乐与歌词

- 通过文件选择器导入本地音频
- 支持拖放导入音频文件
- 支持导入文件夹中的音乐
- 自动读取文件名并生成本地曲目
- 支持 `.lrc` 歌词文件导入
- 支持手动粘贴歌词
- 支持时间轴歌词与逐字歌词解析
- 歌词随播放进度高亮，并支持点击歌词跳转
- 尝试自动匹配同名音频与歌词文件

### 在线内容入口

- **Internet Archive**：搜索并播放可公开访问的音频资源
- **YouTube**：
  - 粘贴视频链接或视频 ID 进行播放
  - 可选配置 YouTube Data API Key 进行搜索
  - 使用官方嵌入播放器，不下载或转换视频音频
- **Bilibili**：
  - 支持粘贴 Bilibili 视频链接或 BV 号
  - 使用官方 iframe 播放器嵌入
- **网易云音乐 / QQ 音乐**：
  - 可配置自行部署或提供的兼容 API 服务
  - 支持搜索、歌曲详情、播放地址与歌词等能力（取决于 API 实现）
- **公开音乐站点搜索入口**：
  - 提供网易云音乐、QQ 音乐、Bilibili、YouTube 等平台的搜索跳转
  - 不抓取页面、不解析下载链接、不绕过平台限制

### 演示内容

项目内置若干演示曲目和歌词，用于展示播放器交互效果。演示音频主要来自公开示例资源，例如 SoundHelix。

> [!IMPORTANT]
> 内置演示资源仅用于界面与功能演示，不代表项目拥有相关音乐作品的版权。

---

## 🖼️ 在线预览

访问 GitHub Pages 在线体验：

**[https://chinatoyhunter.github.io/aurora-music/](https://chinatoyhunter.github.io/aurora-music/)**

---

## 🚀 快速开始

本项目是一个纯静态单页应用，当前不依赖 npm、Node.js 构建流程或前端框架。

### 方式一：直接打开

克隆仓库后，直接在浏览器中打开 `index.html`：

```bash
git clone https://github.com/ChinaToyHunter/aurora-music.git
cd aurora-music
```

然后打开：

```text
index.html
```

> [!TIP]
> 直接以 `file://` 方式打开时，部分浏览器可能会限制跨域请求、远程音频或 iframe 功能。推荐使用本地静态服务器运行。

### 方式二：使用 Python 启动静态服务器

在项目根目录执行：

```bash
python -m http.server 8000
```

随后访问：

```text
http://localhost:8000/
```

### 方式三：使用任意静态服务器

例如：

```bash
npx serve .
```

也可将项目部署至任意静态托管平台：

- GitHub Pages
- Cloudflare Pages
- Vercel
- Netlify
- Nginx
- Apache

---

## 📁 项目结构

当前项目采用单文件实现：

```text
aurora-music/
└── index.html    # 页面结构、样式与交互逻辑
```

`index.html` 内包含：

- HTML 页面结构
- CSS 主题、布局与动效
- JavaScript 播放器逻辑
- 本地文件和歌词导入逻辑
- 播放队列与收藏管理
- 浏览器本地存储逻辑
- Internet Archive、YouTube、Bilibili 与可选音乐 API 集成

---

## 🔧 可选 API 配置

Aurora Music 可在页面内配置部分在线内容服务。所有配置默认保存在**当前浏览器的 Local Storage** 中，不会上传至本项目仓库。

### YouTube Data API

若需要使用 YouTube 搜索能力，可填写自己的 YouTube Data API Key。

未配置 Key 时，项目仍可：

- 粘贴 YouTube 视频 URL 或视频 ID
- 使用内置模拟目录进行展示
- 跳转至 YouTube 官方搜索页面

> [!WARNING]
> 浏览器端保存的 API Key 不应被视为安全机密。请勿在公共设备或不可信环境中填写敏感密钥。

### 网易云音乐 API

项目支持填写兼容网易云音乐接口的 API Base URL，例如用户自行部署的服务：

```text
http://localhost:3000
```

接口能力通常包括：

```text
/cloudsearch
/song/detail
/song/url
/lyric
```

可参考兼容 API 项目：

- [NeteaseCloudMusicApiEnhanced](https://github.com/NeteaseCloudMusicApiEnhanced/api-enhanced)

### QQ 音乐 API

QQ 音乐能力同样依赖用户自行部署或提供的兼容 API 服务，例如：

```text
http://localhost:3300
```

可参考：

- [QQMusicApi](https://github.com/L-1124/QQMusicApi)

> [!CAUTION]
> 第三方音乐 API 的可用性、鉴权方式、接口字段、CORS 策略与合规性由对应服务决定。本项目不提供这些服务端，也不保证任何第三方接口持续可用。

---

## 💾 本地数据与隐私

Aurora Music 使用浏览器 `localStorage` 保存部分偏好与播放状态，包括：

- 当前播放队列
- 当前曲目与播放进度
- 音量
- 收藏列表
- 深色 / 浅色主题
- API 服务地址与音质选项
- YouTube API Key（如用户填写）

### 本地音频不会永久保存

本地导入的音频使用浏览器 `File API` 与 `URL.createObjectURL()` 临时播放：

- 本地文件本身不会上传到网络
- 页面刷新后，浏览器无法重新读取此前导入的本地文件
- 需要重新导入本地音频
- 清除本地数据后，相关播放状态和配置将被移除

### 使用 Cookie 的注意事项

若你配置的第三方音乐 API 需要 Cookie 或登录信息：

- 请仅在可信的个人设备上使用
- 不要将 Cookie、Token、Key 或个人配置提交到 Git 仓库
- 请自行确认所用 API 的安全性、访问控制与隐私策略

---

## ⚠️ 已知限制

- 项目为概念原型，尚未按生产级应用进行工程化拆分。
- 当前没有 TypeScript、模块化目录、自动化测试、CI/CD 或构建流程。
- YouTube 和 Bilibili 内容通过官方 iframe 播放，不属于统一的 HTML5 音频播放链路。
- YouTube、Bilibili、Internet Archive 与第三方音乐 API 的功能可能受到网络、地区、跨域策略和服务端限制影响。
- 未部署网易云音乐或 QQ 音乐 API 时，对应搜索与播放能力不可用或受限。
- 本地导入的音频文件在刷新后无法自动恢复。
- Media Session、文件夹导入、拖放和媒体控制等能力在不同浏览器中的支持程度可能不同。
- 本项目不提供音频下载、音频解析、平台内容抓取或绕过版权/访问限制的能力。

---

## 🧰 技术栈

- HTML5
- CSS3
  - CSS Custom Properties
  - Flexbox
  - CSS Grid
  - 响应式布局
- Vanilla JavaScript
- HTML5 `<audio>`
- File API
- `URL.createObjectURL`
- `localStorage`
- `fetch`
- Media Session API
- iframe 嵌入播放器

无需安装依赖：

```bash
npm install
npm run dev
npm run build
```

---

## 🗺️ 后续方向

- [ ] 拆分 HTML、CSS 与 JavaScript 模块
- [ ] 增加移动端与不同屏幕尺寸适配
- [ ] 增加播放列表管理与导入 / 导出
- [ ] 改进远程音频加载失败提示
- [ ] 完善歌词编辑与匹配体验
- [ ] 增加测试与持续集成
- [ ] 增加正式的开源许可证说明
- [ ] 视需求增加 PWA 离线体验

欢迎通过 [Issues](https://github.com/ChinaToyHunter/aurora-music/issues) 提出功能建议或问题反馈。

---

## 📄 许可证

当前仓库**尚未声明开源许可证**，也未包含 `LICENSE` 文件。

除非项目维护者另有明确授权，请勿默认将本项目视为采用 MIT、Apache-2.0 或其他开源许可证。涉及复制、修改、分发或商业使用时，请先联系维护者确认授权范围。

---

## 🙌 致谢

- [Internet Archive](https://archive.org/)：公开音频资源与元数据接口
- [YouTube](https://www.youtube.com/)：官方播放器嵌入能力
- [Bilibili](https://www.bilibili.com/)：官方播放器嵌入能力
- [SoundHelix](https://www.soundhelix.com/)：演示音频资源
- 所有为开放音乐生态、前端体验和播放器技术做出贡献的开发者

---

<p align="center">
  Built as an iPad music player concept by <a href="https://github.com/ChinaToyHunter">ChinaToyHunter</a>.
</p>
