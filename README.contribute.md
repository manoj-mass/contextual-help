# Contributing

## Overview

The use of Bower for dependencies is not sanctioned in Origami v2. Use npm with webpack or browserify instead.

| **Tech** | **Description** |**Learn More**|
|----------|-------|---|
| [React](https://facebook.github.io/react/)  |   Fast-rendering, composable client-side components.    | [Powering Up with React](https://www.codeschool.com/courses/powering-up-with-react) |
| [React Intl](https://github.com/yahoo/react-intl/wiki) | (see demo) API to handle translations, format dates, numbers, and strings. | |
| [Babel](http://babeljs.io) |  Compiles ES6 to ES5 to enjoy the new version of JavaScript today. Also transpiles JSX via babel-preset-react. | [ES6 REPL](https://babeljs.io/repl/), [ES6 vs ES5](http://es6-features.org), [ES6 Katas](http://es6katas.org), [Pluralsight course](https://www.pluralsight.com/courses/javascript-fundamentals-es6)    |
| [Webpack](http://webpack.github.io) | Bundles npm packages and our JS into a single file. Includes source maps and hot reloading via [webpack-dev-server](https://webpack.github.io/docs/webpack-dev-server.html). | [Quick Webpack How-to](https://github.com/petehunt/webpack-howto) [Pluralsight Course](https://www.pluralsight.com/courses/webpack-fundamentals)|
| [Jest](https://facebook.github.io/jest/) | Automated unit tests with [Enzyme](http://airbnb.io/enzyme/) for DOM testing without a browser. | [Jest & Enzyme](https://www.codementor.io/vijayst/unit-testing-react-components-jest-or-enzyme-du1087lh8), [Pluralsight Course](https://www.pluralsight.com/courses/jest-mastering-react-testing) |
| [ESLint](http://eslint.org/) | Lint JavaScript as configured in the .eslintrc. Reports syntax and style issues. Using [eslint-plugin-react](https://github.com/yannickcr/eslint-plugin-react) for additional React-specific linting rules. | |
| [SCSS](http://sass-lang.com/documentation/file.SCSS_FOR_SASS_USERS.html) | Compiled CSS styles with variables, mixins, and more. | [Pluralsight Course](https://www.pluralsight.com/courses/better-css)|
| [Npm Scripts](https://docs.npmjs.com/misc/scripts) | Glues all this together in a handy automated build. | [Pluralsight course](https://www.pluralsight.com/courses/npm-build-tool-introduction), [Why not Gulp?](https://medium.com/@housecor/why-i-left-gulp-and-grunt-for-npm-scripts-3d6853dd22b8#.vtaziro8n)  |

This archetype includes a working example component that puts the above to use.

## Cross-browser Compatibility

Inform the consumers of this component in [README.usage.md](README.usage.md) of any necessary polyfills and how to use
[Polyfill.io](https://cdn.polyfill.io/v2/docs/examples) to construct requests for specific browser features.

## Continuous Integration

For Origami's SaaS-based continuous integration, PDA must enable a web hook.

Please send your request for one of the following GitHub or BitBucket options to: pearson-design-accelerator@pearson.com
or [HipChat](https://pearson.hipchat.com/chat/room/1469228)

### GitHub

GitHub repositories will integrate with [Travis CI](https://travis-ci.org/Pearson-Higher-Ed/), which will publish to the
 **public** scope in Pearson's npm organization.

### BitBucket

BitBucket repositories will integrate with [Solano CI](https://ci.solanolabs.com), which will publish to the **private**
scope in Pearson's npm organization.

## Initial Machine Setup
1. Install [Git](https://git-scm.com/downloads).
2. Install [Node 4.0.0 or greater](https://nodejs.org) - Need to run multiple versions of Node? Use [nvm](https://github.com/creationix/nvm).
3. On a Mac? You're all set. If you're on Windows, complete the steps for your OS below.

**On Windows:**

1. Install Ruby as the runtime engine for SCSS.
2. Install [Python 2.7](https://www.python.org/downloads/). Some node modules may rely on node-gyp, which requires Python on Windows.

### Quick Start

See the project working before changing anything!

In your local repo:

    npm install
    npm start

Navigate to: **localhost:8081/component-archetype/**

#### Where are the files being served from?

Webpack serves your component in memory when you `npm start`. No physical files are written. When the component is
built using `npm run build`, physical files are written to /build.

Additionally, Hot Module Replacement is activated in the webpack dev server; saved changes to /src are automatically
reloaded in the browser.  Rendering changes to the demo/index.html itself, however, does require a manual page refresh.

### Using ElementsSDK

Pearson has created a base styling library to assist developers in creating a user interface with styles that are
pre-approved by the design team, known as the ElementsSDK.  This is used for demo purposes here, but it is possible that
the component archetype demo does not pull in the latest version.  Should it be necessary, please update the package.json
file to reflect the current version of [ElementsSDK](https://github.com/Pearson-Higher-Ed/elements).


### Unit Test

The project is wired to unit test with the popular [Jest](https://facebook.github.io/jest/) framework and the [expect](https://github.com/mjackson/expect) assertion library.

It is also enabled for the following options:

- [shallow rendering](https://facebook.github.io/react/docs/test-utils.html#shallow-rendering) with React's test utilities

- Rendering a component into a detached DOM node in the document, using [jsdom](http://jaketrent.com/post/testing-react-with-jsdom/)

- Airbnb's [Enzyme](http://airbnb.io/enzyme/) for DOM manipulation and traversal

Code coverage report generated by Jest when the tests are run.  The report can be viewed when you run:

    npm test

    npm start

    go to ---> http://localhost:8081/coverage/lcov-report/

if you've deployed your project to GitHub Pages as detailed above:

    go to ---> http://pearson-higher-ed.github.io/component-archetype/coverage/lcov-report/

Linting will run automatically prior to executing the test suite.

    npm test

### Functional Test

When ready, turn on Selenium-based automated testing for QA, by **un-commenting** `./test/shell_scripts/run_tests.sh`
in the CI configuration (.travis.yml or solano.yml).

### Spec Compliance

Determine if your component passes a series of checks for Origami v2 compliance.

    npm run verify

### GitHub Pages
The component demo can be deployed to GitHub Pages by:

    npm run gh-pages

The page can then be viewed at:

  [http://pearson-higher-ed.github.io/component-archetype](http://pearson-higher-ed.github.io/component-archetype)

### Translations for Internationalization

It is recommended to use the [React Intl](https://github.com/yahoo/react-intl/wiki) library for internationalization.

It is expected that applications will pass in translated text for dynamic and static content, and your component simply
needs to render whatever is passed in.

### Publish to Pearson npm Registry

FOR PUBLIC PACKAGES ONLY, add the following npm script to the package.json:

    "postpublish": "npm access public && echo 'Package scope set to public!'"

**Do not manually version or tag your project**. Instead, when you are ready to publish an update to npm, manually run
the release script in the master branch. It handles all of that and publishes to npm on your behalf using the
pearson-ux account.

Additionally, there is no need to manually maintain a change log - if you follow the
[commitizen](https://commitizen.github.io/cz-cli/) conventions for commit messages, a change log will automatically be
generated during the release process.

Before you run the release script, ensure that you don't have to manually authenticate every time you perform a network
operation with Git.

    npm run release

### How do I debug?

Source maps are enabled for the webpack dev server. Using Chrome's dev tools - open the "Sources" tab, navigate to
`top/webpack://./`, and you will find the original source files for which you can set breakpoints in Chrome's debugger.

To take advantage of source maps, you must enable JavaScript source maps in your browser.

Optionally, install [React developer tools](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en)
for additional React debugging support in Chrome dev tools under the "React" tab.