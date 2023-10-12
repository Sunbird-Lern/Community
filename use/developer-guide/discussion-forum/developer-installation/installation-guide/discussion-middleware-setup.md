# Discussion Middleware Setup

Discussion middleware is middleware proxy service, which is having all discussion forum apis.

### How to setup discussion middleware.

**Step:1**

Clone the discussion middleware repo from [https://github.com/Sunbird-Ed/discussions-middleware.git](https://github.com/Sunbird-Ed/discussions-middleware.git)

**Step:2**

Execute `npm install` command.

**Step:3**

add the environment variable in environmentHelper.js file.

```
let localEnvVariables = {
    NODEBB_SERVICE_URL: env.nodebb_service_url || 'http://localhost:4567', 
    Authorization:  env.authorization_token || 'd8402b15-1d5f-4d84-9fae-595ef805f287', // Your local nodebb Master token
    nodebb_api_slug: env.nodebb_api_slug || '/api'
}
```

**Note**: If your testing the DF-lib using demo application. You have to use user token instead of master token. Once we implemented DF-middleware cache then onwards no need to change the token. we can use master token itself.

**Step:4**

Run the discussion middleware using the command `npm run start`. Discussion-middleware will run on port **3002.**
