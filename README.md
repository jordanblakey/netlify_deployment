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

[context.master]
  command = "echo $ACCESS_TOKEN; yarn run build;"
[context.master.environment]
  ACCESS_TOKEN = "I'M IN PRODUCTION"

[context.deploy-preview.environment]
  command = "echo $ACCESS_TOKEN; yarn run build;"
  ACCESS_TOKEN = "I'M A PULL REQUEST TO MASTER"

[context.staging]
  command = "echo $ACCESS_TOKEN; yarn run build;"
[context.staging.environment]
  ACCESS_TOKEN = "I'M THE STAGING BRANCH"

[context.branch-deploy]
  command = "echo $ACCESS_TOKEN; yarn run build;"
  ACCESS_TOKEN = "I'M A BRANCH BUILD TRIGGERED BY A DEPLOY HOOK"

[context.feature]
  command = "echo $ACCESS_TOKEN $FEATURE_KEY; yarn run build;"
  FEATURE_KEY = "I'M A BUILD TRIGGERED FOR A SPECIFIC BRANCH"

[context."features/branch"]
  command = "echo $ACCESS_TOKEN; yarn run build;"
  ACCESS_TOKEN = "I'M A BUILD TRIGGERED FOR A FEATURE BRANCH"
```

### Environment Variables