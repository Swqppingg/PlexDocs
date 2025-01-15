---
description: >-
  This is a guide on how to update Plex Store. Follow these simple steps to
  update Plex Store while keeping your configuration and data intact.
---

# How to update



{% hint style="danger" %}
Never delete the `uploads` folder, it stores all essential data, including product files, product banners, images, and more. Deleting this folder will result in the loss of these important assets. Always ensure that the `uploads` folder remains intact when updating your bot.
{% endhint %}



### 1. **Backup Your Important Files**

Before you begin, make sure to back up your current configuration and any important data.

* **Backup `config.yml`**: This file contains your bot's configuration settings. Make a copy of it and store it somewhere safe.
* **Backup the `uploads` Folder**: If you have an `uploads` folder where files are stored, back this up as well. This is where all the product files and product banners are stored, and more.

### **2. Download the New Update**

Download the latest version of the product from where you have access.

### **3. Replace Existing Files**

Once you've downloaded the update:

* Extract the new files.
* **Replace all existing files** in your product's directory with the new ones you just downloaded.
* **Do not replace**:
  * The `config.yml` file
  * The `uploads` folder (if it exists and you want to feel extra safe)

### **4. Update Your config.yml File**

You’ll need to merge your old configuration with any new settings:

* **Open the old `config.yml`**: Use a text editor like Notepad, VSCode, etc.
* **Open the new `config.yml`**: Open the new version of this file in another text editor.
* **Compare and Update**: Manually copy your old configuration settings into the new `config.yml` file.
  * Alternatively, use a tool like [DiffChecker](https://www.diffchecker.com/) to easily spot the differences between the old and new files and merge them accordingly.

### 5. Install New Dependencies

Sometimes updates come with new dependencies. To install them:

* Open a terminal or command prompt.
* Navigate to your bot's directory.
* Run the following command:

```
npm install
```

This will install any new dependencies required by the updated bot.



### 6. Restart Your Bot

After completing the steps above, you can now start your bot:

* Use the command you usually use to start the bot, such as:

```
node index.js
```

or if you are using regular discord bot hosting/pterodactyl, then just use the start button on the panel.





{% hint style="success" %}
That's it! Your bot is now updated with minimal hassle. If you encounter any issues, double-check that your configuration settings are correct and that all necessary files have been updated.
{% endhint %}

