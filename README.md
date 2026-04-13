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
src/
  common/            公共模块
  main/              Electron 主进程
  renderer/          主界面渲染进程
  renderer-lyric/    桌面歌词渲染进程
  static/            静态资源
build-config/        构建配置
resources/           图标与打包资源
```

## 当前状态

- 已完成仓库初始化并推送到 Gitee
- 已调整搜索页标签选中横条与标题的间距
- 本地开发环境可正常启动
- 当前打包受限于 Windows C++ 构建工具安装状态

## 许可证

本项目当前沿用仓库中的 `LICENSE` 文件。
