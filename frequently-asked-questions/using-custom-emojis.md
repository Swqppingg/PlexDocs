---
description: >-
  This guide will walk you through the process of adding custom emojis to your
  Discord bot's configuration file.
---

# Using Custom Emojis

To use a custom emoji in your Discord bot's configuration, follow these steps:

1. **Type the Emoji in Chat**
   * In any Discord chat, type your custom emoji’s name (e.g., `:plexdev:`).
2. **Add a Backslash (`\`) Before the Emoji**
   *   Before sending the message, add a `\` before the emoji. It should look like this:

       ```
       \:plexdev:
       ```
3. **Send the Message**
   *   Once sent, Discord will convert it into its full emoji ID format, like this:

       ```
       <:plexdev:1038186189448036475>
       ```
4. **Copy the Emoji Code**
   * Copy the entire output, including the `<:emoji_name:emoji_id>` format.
5. **Paste It in Your Bot’s Config**
   * Use the copied emoji code in your bot’s configuration file or code where needed.

{% hint style="success" %}
Now, your bot will be able to display the custom emoji correctly!
{% endhint %}
