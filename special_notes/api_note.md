# API E2E - Login - App using Cognito AWS

What is Cognito: https://docs.aws.amazon.com/cognito/latest/developerguide/what-is-amazon-cognito.html

Example Curl: 

```
curl --location --request POST 'https://cognito-idp.{{region}}.amazonaws.com/' \
--header 'Content-Type: application/x-amz-json-1.1' \
--header 'X-Amz-Target: AWSCognitoIdentityProviderService.InitiateAuth' \
--data-raw '{
    "AuthParameters" : {
        "USERNAME" : {{username}},
        "PASSWORD" : {{password}}
    },
    "AuthFlow" : "USER_PASSWORD_AUTH",
    "ClientId" : {{client_id}}
}
```

You can read more information here: https://doaitran-testing4everyone.blogspot.com/2022/10/how-to-automate-api-user-login-if.html

Refferences: 
- https://stackoverflow.com/questions/58833462/aws-cognito-authentication-curl-call-generate-token-without-cli-no-clien
- https://docs.aws.amazon.com/cognito-user-identity-pools/latest/APIReference/API_InitiateAuth.html


# API - E2E - Login - App using Office 365:
- Microsft provides us API Document in Graph, you can refer more here: https://learn.microsoft.com/en-us/graph/overview
- Get access as an user: https://learn.microsoft.com/en-us/graph/auth-v2-user#2-get-authorization

