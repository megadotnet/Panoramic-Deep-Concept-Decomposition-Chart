<div align="center">
<img width="1200" height="475" alt="GHBanner" src="https://github.com/user-attachments/assets/0aa67016-6eaf-458a-adb2-6e31a0763ed6" />
</div>

# Gemini Lens - AI Image Editor

🌍 [中文版说明 (Chinese Version)](./ReadMe-ZhCn.md)

## 📖 Project Introduction

Gemini Lens is an intelligent web-based image editor powered by the Gemini 2.5 Flash Image model. It allows users to upload source images and provide text prompts to intuitively edit, transform, and stylize photos. Features include preset editing prompts, dynamic result generation, and direct downloading of edited images.

View your app in AI Studio: [https://ai.studio/apps/drive/1qoagJHJBONxI9dBd-MhYmstFwIM7lCRA](https://ai.studio/apps/drive/1qoagJHJBONxI9dBd-MhYmstFwIM7lCRA)

## 🛠 Tech Stack

The project relies on the following core technologies, structured by category:

### 1. Frontend
- **React (`^19.2.0`)**: Core library for building the interactive user interface and managing state.
- **React DOM (`^19.2.0`)**: Handles web-specific rendering of the React component tree.
- **Tailwind CSS (`CDN`)**: Utility-first CSS framework for rapid and responsive UI styling.

### 2. Backend & AI Services (Third-Party)
- **@google/genai (`^1.30.0`)**: Official Google Gemini API SDK used to interact with the Gemini 2.5 Flash Image model for AI-driven image processing.

### 3. Infrastructure & Runtime Environment
- **Node.js**: The JavaScript runtime environment powering the local development server and build process.

### 4. Toolchain & Build Tools
- **Vite (`^6.2.0`)**: Next-generation frontend tooling providing an extremely fast development server and optimized production builds.
- **TypeScript (`~5.8.2`)**: Adds static typing to JavaScript, enhancing code quality, readability, and developer experience.
- **@vitejs/plugin-react (`^5.0.0`)**: Vite plugin that enables React support, including Fast Refresh.

## ⚙️ Environment Dependencies

To avoid environment conflicts, please ensure your system meets the following minimum requirements:

- **Node.js**: `>= 22.14.0` (Recommended: latest LTS version)
- **npm**: `>= 10.0.0` (Included with Node.js)
- **Modern Web Browser**: Chrome, Firefox, Edge, or Safari (supporting ES modules)

## 🚀 Local Deployment and Startup

### Prerequisites
You need a Google Gemini API Key to run this application. You can obtain one from Google AI Studio.

### Steps (Compatible with Windows, macOS, and Linux)

1. **Clone the repository (if applicable)**
   ```bash
   git clone <repository-url>
   cd gemini-lens---ai-image-editor
   ```

2. **Install project dependencies**
   ```bash
   npm install
   ```

3. **Configure Environment Variables**
   Create a `.env.local` file in the project root directory and add your API key:
   - **Windows (Command Prompt):**
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

4. **Start the development server**
   ```bash
   npm run dev
   ```

5. **Access the application**
   Open your browser and navigate to the address shown in the terminal (usually `http://localhost:3000` or `http://localhost:5173`).

## 📁 Project Structure

```text
├── components/          # Reusable UI components
│   ├── Button.tsx       # Standard button component
│   └── ImageUploader.tsx# Component for image selection and preview
├── services/            # Business logic and external API integrations
│   └── geminiService.ts # Service for interacting with Google GenAI SDK
├── App.tsx              # Main application root component
├── index.html           # HTML entry point containing Tailwind CDN
├── index.tsx            # React application mounting point
├── types.ts             # Global TypeScript interface definitions
├── vite.config.ts       # Vite build tool configuration
├── package.json         # Project metadata, scripts, and dependencies
├── tsconfig.json        # TypeScript compiler configuration
└── README.md            # Project documentation (this file)
```

## 📝 Development Guidelines

1. **Component Design**: Favor functional components and React Hooks. Keep components small, focused, and reusable.
2. **Styling**: Exclusively use Tailwind CSS utility classes for styling to ensure consistency. Avoid custom CSS files unless absolutely necessary.
3. **Type Safety**: Strictly define interfaces in `types.ts` or within the respective component files. Avoid using `any` type whenever possible.
4. **State Management**: Use React's built-in `useState` and `useCallback` for local state. For more complex state, elevate it to `App.tsx`.
5. **API Calls**: All interactions with external APIs must be abstracted within the `services/` directory to decouple business logic from UI components.

## ❓ FAQ & Troubleshooting

**Q: "An unexpected error occurred" when clicking Generate.**
* **A:** Check your browser console. This is often caused by an invalid `GEMINI_API_KEY`. Ensure your `.env.local` file is correctly formatted and the key is valid. Restart the development server (`npm run dev`) after modifying `.env.local`.

**Q: "Failed to load resource" for @google/genai in browser.**
* **A:** Verify that your internet connection allows access to `aistudiocdn.com`, as the SDK and React libraries are mapped via import maps in `index.html`.

**Q: Port already in use error.**
* **A:** If port 3000 is occupied, Vite will automatically try the next available port. If you want to force kill the process on port 3000, use:
  - macOS/Linux: `kill $(lsof -t -i :3000)`
  - Windows: `netstat -ano | findstr :3000` then `taskkill /PID <PID> /F`
