# shire-review-app-envs
Heroku Buildpack to set dynamic env vars like domain for review apps

## The Problem
Heroku dynamically creates the domain for the review app, as a result we can't inherit them from parent app.
Heroku review app scripts are only run after the buildpacks. Env vars are loaded in when node starts up.
We need the url set set for when we start node.

## The Discovery
Looked into documentation and examples for buildpacks and got an understanding of how env vars are set.
Found that they are read from a tmp dir where each env var has it's own file. (eg `$HOSTNAME` would be in a file called `HOSTNAME`)

## The Solution
Write our own env var files before they are read in.
