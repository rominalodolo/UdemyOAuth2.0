# The Nuts and Bolts of OAuth 2.0
> by Aaron Parecki
[Get the course](https://www.udemy.com/course/oauth-2-simplified/)



# Section 1:
- History of OAuth:



- How Oauth improves application security 


- OAuth vs OpenId Connect 

OAuth is Accessing APIs vs OpenId which is Identifying Users.
OAuth is used for authorization, OpenID is used for authentication.

![oauth2](https://user-images.githubusercontent.com/83961643/177513410-1362b4c5-bea6-4cf9-b296-6e1718ccd298.jpg)

![OAuth And OpenID Connect Core Concepts6](https://user-images.githubusercontent.com/83961643/177513621-0a2b0c99-091e-436a-b20c-60d65bb1d323.png)

![OAuth And OpenID Connect Core Concepts5](https://user-images.githubusercontent.com/83961643/177513691-b96a738a-2003-4a20-85f2-faf2d3def289.jpg)


Quiz 1

1. Is there ever a reason to enter your Google password in a third party app?
No, Google requires that all third-party and even first-party apps use OAuth and never accept passwords directly. This gives them the most security and most flexibility for adding new multifactor auth methods in the future as well.

2. a risk to the user of entering their password directly into an application?
The application can potentially access and modify all data in their account. 
When you give your password to an application, you have no way of knowing what it will do with the password, even if it claims it will only access a limited amount of information

3. True or false: OAuth was created to be a single-sign-on protocol 
FALSE - OAuth was created as a delegated authorization protocol. It has been extended to be used as a single-sign-on protocol through things like OpenID Connect, but that was not its original goal.

4. True or false: OAuth provides the application with the identity of the user signing in
FALSE - In order to learn the user’s identity, applications need to use OpenID Connect or a custom API of the OAuth service.

5. 


# Section 2: 

Quiz 2 
