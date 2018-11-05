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
netlify # Show all commands
login   # Login to your Netlify account
status  # Print status information
sites   # Handle various site operations
init    # Configure continuous deployment for a new or existing site
link    # Link a local repo or project folder to an existing site on Netlify
unlink  # Unlink a local folder from a Netlify site
open    # Open settings for the site linked to the current folder
deploy  # Create a new deploy from the contents of a folder
watch   # Watch for site deploy to finish
```

### netlify.toml

``` sh
[build]
  base    = ""
  publish = "/build"
  command = "npm run build"

[context.master]
  command = "echo $ACCESS_TOKEN; npm run build;"
[context.master.environment]
  ACCESS_TOKEN = "I'M IN PRODUCTION"

[context.deploy-preview.environment]
  command = "echo $ACCESS_TOKEN; npm run build;"
  ACCESS_TOKEN = "I'M A PULL REQUEST TO MASTER"

[context.staging]
  command = "echo $ACCESS_TOKEN; npm run build;"
[context.staging.environment]
  ACCESS_TOKEN = "I'M THE STAGING BRANCH"

[context.branch-deploy]
  command = "echo $ACCESS_TOKEN; npm run build;"
  ACCESS_TOKEN = "I'M A BRANCH BUILD TRIGGERED BY A DEPLOY HOOK"


### Environment Variables
