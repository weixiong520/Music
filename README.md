# Savior

Savior 是一个基于 Electron 和 Vue 3 的桌面音乐应用项目。

## 项目地址

- Gitee 仓库：https://gitee.com/savior199812/z-music.git

## 技术栈

- Electron
- Vue 3
- Webpack
- Less

## 开发环境

- Node.js 22 及以上
- npm 8.5.2 及以上

## 启动项目

```bash
npm install
npm run dev
```

## 打包项目

```bash
npm run pack
```

说明：

- Windows 打包依赖 Visual Studio Build Tools。
- 需要安装 `使用 C++ 的桌面开发` 工作负载。

## 项目结构

```text
Savior-music/
├─ .babelrc
├─ .editorconfig
├─ .eslintrc.base.cjs
├─ .eslintrc.cjs
├─ .gitignore
├─ .ncurc.js
├─ CHANGELOG.md
├─ LICENSE
├─ README.md
├─ jsconfig.json
├─ package.json
├─ package-lock.json
├─ postcss.config.js
├─ tsconfig.json
├─ build/
│  ├─ latest.yml
│  ├─ Savior-music-v2.12.1-x64-Setup.exe
│  ├─ Savior-music-v2.12.1-x64-Setup.exe.blockmap
│  ├─ builder-debug.yml
│  ├─ Release/
│  │  └─ qrc_decode.node
│  └─ win-unpacked/
│     ├─ Savior-music.exe
│     ├─ resources/
│     └─ locales/
├─ build-config/
│  ├─ build-after-pack.js
│  ├─ build-before-pack.js
│  ├─ build-pack.js
│  ├─ css-loader.config.js
│  ├─ dependencies-patch.js
│  ├─ lib-update.js
│  ├─ pack.js
│  ├─ post-install.js
│  ├─ runner-dev.js
│  ├─ utils.js
│  ├─ vue-loader.config.js
│  ├─ webpack-build-config.js
│  ├─ lib/
│  ├─ main/
│  ├─ renderer/
│  ├─ renderer-lyric/
│  └─ renderer-scripts/
├─ dist/
│  ├─ main.js
│  ├─ renderer.js
│  ├─ renderer-lyric.js
│  ├─ user-api-preload.js
│  ├─ dbService.worker.js
│  ├─ index.html
│  ├─ lyric.html
│  ├─ media/
│  ├─ static/
│  ├─ theme_images/
│  └─ userApi/
├─ licenses/
│  ├─ license.rtf
│  ├─ license_en.txt
│  └─ license_zh.txt
├─ publish/
│  ├─ changeLog.md
│  ├─ index.js
│  ├─ version.json
│  └─ utils/
├─ resources/
│  └─ icons/
│     ├─ 16x16.png
│     ├─ 32x32.png
│     ├─ 48x48.png
│     ├─ 64x64.png
│     ├─ 128x128.png
│     ├─ 256x256.png
│     ├─ 512x512.png
│     ├─ icon.png
│     ├─ icon.ico
│     └─ icon.icns
└─ src/
   ├─ common/
   │  ├─ theme/
   │  ├─ types/
   │  └─ utils/
   ├─ lang/
   │  ├─ en-us.json
   │  ├─ zh-cn.json
   │  ├─ zh-tw.json
   │  └─ i18n.ts
   ├─ main/
   │  ├─ event/
   │  ├─ modules/
   │  ├─ types/
   │  ├─ utils/
   │  ├─ worker/
   │  ├─ app.ts
   │  ├─ index.ts
   │  └─ index-dev.ts
   ├─ renderer/
   │  ├─ assets/
   │  ├─ components/
   │  ├─ core/
   │  ├─ event/
   │  ├─ plugins/
   │  ├─ store/
   │  ├─ types/
   │  ├─ utils/
   │  ├─ views/
   │  ├─ worker/
   │  ├─ App.vue
   │  ├─ main.ts
   │  └─ router.ts
   ├─ renderer-lyric/
   │  ├─ assets/
   │  ├─ components/
   │  ├─ core/
   │  ├─ plugins/
   │  ├─ store/
   │  ├─ types/
   │  ├─ useApp/
   │  ├─ utils/
   │  ├─ App.vue
   │  └─ main.ts
   └─ static/
      └─ images/
```

## 当前状态

- 已完成仓库初始化并推送到 Gitee
- 已调整搜索页标签选中横条与标题的间距
- 本地开发环境可正常启动
- 当前打包受限于 Windows C++ 构建工具安装状态

## 许可证

本项目当前沿用仓库中的 `LICENSE` 文件。