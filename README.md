# setting-up-step
##My setting up project repo
####Setting up webpack 

1. Setting up files
```
<file>
  dist
    index.html
  src
    index.js
    style.css
```
2. Webpack commands
```
npm init -y
npm install webpack webpack-cli --save-dev
```
3. Config
```
  dist
    index.html
  src
    index.js
    style.css
 +webpack.config.js 
```
inside webpack.config.js
```
const path = require('path');

module.exports = {
  mode: 'development',
  entry: './src/index.js',
  devtool: 'inline-source-map',
  output: {
    filename: 'main.js',
    path: path.resolve(__dirname, 'dist'),
  },
  module: {
    rules: [
      {
        test: /\.css$/i,
        use: ['style-loader', 'css-loader'],
      },
      {
        test: /\.(png|svg|jpg|jpeg|gif)$/i,
        type: 'asset/resource',
      },
      {
        test: /\.m?js$/,
        exclude: /node_modules/,
        use: {
          loader: 'babel-loader',
          options: {
            presets: [
              ['@babel/preset-env', { targets: 'defaults' }],
            ],
            plugins: ['@babel/plugin-proposal-class-properties'],
          },
        },
      },
    ],
  },
};

```
4. command setting babel-loader
```
npm install -D babel-loader @babel/core @babel/preset-env webpack

```
5. command setting css-loader
```
npm install --save-dev style-loader css-loader
```
##seting up eslint
1. command
```
npm install eslint --save-dev
```
2. ctrl+p
```
./node_modules/.bin/eslint --init
```
3. select
```
To check syntax and find problems
CommonJS
None of these
No
Browser
Use the popular
Airbnb
```
4. customize .eslint.js
```
module.exports = {
  env: {
    browser: true,
    commonjs: true,
    es2021: true,
    node: true,
  },
  extends: [
    'airbnb-base',
  ],
  parserOptions: {
    ecmaVersion: 12,
  },
  rules: {
    'no-console': 'off',
  },
};
```
5. creat .eslintignore
```
touch .eslintignore
```
inside .eslintignore
```
dist/main.js
```
