---
description: 'Follow these steps to install and run the bot on your Windows system:'
---

# Windows Installation Guide

### **Step 1: Unzip the Bot**

1. Download the bot's ZIP file from the official source.
2. **Unzip the file** into a folder of your choice.
   * Ensure the folder is in an accessible location, such as `C:\Bots\YourBotName`.

***

### **Step 2: Configure the Bot**

1. Open the `config.yml` file in a text editor (we recommend **Visual Studio Code** or **Notepad++**).
2. Configure the settings in `config.yml` to suit your needs:
   * [Add your **bot token** (from Discord Developer Portal).](bot-application-setup.md)
   * Add your **license key** (if applicable).
   * Customize other settings based on your requirements.
3. Save the file once all changes are made.

***

### **Step 3: Open Command Prompt**

1. Open the Command Prompt by searching for **"cmd"** in the Start menu and clicking on it.
2.  Navigate to your bot's directory using the `cd` command. For example:

    ```bash
    cd C:\Bots\YourBotName
    ```

***

### **Step 4: Install Node Modules**

1. Ensure you have **Node.js LTS** installed on your system.
   * If not, download and install the latest LTS version from [Node.js official website](https://nodejs.org/).
2.  In the Command Prompt, install the required Node.js dependencies by running:

    ```bash
    npm install
    ```

    * This command will install all the necessary modules listed in the `package.json` file.

***

### **Step 5: Start the Bot**

1.  Run the bot by typing the following command in the Command Prompt:

    ```bash
    node index
    ```
2. Check the Command Prompt for any startup messages or errors.

***

### **Step 6: Verify the Bot**

1. Open your Discord server and check if the bot is online.
   * If the bot isn’t online:
     * Double-check your **bot token** in the `config.yml`.
     * Verify that your **license key** is correctly entered.
2. If you’ve confirmed these are correct and the bot is still not working, create a ticket in our [Discord Server](https://discord.gg/plexdev) for further assistance.

{% hint style="success" %}
By following this guide, your bot should be up and running in no time. For additional help, feel free to reach out to our support team on Discord.
{% endhint %}

