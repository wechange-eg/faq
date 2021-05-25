# OAuth2

WECHANGE acts as an OAuth2 Authorization Server. This document contains some information on how to connect WECHANGE with other software.

## Preparation

To connect an application with you WECHANGE installation you have to register it. Go to https://YOUR_WECHANGE_DOMAIN/admin/oauth2_provider/application/. Click the green button to add a new application. Note down the values of `Client id` and `Client secret` as you will need it later.

Set the values:

- *Redirect url*s: https://YOUR_WIKI_DOMAIN/wiki/Special:OAuth2Client/callback
- *Client type*: Confidential
- *Authorization grant type*: Authorization code
- *Skip authorization*: checked

Choose a *Name* so that you can find the entry later easily. After clicking the blue button the application appears in the list of applications.

## MediaWiki

To connect [MediaWiki](https://www.mediawiki.org) with WECHANGE you can use the [OAuth2 Client extension](https://www.mediawiki.org/wiki/Extension:OAuth2_Client). This is an example for the  configuration in `LocalSettings.php`:

```php
$wgPluggableAuth_EnableAutoLogin = true;
$wgPluggableAuth_EnableLocalLogin = false;

wfLoadExtension( 'MW-OAuth2Client' );
$wgOAuth2Client['client']['id']     = 'YOUR CLIENT ID';
$wgOAuth2Client['client']['secret'] =  'YOUR CLIENT SECRET';

$wgOAuth2Client['configuration']['authorize_endpoint']='https://YOUR_WECHANGE_DOMAIN/o/authorize/';
$wgOAuth2Client['configuration']['access_token_endpoint']='https://YOUR_WECHANGE_DOMAIN/o/token/';
$wgOAuth2Client['configuration']['api_endpoint']='https://YOUR_WECHANGE_DOMAIN/o/me/';
$wgOAuth2Client['configuration']['redirect_uri']="https://YOUR_WIKI_DOMAIN/wiki/Special:OAuth2Client/callback";
$wgOAuth2Client['configuration']['email'] = 'email';
$wgOAuth2Client['configuration']['scopes'] = 'read';
$wgOAuth2Client['configuration']['username'] = 'name';

```

## Discourse

[Discourse](https://discourse.org) is an open source web forum and mailing list management software. You can use the [discourse-oauth2-basic plugin](https://github.com/discourse/discourse-oauth2-basic) to connect it to WECHANGE. After you have installed the plugin, go to its configuration page https://YOUR_DISCOURSE_DOMAIN/admin/site_settings/category/all_results?filter=plugin%3Adiscourse-oauth2-basic and set the following values:

- oauth2 enabled: check
- oauth2 client id: YOUR CLIENT ID
- oauth2 client secret: YOUR CLIENT SECRET
- oauth2 authorize url: https://YOUR_WECHANGE_DOMAIN/o/authorize/
- oauth2 token url: https://YOUR_WECHANGE_DOMAIN/o/token/
- oauth2 fetch user details: check
- oauth2 json user id path: ldap_uid
- oauth2 json name path: name
- oauth2 json email path: email
- oauth2 json avatar path: avatar
- oauth2 overrides email: check
- oauth2 button title: with WECHANGE

