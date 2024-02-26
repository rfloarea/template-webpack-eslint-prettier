# Template Repo
A template repo chock full of stuff from Webpack, ESLint, and Prettier

## What's in the box?

### Webpack stuff
Using the [Getting Started Guide](https://webpack.js.org/guides/getting-started/)

1. initialize npm, install webpack locally, and install the webpack-cli 
```
npm init
npm install webpack webpack-cli --save-dev
```
2. create .gitignore and add `node_modules/`
```
touch .gitignore
echo >> .gitignore "node_modules/"
```
3. create `./src/index.js` and `./dist/index.html` and `./dist/main.js`
```
mkdir src dist
touch src/index.js dist/index.html dist/main.js
```
4. create html boiler and link to `main.js`
`<script src="./main.js"></script>`
5. create and setup our Webpack config file
`touch webpack.config.js`
```
const path = require('path');

module.exports = {
  entry: './src/index.js',
  output: {
    filename: 'main.js',
    path: path.resolve(__dirname, 'dist'),
  },
};
```
6. add an npm script to our package.json file
`"build": "webpack"`
Now we can use `npm run build`.
7. install and add loaders to module config
In terminal: `npm install --save-dev style-loader css-loader`
In webpack.config.js: 
```
module: {
    rules: [
        {
        test: /\.css$/i,
        use: ['style-loader', 'css-loader'],
        },
    ],
},
```
8. UPdate config rules to handle images
```
{
    test: /\.(png|svg|jpg|jpeg|gif)$/i,
    type: 'asset/resource',
},
```
9. Update config rules to handle fonts
```
{
    test: /\.(woff|woff2|eot|ttf|otf)$/i,
    type: 'asset/resource',
},
```
10. Set up CSV, TSV, and XML loading
In terminal: `npm install --save-dev csv-loader xml-loader`
In config file:
```
{
    test: /\.(csv|tsv)$/i,
    use: ['csv-loader'],
},
{
    test: /\.xml$/i,
    use: ['xml-loader'],
},
```
11. Update config with `output.clean` to remove unused files from dist after builds
Within output: `clean: true,`
12. Update config to `development` mode, also with `inline-source-map`,
Above entry: `mode: 'development',`
Above module: `devtool: 'inline-source-map',`
13. Add an npm script for watch mode
`"watch": "webpack --watch"`

**Notable Absences**
1. No `HtmlWebpackPlugin`
2. Not using the `webpack-dev-server`


### ESLint stuff
Using the [Getting Started Guide](https://eslint.org/docs/latest/use/getting-started)


### Prettier stuff
Using the [Install guide](https://prettier.io/docs/en/install)