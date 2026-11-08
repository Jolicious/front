# front — OIDC shim for Front help center login testing

Minimal OIDC endpoints used to configure and verify "Login controlled" access on a Front knowledge base.

Layout:

- `authorize/index.html` — static authorize endpoint served by GitHub Pages. Reads `redirect_uri` and `state`, redirects back to the knowledge base callback with a code.

Token and userinfo endpoints are provided by httpbin so the flow can be exercised without running a server:

- token: `https://httpbin.org/response-headers?access_token=tok-test&token_type=Bearer&id_token=<jwt>`
- userinfo: `https://httpbin.org/response-headers?sub=bac&email=bac%40unkn3wndb.site&name=bac+test1`

Front KB configuration used for testing:

- redirect URI registered on the IdP side: `https://bugbountyorg1.frontkb.com/auth/callback`
- scope: `openid email`
