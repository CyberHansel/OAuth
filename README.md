# OAuth

OAuth flows remain largely the same; the main difference is how the client application uses the data that it receives.  

* Although many components of the OAuth flows are optional, some of them are strongly recommended unless there's an important reason not to use them. One such example is the state parameter. (state should be unguessable - hashed). This value is then passed back and forth as a form of CSRF token for the client application. 
* OAuth flow always starts with authorization request "GET /auth?client_id=...." Keep an eye out for the client_id, redirect_uri, and response_type parameters.  


## Implicit login
Vulnerability: server does not have any secrets or passwords to compare with the submitted data, so POST request is implicitly trusted. Attacker simply can change data with BURP, before sending.

OAuth flow:  
1.) always starts with authorization request "GET /auth?client_id=...." Keep an eye out for the client_id, redirect_uri, and response_type parameters.  
2.) Notice (the blog website) receives some basic information about the user from the OAuth service.  
3.) It then logs the user in by sending a POST request containing this information to its own (website) /authenticate endpoint, along with the access token and data that was received from auth.  
4.) Change that POST data to carlos and solve lab.  

## CSRF attack if there is no state parameter 
Exploit server  

## /.well-known/openid-configuration  is left open  
 requestbin.net  - substitude for collaborator
 




