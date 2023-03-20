# Week 3 — Decentralized Authentication
cd frontend-react-js
_npm i aws-amplify --save_
open src/app.jss file and paste this
```
    import { Amplify } from 'aws-amplify';
    Amplify.configure({
    "AWS_PROJECT_REGION": process.env.REACT_AWS_PROJECT_REGION,
    "aws_cognito_identity_pool_id": process.env.REACT_APP_AWS_COGNITO_IDENTITY_POOL_ID,
    "aws_cognito_region": process.env.REACT_APP_AWS_COGNITO_REGION,
    "aws_user_pools_id": process.env.REACT_APP_AWS_USER_POOLS_ID,
    "aws_user_pools_web_client_id": process.env.REACT_APP_CLIENT_ID,
    "oauth": {},
    Auth: {
        // We are not using an Identity Pool
        // identityPoolId: process.env.REACT_APP_IDENTITY_POOL_ID, // REQUIRED - Amazon Cognito Identity Pool ID
        region: process.env.REACT_AWS_PROJECT_REGION,           // REQUIRED - Amazon Cognito Region
        userPoolId: process.env.REACT_APP_AWS_USER_POOLS_ID,         // OPTIONAL - Amazon Cognito User Pool ID
        userPoolWebClientId: process.env.REACT_APP_AWS_USER_POOLS_WEB_CLIENT_ID,   // OPTIONAL - Amazon Cognito Web Client ID (26-char alphanumeric string)
    }
    });
```
set value for env variables under frontend in yml file
REACT_AWS_PROJECT_REGION,
REACT_APP_AWS_COGNITO_IDENTITY_POOL_ID,
REACT_APP_AWS_COGNITO_REGION,
REACT_APP_AWS_USER_POOLS_ID,
REACT_APP_CLIENT_ID,