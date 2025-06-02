# Architecture

The front end is built in [React](https://reactjs.org/), and uses the following
major libraries:

- [CMS Design System](https://design.cms.gov) for standard page components and styling. This helps our app be visually compatible with other CMS web apps.
- [jsonpatch](https://www.npmjs.com/package/jsonpatch) for applying changes to redux state. When a state change arrives at the main APD data reducer, it computes a [JSON Patch](http://jsonpatch.com/) object and uses this handy library to apply it to the state. Saves us a bunch of trouble!
- [react-router](https://www.npmjs.com/package/react-router) for page routing. We use `react-router` beacuse it's pretty standard, well-documented, and well-supported.
- [redux](https://redux.js.org/) for internal state management. It's not always perfect, but it's kind of the go-to standard for flux-like data flows. In the future, it might be useful to spend some time investigating something like [redux-sagas](https://redux-saga.js.org/) to manage more complex action flows instead of managing a lot of complex logic in the actions themselves.
- [okta-auth-js](https://github.com/okta/okta-auth-js) for authenticating with Okta.
- [reselect](https://www.npmjs.com/package/reselect) for memoizing state selectors. Memoization is helpful to avoid repeating costly calculations if the inputs haven't changed.
- [Webpack](https://webpack.js.org/) for bundling the app into a deliverable. Because it's kinda the standard thing at the moment. We've got to turn all that JSX and Sass into browser-friendly code somehow!

We use [Sass](https://sass-lang.com/) to build our styles. We also lean heavily on the CMS Design System.

For testing, we use [Jest](https://facebook.github.io/jest/) as the test runner
and [Enzyme](http://airbnb.io/enzyme/) and [React-Testing-Library](https://testing-library.com/docs/react-testing-library/intro/) as a React renderers. We try to use Jest's stubs and mocks for testing now, but some of our older tests still use [Sinon.js](https://sinonjs.org/). We use Jest because it's a pretty good all-in-one framework, and its ability to capture snapshots makes it really nice for catching UI changes. 

![architecture-diagram](https://user-images.githubusercontent.com/62778/180575086-4c4fff47-a225-405b-9b48-7686bc962d51.png)


# Building

Our front end is built using Webpack. We use the [babel-loader](https://github.com/babel/babel-loader) along with the [env](https://webpack.js.org/plugins/environment-plugin/) plugin and the [react](https://babeljs.io/docs/en/babel-preset-react) and [stage-2](https://babeljs.io/docs/en/babel-preset-stage-2) Babel presets to build the Javascript parts of the app. We use the [sass-loader](https://github.com/webpack-contrib/sass-loader), [postcss-loader](https://github.com/postcss/postcss-loader), [css-loader](https://github.com/webpack-contrib/css-loader), and [mini-css-extract-plugin](https://github.com/webpack-contrib/mini-css-extract-plugin) for our styles.

Webpack injects some environment variables into the front end code. For example, in the code, references to `process.env.API_URL` are replaced at build time with the actual value of that environment variable. Here's the full list of environment variables that gets replaced:

| variable name | purpose                                      |
| ------------- | -------------------------------------------- |
| `API_URL`     | The base URL to the API. **default**: `null` |
| `IDLE_LOGOUT_TIME_MINUTES` | How long to allow the user's browser to sit idle before automatically logging them out. **default:**: `15` |

## Production

In production, our configuration chunks vendored Javascript files, compiles our Sass, and copies a variety of files from static sources.

| file/path               | where it comes from                                                             |
| ----------------------- | ------------------------------------------------------------------------------- |
| index.html              | Entry page, copied directly from `src/index.html`, unchanged                    |
| app.[hash].js           | The React app and all necessary libraries (entrypoint is `src/app.js`)          |
| app.css                 | Our primary styles, built from Sass (entrypoint is `src/styles/index.scss`)     |
| vendors~app.[hash].js   | Vendored code chunk, loaded at page load |
| vendors~zxcvbn.[hash].js| zxcvbn chunk, loaded on-demand |
| static                  | Images and other static resources, copied directly from `src/static`, unchanged |

The Javascript file hashes are content hashes, so as long as our 3rd-party libraries don't change, the vendor files should stay the same and can be cached by users' browsers.  Additionally, our Javascript is run through the
[webpack uglify plugin](https://github.com/webpack-contrib/uglifyjs-webpack-plugin)
to minify it.

## Development

In development, our configuration uses hot reloading to update the contents of
the browser without having to reload the page. Our Sass is build into CSS, is
injected into the app Javascript and is loaded via `<script>` tags, courtesy
of the [webpack style-loader](https://github.com/webpack-contrib/style-loader)
