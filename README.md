# Netlify Tests

Testing Netlify CD for a simple static site.

## Project Setup

* Create a repository
* Use netlify CLI tool to deploy any folder OR
* Add the repository to Netlify for CI
* Add any build scripts and a dist directory
* To set environment variables and contexts, use a netlify.toml:

## CLI Commands

```sh
netlify
netlify deploy
netlify deploy --prod
```

### netlify.toml

``` sh
[build]
  base    = ""
  publish = "/build"
  command = "npm run build"

[context.production]
  command = "yarn run build"
[context.production.environment]
  ACCESS_TOKEN = "super secret"

[context.staging]
command = "echo $ACCESS_TOKEN; yarn run build;"
[context.staging.environment]
  ACCESS_TOKEN = "NKqwV6ztp7ms5yHc3HJ@"

[context.deploy-preview.environment]
  ACCESS_TOKEN = "not so secret"

[context.branch-deploy]
  command = "make staging"

[context.feature]
  command = "make feature"

[context."features/branch"]
  command = "gulp"
```

### Environment Variables