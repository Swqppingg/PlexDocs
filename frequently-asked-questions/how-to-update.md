---
description: >-
  Follow these steps carefully to update your Plex Tickets, Plex Staff, or Plex
  Status product to the latest version without losing your configurations or
  data:
---

# How to update

{% hint style="danger" %}
**Note:** This guide only covers updating **Plex Tickets**, **Plex Staff**, **Plex Status,** and **Plex Forms**. For instructions on how to update **Plex Store**, please visit [this link](../plex-store/how-to-update.md).
{% endhint %}



## Plex Tickets/Plex Staff/Plex Status/Plex Forms:

### **Step 1: Backup Your Configurations**

1. Locate your `config.yml` file in the bot’s directory.
2. Create a **backup** of this file by copying it to a safe location (e.g., your desktop or a backup folder).
   * This ensures you can restore your settings if anything goes wrong during the update.

***

### **Step 2: Download the Latest Update**

1. Visit the official platform where you downloaded the bot to get the latest version.
2. Download the update files to your computer.

***

### **Step 3: Replace Existing Files**

1. Navigate to your bot’s installation directory.
2. **Replace all existing files** with the newly downloaded ones.

**Plex Status:** Don't replace the `history.json` or `lastUpdated.json` file.

**Plex Forms:** Don't replace or delete the `uploads` folder

**Plex Staff:** Don't replace or delete the `uploads` folder

***

### **Step 4: Update the Configuration File**

1. Open your **old `config.yml` file** in a text editor (e.g., Visual Studio Code or Notepad++).
2. Open the **new `config.yml` file** (included in the update) in another text editor.
3. **Manually copy your settings** from the old file to the new one.
   * This ensures compatibility with any new options or changes introduced in the updated version.
4. Save the updated `config.yml` file once all changes are copied.

***

### **Step 5: Install Dependencies (if needed)**

1.  If the update includes new dependencies, you may need to run the following command:

    ```bash
    npm install
    ```

    * This ensures all required Node.js packages are installed.

***

### **Step 6: Start the Bot**

1. Start the bot as you normally would.
2. Verify that everything works as expected.

{% hint style="success" %}
By following these steps, you’ll ensure a smooth update process while keeping your configurations and data intact. For any issues or questions, feel free to reach out via our [Discord Server](https://discord.gg/plexdev).
{% endhint %}
