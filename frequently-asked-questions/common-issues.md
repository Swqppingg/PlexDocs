---
description: >-
  This page lists common issues you might encounter while using Plex Development
  products and their potential solutions.
---

# Common Issues

### MongooseError: Operation `tickets.findOne()` buffering timed out after 10000ms

### MongooseError: Operation `guilds.findOne()` buffering timed out after 10000ms

### MongooseServerSelectionError: Could not connect to any servers in your MongoDB Atlas cluster

#### Description:

These errors occur because MongoDB is unable to establish a successful connection. This can prevent your application from accessing the database properly. Common reasons include issues with network access, incorrect credentials, or an invalid connection URL.

#### Possible Causes and Fixes:

**1. IP Address Not Whitelisted in MongoDB**

MongoDB Atlas requires you to whitelist the IP address of your server to allow connections. If the IP address you're using to host your application isn't whitelisted, the connection will fail.

**How to Fix:**

* Log in to your [MongoDB Atlas](https://cloud.mongodb.com/) account.
* Navigate to your cluster and click on **Network Access**.
* Check if your server's IP address is listed. If not:
  1. Click **Add IP Address**.
  2. Enter your server's public IP address. You can find this using a command like `curl ifconfig.me` or by checking your VPS control panel.
  3. Save the changes and wait for them to take effect (this usually takes a few minutes).
* Alternatively, you can allow access from all IPs by adding `0.0.0.0/0` as the ip.

**2. Invalid Password in the Connection URL**

If the password in your MongoDB connection URL is incorrect, the connection will fail. Additionally, ensure the password is properly formatted in the URL.

**How to Fix:**

* Double-check your MongoDB username and password.
* Ensure the password does not include any special characters like `<`, `>`, or `&`. If your password contains special characters, encode them using a tool like [URL Encoder/Decoder](https://www.urlencoder.org/).
*   Example connection URL:

    ```
    mongodb+srv://username:yourpassword@cluster0.mongodb.net/myDatabase?retryWrites=true&w=majority
    ```

    Replace `yourpassword` with your actual password.

**3. Invalid Connection URL**

The connection URL might be incorrectly formatted, causing MongoDB to reject the connection.

**How to Fix:**

*   Verify the structure of your connection URL. A correct URL format is:

    ```
    mongodb+srv://<username>:<password>@<cluster-url>/<database>?retryWrites=true&w=majority
    ```

    Replace `<username>`, `<password>`, `<cluster-url>`, and `<database>` with your actual credentials and database name.
* Ensure your `cluster-url` matches the one provided by MongoDB Atlas.
* Check if your application’s configuration file (`config.yml` or equivalent) includes the proper connection string.

#### General Troubleshooting Tips:

* Verify that your server has outgoing network access to MongoDB Atlas (port 27017).
