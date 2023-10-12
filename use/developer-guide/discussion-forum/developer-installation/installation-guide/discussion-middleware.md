# Discussion Middleware

In Discussion forum middleware we have add the below configuration in `environmentHelper.js` file.

```
let localEnvVariables = {
    NODEBB_SERVICE_URL: env.nodebb_service_url || 'http://localhost:4567', 
    Authorization:  env.authorization_token || 'd8402b15-1d5f-4d84-9fae-595ef805f287', // Your local nodebb Master token
    nodebb_api_slug: env.nodebb_api_slug || '/api'
}
```

**NODEBB\_**_**SERVICE\_**_**URL** : This is your nodebb url by default local nodebb will run on port **4567.** and the url is[ ](http://localhost:4567)[http://localhost:4567](http://localhost:4567).

**Authorization:** This in nodebb authorization token (Write-api master token) and we have to send this token for all node apis.

**nodebb\_api\_slug:** All nodebb api should be prepend with `/api`
