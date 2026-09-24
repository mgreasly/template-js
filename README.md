# Nano React App Default JavaScript Template

The default template project for [nano-react-app](https://github.com/nano-react-app/nano-react-app).

## Getting started

Use Node.js 20.19 or later within the 20.x release line, or Node.js 22.12 or later, with npm. A current LTS release is recommended.

```sh
npm install
npm start
```

- `npm start` starts the development server on port `5173` by default.
- `npm run build` creates a production build in `dist`.
- `npm run preview` serves the production build locally on port `4173` by default. Run `npm run build` first. Preview is for local checks, not production hosting.

Vite tries the next available port if the default port is in use. Check the terminal output for the actual URL.

## Custom port

Use `--port` to choose a development port:

```sh
npm start -- --port 3000
```

The same option works with preview:

```sh
npm run preview -- --port 3000
```

In Windows PowerShell, if options are not forwarded correctly, use `npm.cmd` instead of `npm`, for example `npm.cmd start -- --port 3000`.

## Adding styles

Create a CSS file and import it from your JavaScript:

```js
import "./index.css";
```

## React development

The [React plugin for Vite](https://github.com/vitejs/vite-plugin-react) is configured in [vite.config.mjs](vite.config.mjs). It enables React Fast Refresh, preserving component state during supported edits, and the automatic JSX runtime, so JSX does not need an `import React` statement.

The app uses React Strict Mode to enable additional development checks. Components may render an extra time, and effects receive an extra setup and cleanup cycle in development. These checks do not affect production builds.

## Deploy to GitHub Pages

Install [gh-pages](https://github.com/tschaub/gh-pages):

```sh
npm install --save-dev gh-pages
```

For a project site at `https://USERNAME.github.io/REPOSITORY/`, update the scripts in [package.json](package.json), replacing `REPOSITORY` with your repository name:

```json
{
  "scripts": {
    "start": "vite",
    "preview": "vite preview",
    "build": "vite build --base=/REPOSITORY/",
    "predeploy": "npm run build",
    "deploy": "gh-pages -d dist"
  }
}
```

The `base` option makes asset URLs work under the repository path. For a user or organisation site at `https://USERNAME.github.io/`, or a custom domain served at its root, keep `"build": "vite build"` instead.

Run `npm run deploy`. The `predeploy` script builds the app first; Vite clears the default `dist` directory automatically. These commands work on Windows, macOS, and Linux.

In the repository's GitHub Pages settings, choose "Deploy from a branch", select `gh-pages`, and use the root folder.
