### create project

```
npm create vite@latest my-project -- --template vue
cd my-project
```

### install tailwind

```
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

### configure template paths in tailwind.config.js

```
  content: [
    "./index.html",
    "./src/**/*.{vue,js,ts,jsx,tsx}",
  ],
```

### add Tailwind directives to style.css

```
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### run build process

```
npm run dev
```
