# Local Installation and Setup

To run the application locally, follow the instructions below. You can introduce and replace each part below with an AWS Cloud component by following the AWSSetup.md instructions.

# Database

You will need to setup a local Postgres database for your project to connect to. You can follow instructions like the one below.
https://www.postgresql.org/docs/9.0/tutorial-createdb.html

# Backend

The project will not work without environment variables set. You will need to create a .env file in the udagram-api folder and include the following:

- POSTGRES_HOST=localDBName
- POSTGRES_DB=datebaseName
- POSTGRES_USERNAME=datebaseUsername
- POSTGRES_PASSWORD=datebasePassword
- AWS_REGION=us-east-1
- AWS_ACCESS_KEY_ID=AWSAccessKey
- AWS_SECRET_ACCESS_KEY=AWSSecretKey
- AWS_BUCKET=aws-bucket-name
- JWT_SECRET=example123!
- URL=http://localhost:8080

After you have setup your .env file, You can run the following commands within the udagram-api folder.

## Basic Scripts to run and deploy the backend app.

In the project directory, you can run:

### npm install

Installs required dependencies.

### npm run start

Runs the backend app at [http://localhost:8080](http://localhost:8080).

### npm run dev

Runs the backend app in development mode at [http://localhost:8080](http://localhost:8080).

### npm run build

Builds the app for production to the `www` folder.\

### npm run lint

Runs ESlint to look for any lint errors.

### npm run deploy

Runs the deploy script located at `bin/deploy.sh`.

# Frontend

The frontend looks for the backend in the `environment.ts` file. This should be set to [http://localhost:8080](http://localhost:8080) initially, and changed later to your Elastic Beanstalk url.

## Basic Scripts to run and deploy the backend app.

In the project directory, you can run:

### npm install

Installs required dependencies.

### npm run start

Runs the backend app at [http://localhost:4200](http://localhost:4200).

### npm run build

Builds the app for production to the `www` folder.\

### npm run deploy

Runs the deploy script located at `bin/deploy.sh`.
