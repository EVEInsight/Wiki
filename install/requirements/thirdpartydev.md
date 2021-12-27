---
title: Third Party Developer Requirements
description: Instructions for obtaining needed developers tokens.
published: true
date: 2020-03-02T03:56:21.617Z
tags: 
editor: markdown
dateCreated: 2020-03-02T03:55:28.874Z
---


# Discord Developer
> The Discord developer token allows you to create a new bot user that runs Insight.
{.is-info}
1. Go to [Discord Developer](https://discordapp.com/developers/applications/me) and create a **New App**.
    > No **Redirect URL** is required.
    {.is-info}
2. After creating a new app, edit your app and click **Create a Bot User**.
    > Ensure the **Public Bot** checkbox is enabled and the **Require OAuth2 Code Grant** is disabled.
    {.is-info}
3. Copy your Discord application's **Token** into the config file under the section [discord]. Your config file section should look
like this:
    ```
    [discord]
    token = YourDiscordAppTokenGoesHereWithoutQuotes
    ;required - Create a new Discord app at https://discordapp.com/developers/applications/me and set token to your App's token
    ```

# CCP Developer
> The CCP developer token allows your bot to interact with the EVE Online API to load contact information for use in ally whitelisting for [radar](/feeds/radar) and [proximity](/feeds/proximity) feeds.
{.is-info}

1. Go to [CCP Developers](https://developers.eveonline.com/applications/create) and create a new app with the following settings:
    * **Connection Type** = Authentication & API Access
    * **Requested Scopes List:**
        * esi-characters.read_contacts.v1
        * esi-corporations.read_contacts.v1
        * esi-alliances.read_contacts.v1
    * **Callback** = ```https://insight.nathan-s.com/Insight/callback``` if you don't plan on personally hosting a callback landing page.
        * Insight does not utilize a callback listener for simplicity so the user must manually copy their returned callback URL into Discord. This callback URL is simply a landing page.
    Feel free to host the contents of /callback/index.html and modify the callback to point to your own landing page. The above URL is hosted on Github and directs users to the contents of ```Insight/callback/index.html```.

2.. Create your new CCP App and copy the **Client ID**, **Secret Key**, and **Callback URL** into the appropriate sections in your **config** file.
