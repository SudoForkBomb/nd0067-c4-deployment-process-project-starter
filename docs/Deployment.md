# Deployment

# AWS CLI and EB CLI

You will need to have AWS CLI and EB CLI installed to handle deployment. For installation and setup instructions, follow the instructions below.

- [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)
- [EB CLI](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3.html)

## Building and deploying

Both the frontend and backend apps can be built with the `npm run build` within their respective folders. This will generate a `www` folder, also within their respective folders. Each app has it's own `deploy.sh` script located in their `bin` folders. To make changes to how or where they are deployed, these scripts can be modified accordingly.

**If you attempt to deploy without building first, you will be unable to deploy the apps.**

## Elastic Beanstalk config

The `.elasticbeanstalk` folder handles the deployment config for the backend app. You can make changes to which environment it uses by using the `eb use` command.

Another key part of the config to what is deployed is the section below. If you change where your app is built, you will need to change it here as well.

```
deploy:
  artifact: www/Archive.zip
```

\
&nbsp;

# CircleCI

We are using CircleCI for our build pipeline. After you have made changes to the main branch and pushed your changes, it will automatically build the frontend and backend apps and run the deploy scripts, which will push the new builds to their corresponding AWS instances.

## Environment Variables

In order for your deploy scripts to work within CircleCI, you will need to set the following environment variables

```
AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
AWS_DEFAULT_REGION
```

## CircleCI config

The config files for CircleCI are located in the root folder, in the `.circleci/config` file. The config file currently installs Node, AWS CLI, and EB CLI on CircleCI, then runs commands within scripts within the root `package.json` to install dependencies, build apps, and deploy them.

## Orbs

The following Orbs are installed to get the apps to build and deploy properly.

1. [Node](https://circleci.com/developer/orbs/orb/circleci/node)
1. [AWS CLI](https://circleci.com/developer/orbs/orb/circleci/aws-cli)
1. [EB CLI](https://circleci.com/developer/orbs/orb/circleci/aws-elastic-beanstalk)

## Source Folder Scripts

### npm install

Installs required dependencies.

### npm run frontend:install

Installs dependencies for `udagram-frontend`

### npm run backend:install

Installs dependencies for `udagram-api`

### npm run frontend:build

Builds `udagram-frontend`

### npm run backend:build

Builds `udagram-api`

### npm run frontend:deploy

Deploys `udagram-frontend` to S3

### npm run backend:deploy

Deploys `udagram-api` to Elastic Beanstalk

### npm run frontend:test

Runs `udagram-frontend` tests
