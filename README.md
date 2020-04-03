# heroku-buildpack-webhook-circleci-deploy

This is a Heroku Buildpack you can add to your heroku deployments that will notify a CircleCI of your deployment and invoke a build with the parameter `run_acceptance_tests`.

## Configuring CircleCI

1. Add `package` and `run_acceptance_tests` to your [CircleCI parameters](https://circleci.com/docs/2.0/configuration-reference/#parameters-requires-version-21)
2. Configure a workflow/job to [depend on those parameters](https://circleci.com/docs/2.0/configuration-reference/#using-when-in-workflows)

## Adding to Heroku

1. Find your [_CircleCI project slug_](https://circleci.com/blog/introducing-circleci-api-v2/) in CircleCI
2. Add your _CircleCI project slug_ as an environment variable called `CIRCLECI_PROJECT_SLUG`
3. Find your [_CircleCI token_](https://circleci.com/docs/2.0/managing-api-tokens/) in CircleCI
4. Add your _CircleCI token_ as an environment variable called `CIRCLECI_TOKEN`
5. Enable Dyno Metadata for yoru application `heroku labs:enable runtime-dyno-metadata`
6. Add this buildpack to your Heroku application: `heroku buildpacks:set https://github.com/CareerJSM/heroku-buildpack-webhook-circleci-deploy.git` (or add it via the Heroku dashboard if you have multiple buildpacks)
