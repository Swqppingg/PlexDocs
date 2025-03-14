# Bot Application Setup

### Creating your bot <a href="#creating-your-bot" id="creating-your-bot"></a>

1. Open [the Discord developer portal ](https://discord.com/developers/applications)and log into your account.
2. Click on the "New Application" button.
3. Enter a name and confirm the pop-up window by clicking the "Create" button.

You should see a page like this:

{% embed url="https://discordjs.guide/assets/create-app.ed82aede.png" %}

You can edit your application's name, description, and avatar here. Once you've saved your changes, move on by selecting the "Bot" tab in the left panel.

Click the "Add Bot" button on the right and confirm the pop-up window by clicking "Yes, do it!"

### Your token <a href="#your-token" id="your-token"></a>

{% hint style="danger" %}
This section is critical, so pay close attention. It explains what your bot token is, as well as the security aspects of it.
{% endhint %}

After creating a bot user, you'll see a section like this:

{% embed url="https://discordjs.guide/assets/created-bot.b809fb6e.png" %}

In this panel, you can give your bot an avatar, set its username, and make it public or private. You can access your token in this panel as well, either by revealing it or pressing the "Copy" button. When we ask you to paste your token somewhere, this is the value that you need to put in. Don't worry if you do happen to lose it at some point; you can always come back to this page and copy it again.

### Gateway Intents <a href="#your-token" id="your-token"></a>

{% hint style="danger" %}
This section is critical, so pay close attention. This step shows you how to enable all of the gateway intents for the bot to work correctly.
{% endhint %}

Under the page, you'll see a section called "Privileged Gateway Intents", which will look at this:

<figure><img src="../.gitbook/assets/firefox_madOMZ4uP6.png" alt=""><figcaption></figcaption></figure>

In this section, you **MUST** enable the following intents: the Presence Intent, the Server Members Intent, and the Message Content Intent. Make sure the intents are enabled for the bot to work correctly.
