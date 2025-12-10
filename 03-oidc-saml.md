---
tags:
  - pecha-kucha
  - oidc
---
# OIDC and SAML
![[media/oidclogo.png]]
![[samllogo.png]]
notes: let's talk about SSO!

---

<grid drag="45" drop="left" flow="col">
**Authentication**  
*Who are you?*

- username
- email address
- group membership
</grid>
<grid drag="45" drop="right" flow="col">
**Authorization**  
*What can you do?*
- Perforce protects table
- IAM Role
- ACL lists
</grid>

notes: First a note on terminology. Authentication is who you are, authorization is what you're allowed to do. Separating these concerns allows you to set authorization rules that aren't tied to individual people ("Anyone in the 'Devops' groups can administer Jenkins") and allows you to split the whole concept of identity versus permission.

---

OIDC = Authentication

OAuth = Authorization

SAML = a protocol to do both

notes: In our talk today, OIDC provides authentication, OAuth is a means to authorize users based on external identity, and SAML is a whole 'nother beast: just an XML-based protocol that can be used to do either. In other words...

---
OIDC = Who is your daddy?

OAuth = ...and what does he do?

---
## OIDC

Authentication method using JSON Web Tokens (JWT, pronounced "jot")

notes: OIDC uses JWTs to establish identity between providers and consumers. IdP administrators (like Pipeworks IT) will pre-configure applications to allow access to different scopes of information, e.g. "Just username" or "Username and group information," etc.

---
## JWT

- Open standard [RFC7519](https://datatracker.ietf.org/doc/html/rfc7519)
- Makes "claims" about user identity
- JWTs are secret, but NOT encrypted! [jwt.io]()
- Signed with a baked-in expiration
	- No revocation!

notes: JWTs are an open standard method of encoding identity information within a JSON blob. The details are out of scope of this talk, but here's some broad strokes. What you need to know: JWTs are not encrypted, but they are _signed_ so you can verify authenticity. They have "not before" and "not after" expiry baked into the token, along with information about the issuer and one or more "claims" about a user's identity, which might be "username" or might be "memberOfGroup" or any other arbitrary key.

---
## OAuth

Assigns privileges to a user based on the claims that OIDC returns

```json
{
	"profiles": [
	    {
	        "id": "qa-run",
	        "actions": ["CreateJob"],
	        "extends": ["default-read"]
	    }
	],
    "entries": [
        {
	        "claim": {
	            "type": "groups",
		        "value": "PW-Horde-GZPro-QA-RunBuilds"
	        },
		    "profiles": ["qa-run"]
		}
	]
}
```

notes: This is a snippet from GZPro Horde marking Robert's QA team as "allowed to make builds."

---
## OAuth Clients

| Public                                                                                                                                     | Confidential                                                                   |
| ------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| Acts as an untrusted client, using the end user's credentials.                                                                             | Contains a secret authorizing it to make requests of the IdP.                  |
| Uses [Proof Key for Code Exchange](https://oauth.net/2/pkce/) (PKCE, pronounced 'pixie') to hide identity info from untrusted user devices | All of our Enterprise SAML applications work this way                          |
| Used in anything that might be considered a "client" application (mobile apps, desktop applications, browser-based workflows, etc)         | Used when we have an authoritative backend server that can hold secrets safely |
note: There are two types of OAuth clients, which boil down to "Trusted" and "Untrusted"

---

## PKCE

A layer of security on top of code exchange

note: So how do we make public clients secure? We borrow the authority of the user by using Proof Key for Code Exchange.

---
## PKCE

<ol>
<li class=fragment>Generate a long string ("`verifier`")</li>
<li class=fragment>base64(sha256(verifier)) ("`challenge`")</li>
<li class=fragment>Pass that hash to the (untrusted) client to give to the IdP</li>
<li class=fragment>User logs in to their IdP, sending the challenge along with the auth request</li>
<li class=fragment>IdP returns a short-lived code with a redirect request to your app ("`code`")</li>
<li class=fragment>User browser returns that code to your app</li>
<li class=fragment>App sends `code` and `verifier` to the IdP</li>
<li class=fragment>IdP looks up the `challenge` that was associated with that `code`, asserts that `verifier` was used to construct that `challenge`</li>
<li class=fragment>IdP responds with identity information (for OIDC: in the form of a JWT)</li>
</ol>
note: PKCE has 9 steps. Buckle up.

---

Okay but why...

---

![[oidc-pkce.png]]

---

![[LassoS3Flow.jpg]]

---

Okay but why SSO at all?

> User PII is radioactive. Let's pay someone else to handle it.

> Centralized identity management provides ease of administration

---
## SAML

briefly...

- XML based <!-- element class="fragment" -->
- Old school (originated for SOAP) <!-- element class="fragment" -->
- Has a broader specification <!-- element class="fragment" -->
- Enterprise-focused <!-- element class="fragment" -->

notes: SAML is an !!slide!! XML-based protocol for exchanging authentication and authorization data. It's much more old school, originating in 2001 to be used with SOAP bindings. Its specification is broader and more extensible than OIDC which allows it to be used for both authn and authz, but by the same token it is less focused and, in practice, only widely-used in contexts where Enterprise was always the target audience.

---
## Usage at Pipeworks

SSO is used for:

- Email
- Slack
- Miro
- Atlassian (I think)
- Perforce
	- and by extension, Swarm
- Horde
- Jenkins
- Helpdesk
- ...and probably more I'm not thinking of.