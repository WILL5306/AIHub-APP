# [Aihub - Mobile]

## 📖 项目简介

这是一个基于 **uni-app** 开发的移动端 AI 聚合应用。它将 DeepSeek、Kimi、ChatGPT、腾讯元宝等主流 AI 工具集成在一个轻量级的 App 中。通过 WebView 容器技术，实现了一键直达官方服务，无需复杂的 API 配置，无广告干扰，为用户提供纯净、流畅的移动端 AI 体验。

<img width="720" height="1460" alt="image" src="https://github.com/user-attachments/assets/5e67a8c4-eb4b-439a-9cf7-93ef273affdc" />

## 📲 安装说明
文件名: Aihub.apk

兼容性: Android 5.0+

注意事项:

如果通过微信发送安装包，微信可能会自动在文件名后添加 .1 后缀（如 Aihub.apk.1）。请在手机文件管理器中重命名，删除 .1 后即可正常安装。

<img width="239" height="104" alt="image" src="https://github.com/user-attachments/assets/fd6e82a2-8a80-4cfa-bf95-74ce10a03df9" />


部分 AI 服务（如 ChatGPT、Google Gemini）需要科学网络环境才能访问。
## 🛠 技术栈

* **核心框架**: uni-app (基于 Vue.js)
* **开发工具**: HBuilderX
* **运行环境**: Android / iOS (本项目主要针对 Android 进行打包)
* **路由/页面**: uni-app Pages

## 📂 目录结构

```text
├── pages
│   ├── index
│   │   └── index.vue       # 首页：AI 工具聚合菜单列表
│   └── browser
│       └── browser.vue     # 浏览器页：通用的 WebView 容器，用于加载外部 AI 链接
├── static                  # 静态资源（应用图标、截图等）
├── App.vue                 # 应用入口，配置全局样式和生命周期
├── main.js                 # Vue 初始化入口
├── manifest.json           # 应用配置文件（App名称、图标、权限、打包配置）
├── pages.json              # 路由配置文件（导航栏样式、页面路径）
└── README.md               # 项目说明文档
```
## 🚀 使用
本项目需要使用 HBuilderX 进行开发和运行。

1. 环境准备
下载并安装 HBuilderX。

2. 导入项目
打开 HBuilderX，选择 文件 -> 导入 -> 从本地目录导入，选择本项目文件夹。

3. 真机运行 (调试)
   
  (1)使用数据线连接 Android 手机，并开启 USB 调试 模式。

  (2)在 HBuilderX 顶部菜单点击 运行 -> 运行到手机或模拟器 -> 运行到 Android App 基座。

  (3)手机端确认安装 HBuilder 调试基座，即可实时预览。

4. 打包
生成 APK 安装包
在 HBuilderX 中打开 manifest.json设置应用图标，确保 应用标识(AppID) 已获取。

点击顶部菜单 发行 -> 原生App-云打包。

选择 使用云端证书（或公共测试证书）。

取消勾选所有广告联盟选项。

点击 打包，等待控制台生成下载链接。



© 2025 Aihub Project. Designed By XZJ.
