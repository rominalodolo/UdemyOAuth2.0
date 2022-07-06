# The Nuts and Bolts of OAuth 2.0
> _by Aaron Parecki_
> 
> [Get the course](https://www.udemy.com/course/oauth-2-simplified/)



## Section 1:
- History of OAuth:

"OAuth started around November 2006, while Blaine Cook was working on the Twitter OpenID implementation. He got in touch with Chris Messina looking for a way to use OpenID together with the Twitter API to delegate authentication. They met with David Recordon, Larry Halff, and others at a CitizenSpace OpenID meeting to discuss existing solutions. Larry was looking into integrating OpenID for Ma.gnolia Dashboard Widgets. After reviewing existing OpenID functionality, as well as other industry practices, they came to the conclusion that there was no open standard for API access delegation. The conversation continued online and off for a few months.

In April 2007, a Google group was created with a small group of implementers to write a proposal for an open protocol. It turned out that this problem wasn’t unique to OpenID and when DeWitt Clinton from Google caught wind of the project, he expressed his interest in supporting the effort, if only as a stakeholder. In July 2007 the team drafted an initial specification and the group was opened to anyone interested in contributing. On October 3rd, 2007 the OAuth Core 1.0 final draft was released."
[Reference](https://oauth.net/about/introduction/)

- How Oauth improves application security 

"Many luxury cars today come with a valet key. It is a special key you give the parking attendant and unlike your regular key, will not allow the car to drive more than a mile or two. Some valet keys will not open the trunk, while others will block access to your onboard cell phone address book. Regardless of what restrictions the valet key imposes, the idea is very clever. You give someone limited access to your car with a special key, while using your regular key to unlock everything.

Every day new websites launch offering services which tie together functionality from other sites. A photo lab printing your online photos, a social network using your address book to look for friends, and APIs to build your own desktop application version of a popular site. These are all great services – what is not so great about some of the implementations is their request for your username and password to the other site. When you agree to share your secret credentials, not only do you expose your password to someone else (yes, that same password you also use for online banking), you also give them full access to do as they wish. They can do anything they wanted – even change your password and lock you out.

This is the problem OAuth solves. It allows you, the User, to grant access to your private resources on one site (which is called the Service Provider), to another site (called Consumer, not to be confused with you, the User). While OpenID is all about using a single identity to sign into many sites, OAuth is about giving access to your stuff without sharing your identity at all (or its secret parts)."
[Reference](https://oauth.net/about/introduction/)

- OAuth vs OpenId Connect 

OAuth is Accessing APIs vs OpenId which is Identifying Users.
OAuth is used for authorization, OpenID is used for authentication.

![oauth2](https://user-images.githubusercontent.com/83961643/177513410-1362b4c5-bea6-4cf9-b296-6e1718ccd298.jpg)

![OAuth And OpenID Connect Core Concepts6](https://user-images.githubusercontent.com/83961643/177513621-0a2b0c99-091e-436a-b20c-60d65bb1d323.png)

![OAuth And OpenID Connect Core Concepts5](https://user-images.githubusercontent.com/83961643/177513691-b96a738a-2003-4a20-85f2-faf2d3def289.jpg)


### Quiz 1

1. Is there ever a reason to enter your Google password in a third party app?
No, Google requires that all third-party and even first-party apps use OAuth and never accept passwords directly. This gives them the most security and most flexibility for adding new multifactor auth methods in the future as well.

2. a risk to the user of entering their password directly into an application?
The application can potentially access and modify all data in their account. 
When you give your password to an application, you have no way of knowing what it will do with the password, even if it claims it will only access a limited amount of information

3. True or false: OAuth was created to be a single-sign-on protocol 
FALSE - OAuth was created as a delegated authorization protocol. It has been extended to be used as a single-sign-on protocol through things like OpenID Connect, but that was not its original goal.

4. True or false: OAuth provides the application with the identity of the user signing in
FALSE - In order to learn the user’s identity, applications need to use OpenID Connect or a custom API of the OAuth service.

5. True or false: OpenID Connect provides the application with the identity of the user signing in
TRUE - OAuth only provides the application with an access token. OpenID Connect was created as an extension of OAuth in order to provide the application with the user’s identity information.

6. True or false: OAuth provides a way for an application to get an access token to make API requests
TRUE - This is the exact thing OAuth was created to solve. This is also called delegated authorization.

7. True or False: Applications need to be able to parse access tokens to be able to use them 
FALSE - Just like a hotel key, the application using the access token doesn’t need to know anything about how it works. Applications should just use the access token in an API request and let the API figure out if it’s valid.


## Section 2: API Security Concepts 

- Roles in OAuth 
1. The User - the resource owner 
2. The Device - user agent
3. The Application - oauth client 
4. The API - where the data lives - resource server 

Authorization server - creates an access token which then is given to the app to get the password. The app makes an api request but never sees the password. 

API Gateway is always in the resource server 

- Application Types
Confidential & Public Clients 

The difference between the two is the deployment credentials.

Confidential applications can hold credentials in a secure way without exposing them to unauthorized parties. They require a trusted backend server to store the secret(s).

Credentials cannot be securely stored in public applications.

[Reference](https://medium.com/identity-beyond-borders/oauth-application-types-729764af73d5)

- User Consent 

Concent screen being critical to the flow 

Password grant - app sends password prompt to user, user gives permisions and provides password then server provides an access token 


<img width="888" alt="2022-01-31_23-33-45" src="https://user-images.githubusercontent.com/83961643/177543848-87414fd2-5f80-4c27-a7a1-963d5971ed9c.png">

![consent-dialog](https://user-images.githubusercontent.com/83961643/177544354-37eaa836-b8c9-4531-8bd3-a4b8db41a1bc.png)


- Front Channel vs Back Channel 
> describes the 2 different ways how data moves around between systems:
> 
> back channel:  normal/ secure, HTTPS client to serever connection (certification, encription, trusted)
> 
> Backend request with java is done with ajax or fetch 
> 
> front channel: using address bar to transfer data (uncertainty)
> ![flow-channels-5d8996b3706cab1e4ac8f9ed716d6529d3970f91cbc3cb5ff5a21a94389d0e1d](https://user-images.githubusercontent.com/83961643/177546795-64333987-3b8a-474c-8ca5-76b0ccd5082a.png)
> [reference](https://developer.okta.com/blog/2017/06/21/what-the-heck-is-oauth)



- Application Identity 

Authorization code flow 

PKCE (pronounced "pixy") is a security extension to OAuth 2.0 for public clients on mobile devices, designed to prevent interception of the authorisation code by a malicious application that has sneaked into the same device. [reference](https://connect2id.com/products/nimbus-oauth-openid-connect-sdk/examples/oauth/pkce)

Redirect URI 


### Quiz 2 

1. When a user is using Travis CI to test code from GitHub, GitHub is playing which of the OAuth roles?
Authorization Server and Resource Server - Even though GitHub is one piece of software, it is playing two roles in the OAuth flow

2. When a user is using Travis CI to test code from GitHub, Travis CI is playing which of the OAuth roles?
Client - A "client" in OAuth is the one that's trying to access resources using an access token

3. If you are building an iPhone app, using an external service as your Authorization Server, which roles are you building?
Client 

4. If you are building an API, using an external service as your Authorization Server, which roles are you building?
Resource Server

5. If you are building an application with a .NET backend, which type of application are you building?
Confidential 

6. If you are building a mobile app, which type of application are you building?
Public

7. Which of the below is considered a “public client”?
An iPhone app used only by employees - Mobile apps don’t have the ability to be deployed with credentials, so they are considered public clients. The users of the app are not significant to this distinction.

8. Which of the below is considered a “confidential client”?
A server-side Java app for publising blog posts - Even though the app will be used to create public content, the application is considered a "confidential client" since it can be deployed with credentials 

9. Which is the better description of the term “back channel”?
A request from an HTTP client to an HTTP server - Any HTTP client that makes a request to an HTTP server is using the back channel, even if that client is JavaScript code in a browser

10. Which is the better description of the term “front channel”?
Sending data by making the browser redirect - Using the browser’s address bar to move data between two other pieces of software is using the front channel.



## Section 3: OAuth Clients


## Section 4: OAuth for Server-side applications


## Section 5: OAuth for native applications

## Section 6: OAuth for singlepage applications


## Section 7: OAuth for the Internet of things 



## Section 16: Conclusion 

OAuth 2.1 (More modern version)
- Authorization Code + PKCE 
- Client Credentials 
- Tokens in HTTP Header 
- Tokens in POST Form Body  

New developments coming up. 

Additional Recources: [EBook](https://oauth2simplified.com) 
[Playground](https://www.oauth.com/playground/)



## Last Edit July 2022
