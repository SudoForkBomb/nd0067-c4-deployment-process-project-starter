# Hosting a Full-Stack Application

# Udagram

[![<SudoForkBomb>](https://circleci.com/gh/SudoForkBomb/nd0067-c4-deployment-process-project-starter.svg?style=svg)](https://circleci.com/gh/SudoForkBomb/nd0067-c4-deployment-process-project-starter)

http://udagram-frontend-taylor.s3-website-us-east-1.amazonaws.com/

The Udagram application is a fairly simple application that includes all the major components of a Full-Stack web application.
It was provided to me as a way to host a Full-Stack application for my Udacity project.

## Getting Started

1. Clone this repo locally into the location of your choice.
1. Open a terminal and navigate to the root of the repo.
1. Install dependencies and build the applications
1. Follow the setup guides for in-depth instructions to running and building the apps.
   1. [LocalSetup.md](./docs/LocalSetup.md)
   1. [AWSSetup.md](./docs/AWSSetup.md)
   1. [Deployment.md](./docs/Deployment.md)

&nbsp;

## Dependencies

```
The below dependencies are what was tested and proven to work with the current iteration of the app. Other options may work, but are not guaranteed without making substantial changes.


- Node v14.18.1 (LTS) or more recent. While older versions can work it is advisable to keep node to latest LTS version.

- npm 6.14.15 (LTS) or more recent. Yarn was tested for this project, but ran into issues with installing newer versions of dependencies, so it is recommended to just use npm.

- AWS CLI v2, v1 can work but was not tested for this project

- A RDS database running Postgres.

- A S3 bucket for hosting uploaded pictures.

- An Elastic Beanstalk instance
```

&nbsp;

## Basic Installation Information

It is recommended to get the project working locally first, then replace each part with its AWS component. Preferably in the order of:

1. Database
1. Backend
1. Frontend

The project will not work without environment variables set. You will need to include the following:

- POSTGRES_HOST=example.amazonaws.com
- POSTGRES_DB=datebaseName
- POSTGRES_USERNAME=datebaseUsername
- POSTGRES_PASSWORD=datebasePassword
- AWS_REGION=us-east-1
- AWS_ACCESS_KEY_ID=AccessKey
- AWS_SECRET_ACCESS_KEY=SecretKey
- AWS_BUCKET=aws-bucket-name
- JWT_SECRET=example123!
- URL=http://localhost:8080

Follow the in-depth setup instructions located in the [docs](./docs) folder
&nbsp;

### AWS Account

Make sure you have an AWS account setup, with a user you are planning to use having access to the required AWS instances needed for the project.

## Testing

This project contains two different test suite: unit tests and End-To-End tests(e2e). Follow these steps to run the tests.

1. `cd starter/udagram-frontend`
1. `npm run test`
1. `npm run e2e`

There are no Unit test on the back-end

### Unit Tests:

Unit tests are using the Jasmine Framework.

### End to End Tests:

The e2e tests are using Protractor and Jasmine.

## Built With

- [Angular](https://angular.io/) - Single Page Application Framework
- [Node](https://nodejs.org) - Javascript Runtime
- [Express](https://expressjs.com/) - Javascript API Framework

## License

[License](LICENSE.txt)
