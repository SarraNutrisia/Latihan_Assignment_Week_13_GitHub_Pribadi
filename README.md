# Documentation 📚


🔎 **_This is assignment for Week 13 on Revou FSSE Section Seoul._** 🔎



*Theme Name :* Unit Testing Component Simple Weather React Application With Jest in React Next Js

*Author :* Sarra Nutrisia

*Created :* 31/01/2024 

*HTML Version :* HTML 5

*CSS Version :* CSS 3

*Node Js Version :* 18.17.0




This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `pages/index.tsx`. The page auto-updates as you edit the file.

[API routes](https://nextjs.org/docs/api-routes/introduction) can be accessed on [http://localhost:3000/api/hello](http://localhost:3000/api/hello). This endpoint can be edited in `pages/api/hello.ts`.

The `pages/api` directory is mapped to `/api/*`. Files in this directory are treated as [API routes](https://nextjs.org/docs/api-routes/introduction) instead of React pages.

This project uses [`next/font`](https://nextjs.org/docs/basic-features/font-optimization) to automatically optimize and load Inter, a custom Google Font.

## Installer for unit testing

First thing first, before testing the code, you have to install libraries through terminal or CLI as follows :

1. npm install -D jest jest-environment-jsdom @testing-library/react @testing-library/jest-dom
2. npm init jest@latest (for jest config) and choose:
    - ✔ Would you like to use Jest when running "test" script in "package.json"? … yes
    - ✔ Would you like to use Typescript for the configuration file? … yes
    - ✔ Choose the test environment that will be used for testing › jsdom (browser-like)
    - ✔ Do you want Jest to add coverage reports? … yes
    - ✔ Which provider should be used to instrument code for coverage? › babel
    - ✔ Automatically clear mock calls and instances between every test? … no
3. npm i -D ts-node
4. npm i --save-dev @types/jest
5. npm install --save-dev @babel/preset-typescript
6. npm install --save-dev @babel/preset-typescript @babel/preset-react
7. npm i -D @babel/preset-env
8. npm install @testing-library/jest-dom --save-dev

## Setting config file for testing

1. Create file babel.config.js on your project and add this code
```javascript
module.exports = {
  presets: [`@babel/preset-env`, `@babel/preset-react`]
};
```

2. Create or change file into jest.config.ts and add this code
```javascript
import type { Config } from 'jest';
import nextJest from 'next/jest.js';

const createJestConfig = nextJest({
  // Provide the path to your Next.js app to load next.config.js and .env files in your test environment
  dir: './',
});

// Add any custom config to be passed to Jest
const config: Config = {
  coverageProvider: 'v8',
  testEnvironment: 'jsdom',
  moduleNameMapper: {
     '^@/components/(.*)$': '<rootDir>/components/$1',
  },
    
  // Add more setup options before each test is run
  // setupFilesAfterEnv: ['<rootDir>/jest.setup.ts'],
};

// createJestConfig is exported this way to ensure that next/jest can load the Next.js config which is async
export default createJestConfig(config);
```

3. Or you can copy this file package.json and paste to your package.json (dont forget to change the name of your project, version and npm install after that)
```javascript
{
  "name": "assignment_week_13",
  "version": "0.1.0",
  "private": true,
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "next lint",
    "test": "jest"
  },
  "dependencies": {
    "@emotion/react": "^11.11.3",
    "@emotion/styled": "^11.11.0",
    "@mui/icons-material": "^5.15.6",
    "@mui/material": "^5.15.6",
    "@mui/styled-engine-sc": "^6.0.0-alpha.13",
    "axios": "^1.6.5",
    "formik": "^2.4.5",
    "js-cookie": "^3.0.5",
    "next": "14.1.0",
    "next-cookies": "^2.0.3",
    "next-iron-session": "^4.2.0",
    "node-fetch": "^3.3.2",
    "react": "^18",
    "react-dom": "^18",
    "styled-components": "^6.1.8",
    "yup": "^1.3.3"
  },
  "devDependencies": {
    "@babel/preset-env": "^7.23.9",
    "@babel/preset-react": "^7.23.3",
    "@babel/preset-typescript": "^7.23.3",
    "@testing-library/jest-dom": "^6.4.0",
    "@testing-library/react": "^14.2.0",
    "@types/jest": "^29.5.11",
    "@types/node": "^20",
    "@types/react": "^18",
    "@types/react-dom": "^18",
    "autoprefixer": "^10.0.1",
    "eslint": "^8",
    "eslint-config-next": "14.1.0",
    "jest": "^29.7.0",
    "jest-environment-jsdom": "^29.7.0",
    "postcss": "^8",
    "tailwindcss": "^3.3.0",
    "ts-node": "^10.9.2",
    "typescript": "^5"
  }
}
```

4. Matching tsconfig.json into this code
```javascript
{
  "compilerOptions": {
    "target": "es5",
    "lib": ["dom", "dom.iterable", "esnext"],
    "allowJs": true,
    "skipLibCheck": true,
    "strict": true,
    "noEmit": true,
    "esModuleInterop": true,
    "module": "esnext",
    "moduleResolution": "bundler",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "jsx": "preserve",
    "incremental": true,
    "paths": {
      "@/*": ["./src/*"]
    }
  },
  "include": ["next-env.d.ts", "**/*.ts", "**/*.tsx"],
  "exclude": ["node_modules"]
}
```

## Add file for npm run dev after testing

1. Create file next.config.js on your project and add this code
```javascript
module.exports = {
  experimental: {
    forceSwcTransforms: true,
  },
}
```

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.


# Deployment Link 🚀
You can check the Deployment of this website by clicking this link : [Link Netlify](https://main--warm-donut-b2d347.netlify.app/) 
  
***

#### Theme by Sarra Nutrisia &#127776;
If you have any other questions that aren't covered in the documentation, feel free to e-mail &#128233; <sarra.nutrisia@gmail.com>.