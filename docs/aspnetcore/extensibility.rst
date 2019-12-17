Extensibility
=============
The main extensibility points are around token storage (users) and token caching (clients).

Client access tokens
--------------------
Client access tokens are cached in memory by default.
The default cache implementation uses the ``IDistributedCache`` abstraction in ASP.NET Core.

You can either

- replace the standard distributed cache with something else
- replace the ``IClientAccessTokenCache`` implementation in DI altogether

User access tokens
------------------
User access tokens are stored/cached using the ASP.NET Core authentication session mechanism.
For that you need to set the ``SaveTokens`` flag on the OpenID Connect handler to ``true``.

ASP.NET Core stores the authentication session in a cookie by default.
You can replace that storage mechanisms by setting the ``SessionStore`` property on the cookie handler.

If you want to take over the token handling altogether, replace the ``IUserTokenStore`` implementation in DI.
