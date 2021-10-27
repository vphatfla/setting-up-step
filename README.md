# setting-up-step
## My setting up project repo
#### Setting up webpack 

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
  entry: ['./src/index.js'],
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
        test: /\.(woff|woff2|eot|ttf|otf)$/i,
        type: 'asset/resource',
      },
    ],
  },
};


```
4. command setting css-loader
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
... enforce styles
CommonJS / javascript
None of these
No
Browser
Use the popular
Airbnb
file in JS
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
### Set up Jest.
1. Settup npm. // already has npm init
```
npm install --save-dev jest
```
2. file *.test.js // with import export
3. inside package.json:
```
"scripts": {
  ...
  "test": "jest",
  "watch": "jest --watch *sum.test.js"
},
 ``` 
example: *.test.js
```
const sum = require('./sum');

test('adds 1 + 2 to equal 3', () => {
  expect(sum(1, 2)).toBe(3);
});
```
# Make a gh-pages:
```
git subtree push --prefix dist origin gh-pages
```
