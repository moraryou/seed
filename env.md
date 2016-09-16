# Environment variables

Sometimes it is practical to have different config values according to the environment that the application is running in.

As an example:

```js
// config/prod.env.js
module.exports = {
  NODE_ENV: '"production"',
  DEBUG_MODE: false,
  API_KEY: '"..."' // this is shared between all environments
}

// config/dev.env.js
module.exports = merge(prodEnv, {
  NODE_ENV: '"development"',
  DEBUG_MODE: true // this overrides the DEBUG_MODE value of prod.env
})
```

> **Note:** string variables need to be wrapped into single and double quotes `'"..."'`

So, the environment variables are:
- Production
    - NODE_ENV   = 'production',
    - DEBUG_MODE = false,
    - API_KEY    = '...'
- Development
    - NODE_ENV   = 'development',
    - DEBUG_MODE = true,
    - API_KEY    = '...'

As we can see, the `dev.env` inherits the `prod.env`.

### Usage

It is simple to use the environment variables to your code. For example:

```js
Vue.config.debug = process.env.DEBUG_MODE
```