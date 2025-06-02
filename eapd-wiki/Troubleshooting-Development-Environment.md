### Cypress Error - The plugins file is missing invalid

The error:

```
**An unexpected error occurred**

The plugins file is missing invalid.

Your `pluginsFile` is set to `.../eAPD/integrationTests/cypress/plugins/index.js`,
but either the file is missing, it contains a syntax error, or threw an error when required.
The `pluginsFile` must be a `.js`, `.ts`, `.coffee` file.

Or you might have renamed the extension of your `pluginsFile`.
If that's the case, restart the test runner.

Please fix this, or set `pluginsFile` to `false` if a plugins file is not necessary for your project.

`Error: Cannot find module 'knex'`

Stack trace
```


Remove node_modules and package-lock.json.

`rm -rf node_modules` `rm -rf package-lock.json`

and then run

`npm install`

(You may also have to reinstall cypress.)


***

### node-gyp error

https://blog.logrocket.com/solving-common-issues-node-gyp/
https://link.medium.com/GaRAz8l4Blb
