---
description: >-
  A tutorial on how to setup and configure the dashboard for Plex Tickets. You
  can either watch the video or follow the instructions below:
---

# Plex Tickets/Staff Dashboard

## Video tutorial:

{% embed url="https://www.youtube.com/watch?v=iPDHqK_soD0" %}
[https://www.youtube.com/watch?v=iPDHqK\_soD0](https://www.youtube.com/watch?v=iPDHqK_soD0)
{% endembed %}

## Text:

This guide will guide you on how to setup the dashboard for both Plex Tickets and Plex Staff to put on your `config.yml` file.

We will do the following:

* For Plex Tickets: Download the dashboard addon.
* Get the Client ID, Client Secret of our bot.
* Set the Callback URL on Discord's Developer Portal.
* Configure the rest.
* Test if everything works.

### Plex Tickets Dashboard:

### Step 1: Downloading the files&#x20;

To begin, you will need to download the dashboard addon. You can download it from the [website](https://plexdevelopment.net/) or from [BuiltByBit](https://builtbybit.com/resources/plex-tickets-discord-ticket-bot.22209/). After downloading the addon, you have to unzip it to the <mark style="color:blue;">`./addons/`</mark> folder.

### Step 2: Configure the dashboard

Next, you have to open the <mark style="color:blue;">`./addons/Dashboard/config.yml`</mark> file, and configure it.

#### Filling out the config

{% hint style="warning" %}
**Important:** If you are using shared hosting without a VPS or reverse proxy, remember to include the port in all the links provided below.
{% endhint %}

This part is very important to succeed. You have to consider that you want to use any proxy and or SSL for your dashboard.&#x20;

1. **Get the Client ID and Client Secret**
   * Go to the [Discord Developer Portal](https://discord.com/developers/applications).
   * Locate your bot's <mark style="color:blue;">`clientId`</mark> and <mark style="color:blue;">`clientSecret`</mark> under the OAuth2 section. Reset the Client Secret if necessary, then copy both of them and put them into the `config.yml` file.
2. **Configure Callback URL**
   * Set the <mark style="color:blue;">`callbackURL`</mark> specified in the <mark style="color:blue;">`config.yml`</mark> file.&#x20;
   * If you use a shared hosting without a VPS or reverse proxy, use <mark style="color:blue;">`http://<ip>:<port>/auth/discord/callback`</mark>. Don't forget to replace <mark style="color:blue;">`<ip>:<port>`</mark> with your IP and port of your server.
   * If you are using a domain, format it as <mark style="color:blue;">`http://ticket.yourdomain.com/auth/discord/callback`</mark>. Don't forget to replace <mark style="color:blue;">`ticket.yourdomain.com`</mark> with your domain.
   * If you use SSL, you can use <mark style="color:blue;">`https://ticket.yourdomain.com/auth/discord/callback`</mark>. Don't forget to replace <mark style="color:blue;">`ticket.yourdomain.com`</mark> with your domain.
   * On the same oAuth2 section, add that URL to the Redirect URL section on the Developer Portal.

You should now have 6 more fields to fill out:

* <mark style="color:blue;">`Port`</mark>: This is the port where the webserver will be running. You can change this to anything, just be aware that it can't be used by any other programs on the VPS. If you are using a shared hosting, the port must be the one assigned to you.
* <mark style="color:blue;">`URL`</mark>: The URL you want to access the dashboard. For example, if you use a custom domain with SSL, you would put `https://ticket.yourdomain.com` as the URL.
* <mark style="color:blue;">`secretKey`</mark>: You can set anything to this but it has to be a string so random characters. We recommend to use [Dashlane's password generator](https://www.dashlane.com/features/password-generator).
* <mark style="color:blue;">`Secure`</mark>: If you want to use SSL for your domain, you have to enable this by setting the value to true. Some users may report that enabling this setting makes them unable to connect to the dashboard. If this is the case, try disabling this setting.
* <mark style="color:blue;">`trustProxy`</mark>: If you use a Reverse Proxy, like Nginx or Cloudflare Tunnels, you must enable this setting for the dashboard to trust proxies.
* <mark style="color:blue;">`SessionExpires`</mark>: This setting controls when the user should be logged out after logging in. For example, if this setting is set to 30d, the user gets logged out after 30 days instead of the usual 7 days.

### Step 3: Restart and test

Once all of theses has been configured, you can restart your bot. If everything you did went correctly, the dashboard should be usable by the URL you set in the config.yml of the dashboard addon, and you should be able to login to the dashboard via Discord.

### Plex Staff Dashboard:

The steps are almost the same for Plex Tickets Dashboard, so you can also use the steps above to setup the dashboard for Plex Staff.\
The only difference is that you have to set every roles permissions in the config.yml file, and the dashboard configuration is located in the main config.yml not in the addons folder, as the dashboard for Plex Staff is included.

{% hint style="success" %}
Congrats! Your dashboard should be up and running after following all of theses steps.
{% endhint %}
