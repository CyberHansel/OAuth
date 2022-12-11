# OAuth

Oroxy traffic and check the corresponding HTTP messages when use OAuth option. First request will always be a request to the /authorization endpoint containing parameters specifically for OAuth.   
Keep an eye out for the client_id, redirect_uri, and response_type parameters. For example, an authorization request will usually look something like this:

> GET /authorization?client_id=12345&redirect_uri=https://client-app.com/callback&response_type=token&scope=openid%20profile&state=ae13d489bd00e3c24  
HTTP/1.1  
Host: oauth-authorization-server.com    

To solve this problem, the client application will often submit this data to the server in a POST request and then assign the user a session cookie, effectively logging them in. This request is roughly equivalent to the form submission request that might be sent as part of a classic, password-based login. However, in this scenario, the server does not have any secrets or passwords to compare with the submitted data, which means that it is implicitly trusted.

In the implicit flow, this POST request is exposed to attackers via their browser. As a result, this behavior can lead to a serious vulnerability if the client application doesn't properly check that the access token matches the other data in the request. In this case, an attacker can simply change the parameters sent to the server to impersonate any user.


OAuth flow:  
1.) starts with authorization request "GET /auth?client_id=...."  
2.) Notice (the blog website) receives some basic information about the user from the OAuth service.  
3.) It then logs the user in by sending a POST request containing this information to its own (website) /authenticate endpoint, along with the access token.  
4.)
