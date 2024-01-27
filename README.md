# MycoNet

## Project Description
In this project we will build a Twitter style application

## Instructions

### Create React App

In the root folder, create a React application using the TypeScript template

`npx create-react-app . --template -typescript`

Check it builds correctly

`npm run build`

### Configuring Amplify

In this project we're going to use AWS Amplify to:
- host the frontend
- utilise Cognito user pools
- Implement a REST API using API Gateway and Lamdba functions

Install dependencies

`npm i aws-amplify @aws-amplify/auth @aws-amplify/ui-react`

Initialise amplify project

`amplify init`

The Project Information we're using is:

Project information
| Name: myconetaws
| Environment: dev
| Default editor: Visual Studio Code
| App type: javascript
| Javascript framework: react
| Source Directory Path: src
| Distribution Directory Path: build
| Build Command: npm run-script build
| Start Command: npm run-script start

Choose your authentication method

#### Set up CI/CD
Head to the AWS Amplify console, select your app, link your github/other provider to your aws account, select the repo and branch to deploy from.

Select the "deploy on every code change" for automated deployments.

#### Configure Authentication

`amplify add auth`

Default configuration

Email

No advanced settings

#### Configure S3 storage for assets

`amplify add storage`

Select "Content"

Name the resource
Name the bucket
Auth and guest users should have access
Auth users can CRUD
Guests can R
Add lamba trigger for S3 bucket
Don't edit the function now

#### Configure the API

`amplify add api`

Select REST
Name API
Name the path
Create new function
Call it test
NodeJS
Serverless ExpressJS
No
No
Yes
Authenticated and Guest users
Authenticated CRUD
Guests R
No

And that's all the paths we'll add for now.

#### Push amplify changes

`amplify push`

 Category │ Resource name      │ Operation │ Provider plugin   │
├──────────┼────────────────────┼───────────┼───────────────────┤
│ Auth     │ myconetaws66b9c2bb │ Create    │ awscloudformation │
├──────────┼────────────────────┼───────────┼───────────────────┤
│ Function │ S3Trigger56797c09  │ Create    │ awscloudformation │
├──────────┼────────────────────┼───────────┼───────────────────┤
│ Function │ test               │ Create    │ awscloudformation │
├──────────┼────────────────────┼───────────┼───────────────────┤
│ Storage  │ myconetaws         │ Create    │ awscloudformation │
├──────────┼────────────────────┼───────────┼───────────────────┤
│ Api      │ myconetaws         │ Create    │ awscloudformation │

This will create the Cognito user pool, the S3 resource and bucket, a lambda function to trigger S3 connections, a test lambda function and configure the api in API gateway.

### API Dummy functions

In order for us to set up dummy functions that connect to the database, we'll first need to create the database and database proxy.

#### Creating the database

Head over to AWS RDS and create a free tier PostgreSQL database.
Ensure that it is set-up to be publicly accessible.

MASTER USER
postgres
databasePassword123

Wait for the Database to be set up and deployed

Create RDS Proxy
You will need to create a new secret in order to create the RDS Proxy logged in as the master account

Wallah, we can connect to the database.