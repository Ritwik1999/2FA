# 2FA

2FA helps one quickly set up a backend to integrate 2 Factor Authentication into their existing workflow.

P.S Inspired from Brad Traversy's video on the same (https://www.youtube.com/watch?v=KQya9i6czhM)

## Setup 
1. Clone the repository
2. Install the npm packages
2. Rename .env.exmaple to .env
3. Create a file in the root directory of your project and name it TrialDB.json


## Usage
As this is only the backend, you'd have to use an API testing tool like Postman. You'd also need a 2FA app like Google Authenticator (or it's chrome extension).
Send a POST request to `/api/register` to register a new user. If successful, you'd get a JSON response with an ID and secret. Use this secret in the 2FA app/extension to get the intial verification code.
Using the `id` and the `code` from previous step, send a POST request to `/api/verify` with the request body structured as JSON using the template
```
{
  "userId": "id",
  "token": "code"
}
```

You are all set up! Send POST requests generated from the app/extension to `/api/validate` replacing the `token` above with the code generated.
