## Comparison and migration guide for Vite 3.0 vs. Create React App

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1662450844749/Re_bRji_V.png)

Create React App (CRA) has been instrumental in the growth of the React community and its ecosystem as a whole. When it comes to constructing a local React development environment on the fly, it is the tool of choice for developers of all skill levels.

CRA has several distinguishing features that make it difficult to overlook, the most notable of which are: local development server, Hot Module Replacement (HMR), and production bundling. However, CRA has a significant disadvantage in progressive speed and performance degradation.

The performance of Create React App degrades as an application grows in size and complexity, and the time it takes to start a development server increases significantly. This renders CRA unsuitable for production.

This guide will introduce Vite, an esbuild-based build tool. We’ll go over everything you need to know to get started with Vite and building React applications. We’ll also go over the differences between Vite and CRA and show you how to transition from Create React App to Vite.

![1662323245939486 0](https://i0.wp.com/lh3.googleusercontent.com/-_3l0PWpIuVo/YxUKMFi6-RI/AAAAAAAACaQ/QA8HeLvlK7YaWb2KITCpXncZhgbyQvslgCNcBGAsYHQ/s1600/1662323245939486-0.png?w=1290&ssl=1 "Comparison and migration guide for Vite 3.0 vs. Create React App 1")

Prerequisites
-------------

You’ll need the following to follow along with the tutorial portion of this article:

*   Node.js 14.18 or later
*   A browser that supports native ES modules (ESM) and dynamic imports; most modern browsers do.
*   A package manager like npm or Yarn

What exactly is Vite?
---------------------

Vite is a development tool designed to bridge the gap between current and next-generation web development. It focuses on giving developers and current web projects a faster and more performant experience.

Vite is built on esbuild, a Go-based JavaScript bundler that bundles dependencies 10-100 times faster than JavaScript-based bundlers.

Evan You, the creator of Vue.js, created Vite. It is, however, platform-independent, which means it can be used to develop JavaScript/TypeScript applications that support popular libraries such as React, Svelte, Preact, and even vanilla JavaScript.

Vite uses the browser’s native ESM to parse and compile your code as it is requested by the browser. The source file is then served using a plugin like Koa (a lightweight Node.js web server) to create a development server with support for Hot Module Replacement (HMR) for updating served modules and Rollup for production builds.

What are the workings of Vite and Create React App?
---------------------------------------------------

It’s not as different as you might think between Vite and CRA. They both serve a local development server and bundle codes for production, which is essentially what they both do. You’ll notice primary differences in the supported modules and how code is served during development.

By allowing developers to concentrate on their code rather than setting up build tools, the Create React App development environment aids in the acceleration of the development process.

CRA’s internal core functionalities are handled by a third-party build tool called webpack. Vite is actually up against this.

What is Webpack, then? Similar to Vite, webpack is a bundler for JavaScript modules. However, in contrast to Vite, Webpack supports multiple modules out of the box:

*   ESM
*   CommonJS
*   Asynchronous Module Definition (AMD) API

Webpack combines assets and modules into one or more static assets using any of these JavaScript module systems and then uses the Express.js web server and webpack-dev-server to serve content from the bundled asset with HMR support.

We’ll break down how both tools handle these functionalities in development to put things into perspective.

[Create React App in development](https://jainil.dev/react-cheat-sheet-for-beginners/)
--------------------------------------------------------------------------------------

The first thing webpack does when you start a CRA development is use the app’s entry point (the `index.js` file) to build a tree of dependencies from every module in the project.

The code is then transpired with Babel, bundled, and served using the Express.js web server. Last but not least, it prepares sockets for the Hot Module Replacement.

Although this method is quicker and allows you to concentrate on your code, it has a serious disadvantage.

![Comparison and migration guide for Vite vs. Create React App](https://i0.wp.com/www.eternaldev.com/static/8d2bca125a7ee84af38ab7e519532a02/f9218/bundlebasedevserver.jpg?w=1290&ssl=1 "Comparison and migration guide for Vite 3.0 vs. Create React App 2")

Vite in development
-------------------

However, before Vite starts serving your app, you only need to pre-bundle your dependencies using esbuild the first time you start development.

Vite is much faster than CRA because it doesn’t need to bundle the entire app or transpile the modules and code before starting a development server. Instead, transpiring is done as needed.

Instead of rebuilding and reloading the entire page like CRA, Vite uses route-based code-splitting to determine which portion of the code needs to be loaded after serving the app. It then parses the native ES modules from the app’s entry point using the browser.

This means that for each import, the browser will send an HTTP request back to the server after reading the `import` and `export` statements in your code. When necessary, the dev server intercepts the requests and transforms the code.

The browser simply ignores modules that haven’t been modified because they return a 304 “not modified” status code. The application keeps its state and the browser avoids having to reload.

Here is a diagram showing how the Vite was developed:

![Comparison and migration guide for Vite vs. Create React App](https://i0.wp.com/craftsmenltd.com/wp-content/uploads/2022/06/esc.png?resize=1060%2C663&ssl=1 "Comparison and migration guide for Vite 3.0 vs. Create React App 3")

Why should you use Vite?
------------------------

We previously discussed some of the benefits of using Vite for React app development. Let’s take a closer look at Vite’s advantages.

### Outstanding performance

Vite transforms dependencies that are shipped as CommonJS or UMD into ESM during the pre-bundling process. Because Vite only supports and serves native ESM codes by default, this conversion takes place.

For faster page loads, Vite can combine dependencies with multiple internal modules into a single module. These modules frequently send out hundreds of requests all at once, which may clog up the browser and slow download times. However, they only need to send one request because these dependencies have already been pre-bundled into a single file, improving overall performance.

### Plugin compatibility is extensive.

By enabling developers to rely on the established Rollup plugin ecosystem, Vite enhances the developer experience. In other words, Vite is ready to use with the majority of Rollup plugins.

### Quicker updates

We previously described how the size of the application has a significant negative impact on HMR speed in a bundled-based server.

HMR is applied to native ESM in Vite. A module that accepts hot updates only needs to be precisely invalidated by Vite when changes are made to it. No matter how large the application, this leads to a quicker HMR update time.

### Increased build speed

Vite creates production-ready apps using pre-configured Rollup. Vite’s build time typically runs faster than that of CRA because Rollup is a more effective bundler than Webpack, and its output is smaller.

Creating a React project in Vite 3.0
------------------------------------

To make a Vite app, open the terminal on your machine, `cd` to a preferred folder, and run the following command:

npm install vite@latest

The CLI will prompt you for a project name after you run the command. In this case, we’ll stick with the default name vite-project. Then, from the list of available templates, we’ll choose to react. This usually takes tens of seconds or less.

![Comparison and migration guide for Vite vs. Create React App](https://i0.wp.com/www.section.io/engineering-education/develop-and-deploy-fast-apps-with-vite-js/project-name.jpg?w=1290&ssl=1 "Comparison and migration guide for Vite 3.0 vs. Create React App 4")

Alternatively, you can specify your preferred template in the command to avoid the prompt.

You can do this by including the `--template` flag, followed by the name of the framework:

npm init vite@latest vite-project --template react

Next, navigate to the project folder, install any required dependencies, and launch the dev server using the following commands:

cd vite-project
npm install
npm run dev

Following the execution of these commands, a development server will be available on port 5173. Vite typically serves an application in 1325ms.

![Comparison and migration guide for Vite vs. Create React App](https://i0.wp.com/blog.logrocket.com/wp-content/uploads/2022/09/vite-ready-in-1325-ms.png?w=1290&ssl=1 "Comparison and migration guide for Vite 3.0 vs. Create React App 5")

Now open your browser and type **localhost:5173** into the address bar. You’ll see a page similar to the one below, complete with the iconic count button.

![Comparison and migration guide for Vite vs. Create React App](https://i0.wp.com/blog.logrocket.com/wp-content/uploads/2022/09/vite-and-react-page.png?w=1290&ssl=1 "Comparison and migration guide for Vite 3.0 vs. Create React App 6")

That’s all! We have successfully established a Vite React development environment!

The following section will go over how to migrate a Create React App project to Vite.

Migrating a Create React App project to Vite
--------------------------------------------

It’s not too difficult to migrate an existing CRA project to Vite.

Open `package.json` in your project folder, then `remove-react-scripts` from the list of dependencies as a first step:

  "dependencies": {
    ...
    "react-scripts": "5.0.1",
    ...
  }, 

Next, include a “`devDependencies`” with the information listed below:

  "devDependencies": {
    "@vitejs/plugin-react": "^2.0.1",
    "vite": "^3.0.7"
  },  

N.B., using the most recent version is always advised.

Replacing the scripts now

 "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  },

Including the following

  "scripts": {
    "start": "vite",
    "build": "vite build",
  }, 

Next, go to the `index.html` file inside the `Public` folder and remove every `%PUBLIC_URL%/`prefix in the link paths:

<link rel="icon" href="%PUBLIC\_URL%/favicon.ico" />

<link rel="apple-touch-icon" href="%PUBLIC\_URL%/logo192.png" />

<link rel="manifest" href="%PUBLIC\_URL%/manifest.json" />

Replace the prefix that was removed with the following:

<link rel="icon" href="./public/favicon.ico" />
 ...
<link rel="apple-touch-icon" href="./public/logo192.png" />
 ...
<link rel="manifest" href="./public/manifest.json" />

Then, add an entry point script inside the `body` element, just below the `root` div:

<script type="module" src="/src/index.jsx"></script>

But before you do this, rename every `.js` the file that contains React codes to a `.jsx` file. For example, you’d rename the `index.js` file `index.jsx`.

Then, move the `index.html` file to the root folder.

![Comparison and migration guide for Vite vs. Create React App](https://i0.wp.com/blog.logrocket.com/wp-content/uploads/2022/09/index-file.png?w=1290&ssl=1 "Comparison and migration guide for Vite 3.0 vs. Create React App 7")

The following steps are to create a Vite configuration file, delete the node modules folder, and reinstall the dependencies.

Begin by creating a `vite.config.js` file in the root directory and add the following code:

import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";

export default defineConfig({
  plugins: \[react()\],
})

Next, go to the root folder and delete the `node_modules` folder. Then, run the following command to reinstall the dependencies and start the development server:

npm install
npm start

The development server should now successfully boot up if you open your browser and navigate to localhost:5173.

![Comparison and migration guide for Vite vs. Create React App](https://i0.wp.com/fullstackcode.dev/wp-content/uploads/2022/01/vite-react-app-1536x826.png?resize=1290%2C694&ssl=1 "Comparison and migration guide for Vite 3.0 vs. Create React App 8")

Differences between Create React App and Vite
---------------------------------------------

We have compared the functions of CRA and Vite and discussed some advantages of using Vite over CRA. Let’s now examine some distinctions between these tools.

### Absolute imports

The difference in path resolving is probably the first thing you’ll notice when you start developing with Vite. Vite lacks an internal `src` path, unlike CRA.

As a result, use the following syntax to import files and components into your React app:

import Cards from "components/cards";

They must be imported in the following manner:

import Cards from “/src/components/cards.jsx”

Fortunately, this path resolving has a fix.

Open the `vite.config.js` file in the project’s root folder, then change the existing code:

import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";

export default defineConfig({
  plugins: \[react()\],
}); 

With the following:

import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";

export default defineConfig({
  resolve: {
    alias: \[
      {
        find: "common",
        replacement: resolve(\_\_dirname, "src/common"),
      },
    \],
  },

  plugins: \[react()\],
});

You should now be able to use absolute paths in your project after saving the code.

### Environment variables

The way environment variables are named in Create React App and Vite is another difference. You should substitute `VITE_` for `REACT_APP_` if your project makes use of environment variables.

//Instead of this 
REACT\_APP\_ API\_KEY = 1234567890..
//Use this
VITE\_API\_KEY = 1234567890..

It can be tedious to change each variable individually, especially if your `.env` file contains a large number of variables. Fortunately, we can use environment variables without changing their names thanks to the vite-plugin-env-compatible package.

To install the vite-plugin-env-compatible package, issue the following command:

npm i vite-plugin-env-compatible

Next, go to the `vite.config.js` file in the root folder of the project and add the following code:

import envCompatible from 'vite-plugin-env-compatible';

export default defineConfig({
    ...
  envPrefix: 'REACT\_APP\_',

  plugins: \[
    react(),
    envCompatible
  \],
});

Vite will be instructed to use variables with a `REACT_APP_` prefix by the `envPrefix` property. Environment variables can now be used in your project without having to change their names. You will still need to change `import.meta.env` in your code to replace `process.env`.

You can quickly locate and replace each process.env in your codebase by using the search feature in your IDE.

Conclusion
----------

In this article, we introduced Vite, contrasted its fundamental ideas with Create React Apps, and examined how both tools function during the development process. We also looked at Vite’s advantages and showed you how to convert a Create React App project to it.

<p>The post [Comparison and migration guide for Vite 3.0 vs. Create React App](https://jainil.dev/comparison-and-migration-guide-for-vite-3-0-vs-create-react-app/) first appeared on [Jainil Prajapati.](https://jainil.dev).</p>