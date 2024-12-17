### Frontend Starter Kit (VITE+Shadcn+Tailwind+MagicUi+BoilerPlate)

### Step 1: Create a New Vite Project

1. Open your terminal and run the following command to create a new Vite project:
   ```bash
   npm create vite@latest my-shadcn-project -- --template react
   ```
   Replace `my-shadcn-project` with your desired project name.

2. Navigate to your project directory:
   ```bash
   cd my-shadcn-project
   ```

### Step 2: Install Dependencies

1. Install the necessary packages, including **Tailwind CSS** and **Shadcn UI**:
   ```bash
   npm install tailwindcss postcss autoprefixer
   ```

2. Initialize Tailwind CSS:
   ```bash
   npx tailwindcss init -p
   ```

### Step 3: Configure Tailwind CSS

1. Open the `tailwind.config.js` file and configure the content paths:
   ```javascript
/** @type {import('tailwindcss').Config} */
export default {
  darkMode: ["class"],
  content: [
    "./index.html",
    "./src/**/*.{js,jsx,ts,tsx}", // Include all JS/JSX files
  ],
  theme: {},
  plugins: [],
};

   ```

2. In your `src/index.css` file (or create it if it doesn't exist), add the following Tailwind directives:
   ```css
   @tailwind base;
   @tailwind components;
   @tailwind utilities;
   ```

### Step 4: Create `jsconfig.json`

Since you are using JavaScript, create a `jsconfig.json` file in the root of your project to enable path aliases:

```json
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/*": ["./src/*"],
      "@components/*": ["./src/components/*"],
      "@assets/*": ["./src/assets/*"]
    }
  },
  "include": ["./src/**/*"]
}

```

### Step 5: Update `vite.config.js`

Make sure to configure your Vite setup to resolve the path alias. Open `vite.config.js` and add the following code:

```javascript
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react-swc"; // Using SWC for faster builds
import path from "path";
//do "npm install -D @types/node"


// https://vitejs.dev/config/
export default defineConfig({
  css: {
    postcss: "./postcss.config.js", // Specify PostCSS configuration
  },
  resolve: {
    alias: {
      "@": path.resolve(__dirname, "./src"), // Set up alias for src directory
      "@components": path.resolve(__dirname, "./src/components"), // Alias for components
      "@assets": path.resolve(__dirname, "./src/assets"), // Alias for assets
    },
  },
  plugins: [react()], // Include React plugin
});

```

### Step 6: Install Shadcn UI

Run the following command to initialize Shadcn UI in your project:

```bash
npm i shadcn/ui
npx shadcn-ui@latest init

or 
 (main)use this
npx shadcn@latest init
npx shadcn@latest add card button

```

During this process, you'll be prompted to answer several configuration questions. Since you're using JavaScript, select options that suit your needs (like not using TypeScript).

### Step 7: Add Components

To add a component, such as a button, run:

```bash

npx shadcn-ui@latest add button or npx shadcn@latest add button
```

This command will prompt you to specify where to place the component; typically, you can use `./src/components/ui`.

### Step 8: Use Shadcn UI Components

Now that you have set up everything, you can start using Shadcn UI components in your application. Open `src/App.jsx` and modify it as follows:

```javascript
import React from 'react';
import { Button } from '@/components/ui/button'; // Adjust the import according to your structure

function App() {
  return (
    <div className="h-screen flex flex-col justify-center items-center gap-4 bg-gray-100">
      <h1 className="text-4xl font-semibold">Welcome to Shadcn UI with Vite!</h1>
      <Button onClick={() => alert('Button clicked!')}>Click Me</Button>
    </div>
  );
}

export default App;
```

### Step 9: Run Your Project

Finally, run your Vite project:

```bash
npm run dev
```

Open your browser and go to `http://localhost:5173` (or whatever port Vite is running on) to see your application with Shadcn UI components in action.

### Summary

By following these steps, you will have successfully set up a Vite project using Shadcn UI with JavaScript (JSX). You can now start building your application with beautiful UI components provided by Shadcn.

Citations:
[1] https://stackoverflow.com/questions/76689520/can-shadcn-ui-be-installed-for-vite-react-with-javascript-and-not-typescript
[2] https://www.youtube.com/watch?v=vGiYuaquCo4
[3] https://www.youtube.com/watch?v=8PDFi4cKjuI
[4] https://blog.ashutoshtiwari.co.in/how-to-build-a-react-ui-component-library-a-step-by-step-guide-using-shadcn-ui-vite-tailwind-36c1b89e2113
[5] https://github.com/ahmad1702/shadcn-ui-vite
[6] https://www.youtube.com/watch?v=gXSC5eMw68o
[7] https://github.com/dan5py/react-vite-shadcn-ui
[8] https://chapimaster.com/how-to-setup-shadcn-ui-in-react-using-vite-step-by-step