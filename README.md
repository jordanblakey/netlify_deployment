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
  base    = "site"
  publish = "public"
  command = "make"

[context.production]
  command = "make production"
  [context.production.environment]
    ACCESS_TOKEN = "super secret"

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