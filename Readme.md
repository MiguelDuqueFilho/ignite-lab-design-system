# commnds this project


```cmd 
npm install vite@latest

npm install -D tailwindcss postcss autoprefixer 

npx tailwindcss init -p
Created Tailwind CSS config file: tailwind.config.cjs
Created PostCSS config file: postcss.config.cjs

```

configuration tailwind.config.cjs

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    './src/**/*.tsx'
  ],
  theme: {
    extend: {
      fontFamily: {
        sans: 'Inter, sans-serif'
      }
    },
  },
  plugins: [],
}

```

create in styles/global.css 

```css
@tailwind base;
@tailwind utilities;
@tailwind components;
```

import in html head fonts inter 

```html
 <head>
    <meta charset="UTF-8" />
    <link rel="preconnect" href="https://fonts.googleapis.com"/>
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin/>
    
    <link rel="icon" type="image/svg+xml" href="/vite.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />

    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&family=Roboto+Mono:wght@700&display=swap" rel="stylesheet"/>
    
    <title>Lab Design System</title>
  </head>
```

storybook 

```cmd 
npx sb init --builder @storybook/builder-vite --use-npm
```

create .storybook/manager.js 

```js 
import { addons } from '@storybook/addons';
import { themes } from '@storybook/theming';

addons.setConfig({
  theme: themes.dark,
})
```

include in .storybook/preview.cjs 

```js
 docs: {
    theme: themes.dark,
  }
```
create repository github

```cmd 
gh repo create                                      
? What would you like to do? Push an existing local repository to GitHub
? Path to local repository .
? Repository name miguelduquefilho/ignite-lab-design-system
? Description Design desenvolvido durante o Ignite Lab 03
? Visibility Public
✓ Created repository MiguelDuqueFilho/ignite-lab-design-system on GitHub
? Add a remote? Yes
? What should the new remote be called? (origin) 
```

update .storybook/main.cjs

```js 
module.exports = {
  "stories": [
    "../src/**/*.stories.mdx",
    "../src/**/*.stories.@(js|jsx|ts|tsx)"
  ],
  "addons": [
    "@storybook/addon-links",
    "@storybook/addon-essentials",
    "@storybook/addon-interactions",
    "@storybook/addon-a11y"
  ],
  "framework": "@storybook/react",
  "core": {
    "builder": "@storybook/builder-vite"
  },
  "features": {
    "storyStoreV7": true
  },
  viteFinal: (config, { configType }) => {
    if (configType === 'PRODUCTION') {
      config.base = '/ignite-lab-design-system/'
    }
  }
}
```