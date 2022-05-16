---
title: "Setup React project from scratch"
date: 2022-05-16T07:45:00+05:30
draft: true
latex: true
tags: [react, setup, tech]
categories: React
---

Whenever it comes to working setting up a react project the first option that comes to our mind is `create-react-app`. I usually wondered what are some of the files that are created with it and how it creates the build etc. So, decided to give it a try to setup the full project from scratch. I will guide you through the tutorial how to do it and explain what each component does. Usually it is not recommended to people just starting with `JavaScript` and `NodeJS` world. I'll put some resources link if you want to explore that further.

### Prerequisite

-   Prior knowledge to NodeJS and `yarn` / `npm` package manager.

### Installing NodeJS

Install latest LTS version of NodeJS (as per your OS) from link given below. If you are stuck anywhere please go through the installation manual of NodeJS-

[Download | Node.js (nodejs.org)](https://nodejs.org/en/download/)

Note - If you installing it on `Linux` then you might need to install `npm` or `yarn` as well.

### Initializing project

Now it's time to fire up your favourite terminal 🖥️ -

Create a folder with your project name and open it in your terminal. First let's initialize a NodeJS project using following command -

For npm -

```bash
npm init -y
```

For yarn -

```bash
yarn init -y
```

you will see a `package.json` file created in project with some defaults. That's it now our project has been initialized as a NodeJS project.

### Adding react

Now it's time to add react to our project. we'll need at least `react` and `react-dom` dependencies to get started. Use following command to install dependencies

For npm -

```bash
npm install --save react react-dom
```

For yarn -

```bash
yarn add react react-dom
```

### Adding Babel

For compiling next-gen JavaScript code to a browser compatible version, we'll need babel. First let's install it's dependencies. As this is only used in development we'll add dev dependency as follows -

For npm -

```bash
npm install --save-dev @babel/core @babel/present-env @babel/react babel-loader
```

For yarn -

```bash
yarn add -D @babel/core @babel/present-env @babel/preset-react babel-loader
```

Now to configure babel, let's create a new file `.babelrc` wit following contents -

```json
{
	"presets": ["@babel/preset-react", "@babel/preset-env"]
}
```

### Adding webpack

Now it's time to introduce the most ignored and most important component in any JS frameworks. Webpack does a lot of thing which is a different topic altogether. For now I'll only explain the things we need -
first things first, let's add the dependencies -

For npm -

```bash
npm install --save-dev webpack webpack-cli webpack-dev-server
```

For yarn -

```bash
yarn add -D webpack webpack-cli webpack-dev-server
```

Once the installation is done we need to configure webpack to bundle our `js` `css` and other files together. create a file `webpack.config.js` with following contents -

```javascript
const path = require("path");

module.exports = {
	entry: "./src/index.js",
	output: {
		filename: "bundle.[hash].js",
		path: path.resolve(__dirname, "dist"),
	},
	plugins: [],
	resolve: {
		modules: [__dirname, "src", "node_modules"],
		extensions: ["*", ".js", ".jsx"],
	},
	module: {
		rules: [
			{
				test: /\.jsx?$/,
				exclude: /node_modules/,
				use: ["babel-loader"],
			},
		],
	},
	devServer: {
		port: 3000,
		compress: true,
	},
};
```

There are a lot of things here let's understand them one by one -

1. `entry` defines the starting point for webpack from which it should parse.
2. `output:filename` defines the final bundled file name. `[hash]` will create the hash value of the bundle and use it there.
3. `output:path` defines the path at which we should but our bundled files.
4. `resolve:modules` tells webpack what directories should be searched when resolving modules.
5. `resolve:extensions` attempt to resolve these extensions in order given.
6. `module:rules` defines multiple rules for resolving the files and extensions
    1. `test` regex matching files to resolve with this rule
    2. `exclude` while resolving exclude these paths.
    3. `use` define multiple loaders to resolve the files and these **_order is right to left_**
7. `devServer` defines properties for dev-server
    1. `port` port at which it should start a live server
    2. `compress` compress the bundled files using gzip compression.

Hope you might have got the idea about it, we'll be working with it more as we move along.
