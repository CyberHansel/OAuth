# OAuth

Oroxy traffic and check the corresponding HTTP messages when use OAuth option. First request will always be a request to the /authorization endpoint containing parameters specifically for OAuth.   
Keep an eye out for the client_id, redirect_uri, and response_type parameters. For example, an authorization request will usually look something like this:

GET /authorization?client_id=12345&redirect_uri=https://client-app.com/callback&response_type=token&scope=openid%20profile&state=ae13d489bd00e3c24  
HTTP/1.1  
Host: oauth-authorization-server.com  

