---
description: A tutorial on how to setup and configure the dashboard for Plex Tickets
---

# Plex Tickets/Staff Dashboard

{% embed url="https://www.youtube.com/watch?v=iPDHqK_soD0" %}
[https://www.youtube.com/watch?v=iPDHqK\_soD0](https://www.youtube.com/watch?v=iPDHqK_soD0)
{% endembed %}

## Plex Tickets Dashboard

### Step 1: Downloading the files&#x20;

To begin the installation you have to download the dashboard from the [website](https://plexdevelopment.net/) or [BBB](https://builtbybit.com/resources/plex-tickets-discord-ticket-bot.22209/).\
After downloading you have to unzip it to the <mark style="color:blue;">`./addons/`</mark> folder.

### Step 2: Configure the dashboard

Next you have to open the <mark style="color:blue;">`./addons/Dashboard/config.yml`</mark> file, and configure it.

#### Filling out the config

{% hint style="warning" %}
**Important:** If you are using shared hosting without a VPS, remember to include the port in all the links provided below.
{% endhint %}

This part is very important to succeed. You have to consider that you want to use any proxy and or SSL for you dashboard.&#x20;

1. **Access Discord Developer Portal**
   * Go to the [Discord Developer Portal](https://discord.com/developers/applications).
   * Locate your bot's <mark style="color:blue;">`clientId`</mark> and <mark style="color:blue;">`clientSecret`</mark> under the OAuth2 section.
2. **Configure Callback URL**
   * Set the <mark style="color:blue;">`callbackURL`</mark> specified in the <mark style="color:blue;">`config.yml`</mark> file.
   * If using a domain, format it as <mark style="color:blue;">`http://ticket.yourdomain.com/auth/discord/callback`</mark>.
   * For SSL, use <mark style="color:blue;">`https://ticket.yourdomain.com/auth/discord/callback`</mark>.
   * Add this URL to the Redirect URL section on the Developer Portal.

Now you only have 6 fields left to configure:

* <mark style="color:blue;">`Port`</mark>: you can change this to anything, just be aware that it can't be used by any other programs on the VPS.&#x20;
* <mark style="color:blue;">`URL`</mark>: The link you want to access the dashboard in the future.
* <mark style="color:blue;">`secretKey`</mark>: you can set anything to this but it has to be a string so random characters. We recommend to use [Dashlane's password generator](https://www.dashlane.com/features/password-generator).
* <mark style="color:blue;">`Secure`</mark>: IF you want to use SSL for your domain, you have to enable this by setting its value to true.
* <mark style="color:blue;">`trustProxy`</mark>`:` If you don't want to use the port in the URL you have to use a tool called Reverse Proxy, for example Nginx. There is a tutorial about how to set it up [here](setting-up-a-reverse-proxy-with-nginx.md). So If you want to use it you have to set this to true.
* <mark style="color:blue;">`SessionExpires`</mark>`:` you can set this to any day value like 7d, 14d, 30d etc. This controls how much time a login can last. Like if you set this to 30d, and login to the dashboard, you will be logged out after 30 days, instead of the default 7 days.

### Step 3: Restart and test

Next you can restart your bot and if you did everything correctly, the dashboard should be usable by the URL you set in the config.yml of the dashboard addon.&#x20;

## Plex Staff Dashboard

### Step 1: Configure the dashboard

Its almost 1/1 the same as Plex Tickets Dashboard configuration, so you can use that to configure plex staff too!\
The only difference is that you have to set every roles permissions in the config.yml file, and the dashboard configuration is located in the main config.yml not in the addons folder.

