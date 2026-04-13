# bqe-oauth-callback

Static GitHub Pages host for the BQE Core OAuth 2.0 callback page used by the
[logseq-plugin-jpi-tools](https://github.com/JoshGJPI/logseq-plugin-jpi-tools) plugin.

## How it works

When the plugin initiates a BQE Core login, it opens a popup window pointing at
BQE's OAuth authorize endpoint. After the user signs in, BQE redirects the popup to
this page with an authorization code in the URL query string.

This page reads the `code` parameter and sends it back to the plugin via
`window.opener.postMessage`, then closes itself. The plugin exchanges the code for
access tokens without the user needing to copy-paste anything.

## Hosted URL

```
https://joshgjpi.github.io/bqe-oauth-callback/oauth-callback.html
```

Register this URL as an allowed redirect URI in your BQE developer portal OAuth
application settings, and paste it into the plugin's **BQE OAuth Callback URL**
setting.

## Setup (GitHub Pages)

This repo must be **public** and GitHub Pages must be enabled:

`Settings → Pages → Deploy from branch → main → / (root) → Save`
