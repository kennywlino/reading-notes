# Authentication

## Why this topic matters

Authentication is important as we consider working with more sensitive data. Being able to keep our databases secure as well guaranteeing our users' security via authentication will help us make strong web applications.

## OAuth

Based on this [article](https://www.csoonline.com/article/3216404/what-is-oauth-how-the-open-authorization-framework-works.html).

1. What is OAuth?

    OAuth is an open-standard authorization protocol/framework that allows separate systems to authenticate requests without having to share login credentials between the systems.

2. Give an example of what using OAuth would look like.

    A good example of OAuth is when we sign-up for a new website such as Spotify and there's a button like 'Connect with Apple' or 'Sign in with Google'. Clicking the button would authenticate us and log us into the website.

3. How does OAuth work? What are the steps that it takes to authenticate the user?

    OAuth works via HTTPS and uses the second website to verify a user.

    After connecting to the second website via OAuth, the second site will create a one-time token and secret that's unique to the session, which is then passed back to the user's client by the first site.

    The client will the give the request token and secret to the authorization provider, at which point authentication may occur if not already taken place. The user/software approves the authorization transaction, and then given an approved access token. This approved access token is given to the first website, and the first website gives it to the second for authentication proof.

    From there, the second website grants the first website access.

4. What is OpenID?

    OpenID is another security technology used now as an authentication layer for OAuth, since OAuth is primarily for *authorization*.

## Authorization and Authentication Flows

Based on this article from the [auth0 docs](https://auth0.com/docs/get-started/authentication-and-authorization-flow).

1. What is the difference between authorization and authentication?

    Authorization is when we verify *what* users have access to, while authentication is when we verify *who* a user is.

2. What is Authorization Code Flow?

    Authorization Code Flow is where we exchange an authorization code for a token. The application will also store a Client Secret in order to validate our client.

3. What is Authorization Code Flow with Proof Key for Code Exchange (PKCE)?

    This is a variation of the Authorization Code Flow for native and single-page apps that cannot store the Client Secret securely.

    The way that it works is that a Code Verifier is created by the calling application and is checked by the authorization server. The Code Verifier is also transformed into another value called the Code Challenge which is used to get an Authorization Code.
    In order to exchange the Authorization Code for a token, both the Authorization Code and the Code Verifier are used to validate.

4. What is Implicit Flow with Form Post?

    Implicit Flow with Form Post is a way to set up a sign-in feature for traditional web applications that can get tokens without having to handle secrets in our applications.

5. What is Client Credentials Flow?

    The Client Credentials Flow is a way for machine-to-machine applications to authenticate/authorize an app instead of a user. This functions in place of using a standard username/password login.

6. What is Device Authorization Flow?

    The Device Authorization Flow is a way for devices that are limited in their inputs to get authorization via a link, where they pass their Client ID to start authorization and get a token.

7. What is Resource Owner Password Flow?

    The Resource Owner Password Flow is when users give a username and password in exchange for an access token.
