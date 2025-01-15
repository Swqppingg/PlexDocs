---
description: >-
  This guide will walk you through setting up a reverse proxy using Nginx on an
  Ubuntu (Linux) VPS or dedicated server.
---

# Setting Up a Reverse Proxy with Nginx

A reverse proxy allows you to use a custom domain for your self-hosted Node.js applications (like websites and bots with dashboards).

{% hint style="danger" %}
This guide is only applicable if you're using a VPS, dedicated server, or similar. Shared hosting does not support custom reverse proxy setups.
{% endhint %}

### What is a Reverse Proxy?

A reverse proxy is a server that forwards requests from clients (e.g., web browsers) to another server. For example, when a user visits `https://yourdomain.com`, the reverse proxy directs the request to your application running locally (e.g., on `http://localhost:3000`). This is essential for:

* Using a custom domain with your application.
* Handling HTTPS (secure connections).
* Better performance and security management.

This guide assumes you already have:

1. An Ubuntu VPS or dedicated server.
2. Nginx installed.
3. Your Node.js application running locally (e.g., on `http://localhost:3000`).

###

### Step 1: Install Nginx

Nginx is a lightweight, high-performance web server that will act as the reverse proxy for your application. Follow these steps to install it:

1.  Update your package list:

    ```
    sudo apt update
    ```
2.  Install Nginx:

    ```
    sudo apt install nginx -y
    ```
3.  Start and enable Nginx to ensure it runs on boot:

    ```
    sudo systemctl start nginx
    sudo systemctl enable nginx
    ```
4. Verify the installation by visiting your server's public IP address in a browser. You should see the default Nginx welcome page.

#### Explanation:

* `apt update`: Updates the package list to ensure you get the latest version of Nginx.
* `apt install nginx`: Installs Nginx.
* `systemctl start nginx`: Starts the Nginx service immediately.
* `systemctl enable nginx`: Ensures Nginx starts automatically when the server boots.

### Step 2: Upload your files to the server

The first step is to upload the product files to your server. Follow these instructions:

1. Use an FTP client (e.g., FileZilla)
2. Place the product folder in a directory, such as `/home/your_product_folder`.

Place your files in an easily accessible directory, such as `/home`, for better organization and management.



### Step 3: Create a New Nginx Configuration File

Run the following command to edit/create your Nginx configuration file:

```
sudo nano /etc/nginx/sites-available/your_domain
```

Add the following configuration:

```
server {
    server_name example.com; # Change to your domain.

    location / {
        proxy_pass http://localhost:3000; # Keep localhost as it is. Change only the port if needed.
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
        proxy_set_header X-Real-IP $remote_addr;
    }

    error_page 502 /502.html;
    location = /502.html {
        root /home/PlexStore;
    }
}
```

#### Important Notes:

* **`proxy_pass`:** Always keep `localhost` the same, even if your domain changes. The port number (`3000`) must match the port your application is using, as configured in your product's `config.yml` file. For example, if your product's `config.yml` specifies port `4000`, replace `3000` with `4000`.
* **`server_name`:** Replace `example.com` with your actual domain name.
* **`root`:** Specifies the directory where your custom error page is located. This should be the path of where your product is located.

Save and close the file (press `Ctrl+O`, `Enter`, and `Ctrl+X`).



### Step 4: Enable the Configuration

Run the following commands:

```
sudo ln -s /etc/nginx/sites-available/your_domain /etc/nginx/sites-enabled/
sudo unlink /etc/nginx/sites-enabled/default
```

#### Explanation:

* `ln -s`: Creates a symbolic link to enable your new configuration.
* `unlink`: Disables the default Nginx configuration to avoid conflicts.



### Step 5: Test and Reload Nginx

Run these commands:

```
sudo nginx -t
sudo systemctl reload nginx
```

#### Explanation:

* `nginx -t`: Tests your Nginx configuration for errors.
* `systemctl reload nginx`: Reloads Nginx to apply the new configuration.

If there are no errors, your reverse proxy is now set up!



### Step 6: Point Your Domain to the Server

To complete the setup, configure your domain's DNS settings:

1. Log in to your domain registrar's control panel.
2. Add an **A Record** with the following details:
   * **Name**: `@` (or leave it blank for the root domain).
   * **Value**: Your server's public IP address.

#### Important Notes:

* Ensure you only create a single **A Record** pointing to your server's IP.
* DNS propagation may take a few minutes to several hours.



### Step 7: Final Verification

Once the DNS changes have propagated, you should be able to access your application using your domain (e.g., `https://example.com`).

***

### Hosting Multiple Websites

If you need to host multiple Node.js applications, you can repeat all the steps in this guide for each application. Keep the following in mind:

1. Each application must run on a separate port (e.g., `3001`, `3002`, etc.). Ensure the `proxy_pass` directive in the Nginx configuration file matches the port used by the application.
2. Use a unique domain or subdomain for each application by updating the `server_name` directive accordingly.
3. Ensure that each application is running independently and that the correct ports are open on your VPS or server.

By following these guidelines, you can host multiple applications and manage them seamlessly using Nginx as a reverse proxy.



{% hint style="success" %}
Congratulations! Your setup is now complete. If everything is configured correctly, your application should be accessible via your custom domain. If you encounter any issues, double-check the steps above or contact support for assistance.
{% endhint %}
