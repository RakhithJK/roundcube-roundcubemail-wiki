_(since version 1.5-beta)_

Connecting Roundcube via OAuth2 is now possible and requires a few configuration options which are to be explained on this page.

## Prerequisites

1. Registered Client App (Roundcube) with your OAuth2 provider service
2. XOAUTH support for both IMAP and SMTP servers Roundcube connects to

First of all, your Roundcube installation needs to be registered as a client application with your OAuth2 provider. This will give you the necessary credentials (client-id and secret) to fill in the Roundcube config. It's also necessary to register the redirect URL to Roundcube at the provider. Use `https://<your-roundcube-url>/index.php/login/oauth` for this. The token endpoint must support the [client_secret_post](https://datatracker.ietf.org/doc/html/rfc7591#section-2) authentication method.


## Roundcube Config

All available config options are listed in the "OAuth" section of the `config/defaults.inc.php` file inside your Roundcube installation along with examples for Gmail and Outlook.com. Copy them to your `config.inc.php` file and adapt them according to your setup. Please do not exit the `defaults.inc.php` as this will be replaced on your next update.

There are the mandatory config options required to enable OAuth in Roundcube:

* `oauth_provider`: Enable OAuth2 by defining a provider. Use 'gmail', 'outlook' or 'generic'.
* `oauth_provider_name`: Provider name to be displayed on the login button
* `oauth_client_id`: OAuth client ID for your Roundcube installation
* `oauth_client_secret`: OAuth client secret
* `oauth_auth_uri`: URI for OAuth user authentication (redirect)
* `oauth_token_uri`: Endpoint for OAuth authentication requests (server-to-server)
* `oauth_identity_uri`: Endpoint to query user identity if not provided in auth response
* `oauth_scope`: OAuth scopes to request (space-separated string)

For Roundcube it's mandatory to receive the email address (or username) of the connected user. This is being used to identify returning users and also to authenticated at the IMAP and SMTP servers. Most OAuth providers will return a so called [ID Token](https://www.oauth.com/oauth2-servers/openid-connect/id-tokens/) along with the access token. That ID token contains information about the connected user. This can be enforced by requesting a specific scope, in most cases `openid`. If no such ID token is returned in the first place, Roundcube will connect to the configured `oauth_identity_uri` in order to query the connected user's identity. Use the `oauth_identity_fields` option to tell Roundcube which field of the identity information holds can canonical username.

Some OAuth servers (like Outlook) needs a `nonce` parameter for security. This parameter can be passed using the `oauth_auth_parameters` config option. For instance: `$config['oauth_auth_parameters'] = ['nonce' => mt_rand()];`

### Setting IMAP and SMTP hosts

With OAuth2 enabled, it's important to set fixed values for email server connections servers.
Enter hostnames with prefix `ssl://` to use implicit TLS, or use prefix `tls://` to use STARTTLS.

* `default_host`: IMAP hostname
* `smtp_server`: SMTP hostname (or %h to inherit from `default_host`)

### Disabling the Roundcube Login Form

By default, Roundcube will still show the classic login form with username/password fields with an additional button "Login via XXX". If OAuth shall be the only option to login at Roundcube, simply set `oauth_login_redirect` = true. This will immediately redirect to the `oauth_auth_uri` instead of displaying Roundcube's login screen.

## Troubleshooting

Coming soon.