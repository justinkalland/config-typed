# config-typed

Configuration through process.env in the spirit of TypeScript

This is a placeholder for an idea I want to build. It is the next evolution of my [`config-twelve`](https://github.com/justinkalland/config-twelve) module.

## The problem

Street standard for Node.js configuration is using environment variables (see [third factor](https://12factor.net/config)). It is also common practice to use [`dotenv`](https://www.npmjs.com/package/dotenv) for development. The problem is that it is weak typed and requires lots of handling for validation. How many times have you had a issue with missing or invalid environment variables? For example:
- `process.env` forces all of it's properties to be strings.
- I use `process.env.BASE_URL` in my config and locally provide `https://127.0.0.1:8080` but another engineer deploys to production with `https://prod.com/` _(notice the trailing slash)_. Did I write logic to account for this?
- Dealing with truthy and falsey values can be tricky. If `process.env.LOG_TRANSACTIONS === undefined` is that false? What about `process.env.LOG_TRANSACTIONS === 'yes'`?
- Windows env variables are case-sensitive, while in Linux the aren't
- Forgot to setup a new environment variable when deploying
- 


## The solution

I aim for `config-typed` to provide a TypeScript module that:
- Requires you to define env variables for the application (even if optional)
- Throws fatal exception for missing (required) variables
- Validates the variables (strictly typed)
- Supports defaults for optional 
- Gives benefits of IDE auto complete afforded by TypeScript

