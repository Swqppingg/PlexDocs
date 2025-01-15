---
description: 'Follow these steps to install and run the bot on your Linux server:'
---

# Linux Installation Guide

### **Step 1: Log in to Your VPS**

1. Log in to your VPS using your preferred SSH client or terminal software (e.g., PuTTY, MobaXterm, or any similar tool).

***

### **Step 2: Place Bot Files on the Server**

1. Ensure the bot files are uploaded to a directory of your choice on the server.

***

### **Step 3: Navigate to the Bot Directory**

1.  Open a terminal on the server and navigate to the folder containing your bot files using the `cd` command:

    ```bash
    cd /path/to/your-bot-directory
    ```

***

### **Step 4: Install Node.js Modules**

1. Ensure all required Linux dependencies are installed.
   * For a list of required dependencies, refer to the [Linux Dependencies Guide](requirements.md).
2.  Install the Node.js modules required for the bot by running:

    ```bash
    npm install
    ```

    * This will install all necessary dependencies as listed in the `package.json` file.

***

### **Step 5: Start the Bot**

1.  Run the bot with the following command:

    ```bash
    node index
    ```
2. Check the terminal output to ensure the bot starts without errors.

***

{% hint style="info" %}
### **Keeping the Bot Online 24/7**

To keep the bot running continuously, you can use the `screen` command. [Click here for a detailed guide on using `screen`.](../frequently-asked-questions/keep-your-node.js-application-running-24-7.md)
{% endhint %}





