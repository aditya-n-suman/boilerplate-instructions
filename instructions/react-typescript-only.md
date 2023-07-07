This is the updated boilerplate without the support for JavaScript (JS) and JSX files:

Step 1: Set up a new project directory
Create a new directory for your project and navigate into it:
```
mkdir react-boilerplate
cd react-boilerplate
```

Step 2: Initialize a new npm project
Initialize a new npm project by running the following command and following the prompts:
```
npm init
```

Step 3: Install necessary dependencies
Install the required dependencies for your project:
```
npm install react react-dom
npm install --save-dev typescript webpack webpack-cli webpack-dev-server ts-loader
npm install --save-dev eslint eslint-config-prettier eslint-plugin-prettier eslint-plugin-react eslint-plugin-react-hooks
npm install --save-dev prettier @testing-library/react @testing-library/jest-dom ts-jest
```

Step 4: Create necessary configuration files
Create a `tsconfig.json` file in the root of your project and add the following content:
```json
{
  "compilerOptions": {
    "target": "es5",
    "lib": ["dom", "dom.iterable", "esnext"],
    "allowJs": false,
    "skipLibCheck": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,
    "strict": true,
    "forceConsistentCasingInFileNames": true,
    "module": "esnext",
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "react-jsx"
  },
  "include": ["src"]
}
```

Create a `webpack.config.js` file in the root of your project and add the following content:
```javascript
const path = require('path');

module.exports = {
  entry: './src/index.tsx',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'bundle.js',
  },
  resolve: {
    extensions: ['.tsx', '.ts'],
  },
  module: {
    rules: [
      {
        test: /\.tsx?$/,
        use: 'ts-loader',
        exclude: /node_modules/,
      },
    ],
  },
  devServer: {
    contentBase: path.join(__dirname, 'dist'),
    compress: true,
    port: 3000,
  },
};
```

Create an `.eslintrc.json` file in the root of your project and add the following content:
```json
{
  "parser": "@typescript-eslint/parser",
  "plugins": [
    "react",
    "react-hooks",
    "@typescript-eslint",
    "prettier"
  ],
  "extends": [
    "eslint:recommended",
    "plugin:react/recommended",
    "plugin:react-hooks/recommended",
    "plugin:@typescript-eslint/recommended",
    "prettier"
  ],
  "env": {
    "browser": true,
    "es6": true,
    "jest": true
  },
  "parserOptions": {
    "ecmaVersion": 2018,
    "sourceType": "module"
  },
  "rules": {
    "prettier/prettier": "error",
    "react/prop-types": "off"
  },
  "settings": {
    "react": {
      "version": "detect"
    }
  }
}
```

Create a `.prettierrc` file in the root of your project and add the following content:
```json
{
  "printWidth": 80,
  "tabWidth": 2,
  "useTabs": false,
  "semi": true,
  "singleQuote": true,
  "jsxSingleQuote": false,
  "trailingComma": "es5",
  "bracketSpacing": true,
  "jsxBracketSameLine": false,
  "arrowParens": "avoid",
  "proseWrap": "preserve"
}
```

Create a `jest.config.js` file in the root of your project and add the following content:
```javascript
module.exports = {
  preset: 'ts-jest',
  testEnvironment: 'jsdom',
  setupFilesAfterEnv: ['@testing-library/jest-dom/extend-expect'],
  moduleNameMapper: {
    '\\.(css|less|scss|sass)$': 'identity-obj-proxy',
    '\\.(jpg|jpeg|png|gif|svg)$': '<rootDir>/__mocks__/fileMock.js'
  },
  transform: {
    '^.+\\.(ts|tsx)$': 'ts-jest'
  },
  testMatch: ['<rootDir>/src/**/*.test.(ts|tsx)'],
  moduleFileExtensions: ['ts', 'tsx', 'json', 'node']
};
```

Step 5: Create a basic React component
Create a `src` directory in the root of your project and inside it, create an `index.tsx` file with the following content:
```tsx
import React from 'react';
import ReactDOM from 'react-dom';

const App: React.FC = () => {
  return <h1>Hello, React!</h1>;
};

ReactDOM.render(<App />, document.getElementById('root'));
```

Step 6: Start the development server
Open the `package.json` file in the root of your project and update the `"scripts"` section as follows:
```json
"scripts": {
  "start": "webpack-dev-server --mode development",
  "build": "webpack --mode production",
  "test": "jest"
}
```

Step 7: Start the development server
You can now start the development server by running the following command:
```
npm start
```

Open your browser and navigate to `http://localhost:3000`, and you should see your React app running with the "Hello, React!" message.

To run tests, use the following command:
```
npm test
```

That's it! You now have a final React boilerplate app set up with TypeScript, Webpack, ESLint, Prettier, and React Testing Library. The configuration files are included, and the app uses TypeScript and TSX files exclusively, without any support for JavaScript (JS) or JSX files.
