# AWS Installation and Setup

This project is currently configured to use Amazon AWS Services.

Provisioning the necessary AWS services is needed for running the application.

**Please follow the [Local Setup Guide](./docs/LocalSetup.md) first to get a basic idea of the setup and environment.**
\
&nbsp;

# Environment Variables

It is extremely important that your environment variables are properly set in your `.env` file for local testing and development, and within your Elastic Beanstalk instance once it is deployed.
\
&nbsp;

Below are the required variables again:

```
POSTGRES_HOST=example.amazonaws.com
POSTGRES_DB=datebaseName
POSTGRES_USERNAME=datebaseUsername
POSTGRES_PASSWORD=datebasePassword
AWS_REGION=us-east-1
AWS_ACCESS_KEY_ID=AccessKey
AWS_SECRET_ACCESS_KEY=SecretKey
AWS_BUCKET=aws-bucket-name
JWT_SECRET=example123!
URL=http://localhost:8080
```

You will need to set up your env variables on the Elastic Beanstalk Instance
\
&nbsp;

# Database - Amazon RDS

## RDS Setup

In AWS, provision a publicly available RDS database running Postgres.\
After setup you will need to add or change your environment variables to correspond with your new database. These will be either locally or in Elastic Beanstalk, depending on where you are running your backend app.

You may need to allow make changes to your security settings and allow incoming traffic to talk to your database.

**Warning: This will make your database open to the public. I do not recommend these instructions permanently and you should shut down your database when not in use.**
\
&nbsp;

# Backend - Amazon Elastic Beanstalk

In AWS, provision an Elastic Beanstalk environment and application for a Node application. It is recommended that you choose Node 14 LTS.\
For the files for the application:

1. Build the `udagram-api` app using `npm run build`.
1. Zip the contents of the `www` folder.
1. Upload to your EB instance.

After the EB environment and app are running, you should then add the environment variables.
\
&nbsp;

# Frontend - Amazon S3 Bucket

In AWS, provision a public s3 bucket for hosting the uploaded files and your frontend application.
For the files for the application:

1. Build the `udagram-frontend` app using `npm run build`.
1. Zip the contents of the `www` folder.
1. Upload to your s3 instance.

You're welcome to add more restrictive security permissions later, but the initial recommendation to get the app working are listed below.

**Warning: This will make your application open to the public. I do not recommend these instructions permanently and you should shut down your instances when not in use.**
\
&nbsp;

### Block all public access

You will need to set _Block all public access_ to **Off**

### Bucket policy

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:GetObject",
                "s3:DeleteObject",
                "s3:GetObjectVersion",
                "s3:PutObject",
                "s3:PutObjectAcl"
            ],
            "Resource": "arn:aws:s3:::udagram-frontend-taylor/*"
        }
    ]
}
```

### Cross-origin resource sharing (CORS)

```
[
    {
        "AllowedHeaders": [
            "*"
        ],
        "AllowedMethods": [
            "GET",
            "POST",
            "PUT",
            "DELETE"
        ],
        "AllowedOrigins": [
            "*"
        ],
        "ExposeHeaders": []
    }
]
```

&nbsp;
