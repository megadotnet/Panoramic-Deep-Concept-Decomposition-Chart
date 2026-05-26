<div align="center">
<img width="1200" height="475" alt="GHBanner" src="https://github.com/user-attachments/assets/0aa67016-6eaf-458a-adb2-6e31a0763ed6" />
</div>

# Gemini Lens - AI 图像编辑器

🌍 [English Version](./README.md)

## 📖 项目介绍

Gemini Lens 是一款由 Gemini 2.5 Flash Image 模型驱动的智能网页端图像编辑器。它允许用户上传源图像并提供文本提示，从而直观地编辑、转换和风格化照片。功能包括预设的编辑提示词、动态生成结果以及直接下载编辑后的图像。

在 AI Studio 中查看您的应用：[https://ai.studio/apps/drive/1qoagJHJBONxI9dBd-MhYmstFwIM7lCRA](https://ai.studio/apps/drive/1qoagJHJBONxI9dBd-MhYmstFwIM7lCRA)

## 🛠 技术栈

本项目依赖以下核心技术，按类别结构化展示如下：

### 1. 前端框架
- **React (`^19.2.0`)**: 用于构建交互式用户界面和管理状态的核心库。
- **React DOM (`^19.2.0`)**: 负责将 React 组件树渲染到 Web 平台。
- **Tailwind CSS (`CDN`)**: 实用优先的 CSS 框架，用于快速、响应式地构建 UI 样式。

### 2. 后端与 AI 服务 (第三方中间件)
- **@google/genai (`^1.30.0`)**: Google 官方 Gemini API SDK，用于与 Gemini 2.5 Flash Image 模型交互，提供 AI 驱动的图像处理能力。

### 3. 基础设施及运行环境
- **Node.js**: JavaScript 运行环境，为本地开发服务器和构建流程提供支持。

### 4. 工具链与构建工具
- **Vite (`^6.2.0`)**: 下一代前端构建工具，提供极速的开发服务器和优化的生产环境构建。
- **TypeScript (`~5.8.2`)**: 为 JavaScript 添加静态类型检查，提升代码质量、可读性和开发体验。
- **@vitejs/plugin-react (`^5.0.0`)**: 启用 React 支持的 Vite 插件，包含快速刷新 (Fast Refresh) 功能。

## ⚙️ 环境依赖要求

为避免环境冲突，请确保您的系统满足以下最低版本兼容要求：

- **Node.js**: `>= 22.14.0` (推荐：最新的 LTS 长期支持版本)
- **npm**: `>= 10.0.0` (随 Node.js 一起安装)
- **现代浏览器**: Chrome、Firefox、Edge 或 Safari (必须支持 ES 模块)

## 🚀 本地部署与启动步骤

### 前置准备
运行此应用需要 Google Gemini API Key。您可以从 Google AI Studio 获取。

### 操作指令 (适配 Windows、macOS 和 Linux)

1. **克隆仓库 (如适用)**
   ```bash
   git clone <repository-url>
   cd gemini-lens---ai-image-editor
   ```

2. **安装项目依赖**
   ```bash
   npm install
   ```

3. **配置环境变量**
   在项目根目录下创建一个 `.env.local` 文件，并添加您的 API Key：
   - **Windows (命令提示符 cmd):**
     ```cmd
     echo GEMINI_API_KEY=your_api_key_here > .env.local
     ```
   - **Windows (PowerShell):**
     ```powershell
     echo "GEMINI_API_KEY=your_api_key_here" | Out-File -Encoding utf8 .env.local
     ```
   - **macOS / Linux:**
     ```bash
     echo "GEMINI_API_KEY=your_api_key_here" > .env.local
     ```

4. **启动开发服务器**
   ```bash
   npm run dev
   ```

5. **访问应用程序**
   打开您的浏览器并访问终端中显示的地址 (通常是 `http://localhost:3000` 或 `http://localhost:5173`)。

## 📁 项目结构说明

```text
├── components/          # 可复用的通用 UI 组件
│   ├── Button.tsx       # 标准按钮组件
│   └── ImageUploader.tsx# 图像选择和预览组件
├── services/            # 业务逻辑与外部 API 交互集成层
│   └── geminiService.ts # 与 Google GenAI SDK 交互的服务类
├── App.tsx              # 应用程序主入口/根组件
├── index.html           # HTML 模板文件，包含 Tailwind CDN
├── index.tsx            # React 应用程序挂载点
├── types.ts             # 全局 TypeScript 接口及类型定义
├── vite.config.ts       # Vite 构建工具配置文件
├── package.json         # 项目元数据、脚本命令与依赖声明
├── tsconfig.json        # TypeScript 编译器配置文件
└── ReadMe-ZhCn.md       # 项目中文文档 (当前文件)
```

## 📝 开发规范

1. **组件设计**: 优先使用函数式组件 (Functional Components) 和 React Hooks。保持组件小巧、职责单一且易于复用。
2. **样式编写**: 统一使用 Tailwind CSS 实用类进行样式定义以保证一致性。除非绝对必要，否则避免编写自定义 CSS 文件。
3. **类型安全**: 必须在 `types.ts` 或各自的组件文件中严格定义接口和类型。尽量避免使用 `any` 类型。
4. **状态管理**: 使用 React 内置的 `useState` 和 `useCallback` 处理局部状态。对于跨组件的复杂状态，可提升至 `App.tsx` 中统一管理。
5. **API 调用**: 所有与外部 API 的交互逻辑必须抽象在 `services/` 目录中，以实现业务逻辑与 UI 组件的解耦。

## ❓ 常见问题排查

**Q: 点击生成 (Generate) 时提示 "An unexpected error occurred" (发生意外错误)。**
* **A:** 请检查浏览器控制台 (Console)。这通常是由于 `GEMINI_API_KEY` 无效或未配置引起的。请确保 `.env.local` 文件格式正确且密钥有效。修改 `.env.local` 后，请务必重启开发服务器 (`npm run dev`)。

**Q: 浏览器提示 `@google/genai` 模块 "Failed to load resource" (加载资源失败)。**
* **A:** 请验证您的网络连接是否允许访问 `aistudiocdn.com`。由于 SDK 和 React 库是通过 `index.html` 中的 Import Maps (导入映射) 从 CDN 加载的，网络限制会导致加载失败。

**Q: 启动时提示端口被占用 (Port already in use error)。**
* **A:** 如果 3000 端口被占用，Vite 通常会自动尝试下一个可用端口。如果您想强制关闭占用 3000 端口的进程，可以使用以下命令：
  - macOS/Linux: `kill $(lsof -t -i :3000)`
  - Windows: `netstat -ano | findstr :3000` 找到对应的 PID，然后执行 `taskkill /PID <PID> /F`
