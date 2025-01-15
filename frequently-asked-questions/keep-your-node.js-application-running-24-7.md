---
description: >-
  To keep your Node.js application running 24/7 on your VPS, you can use the
  screen command. Follow these steps:
---

# Keep Your Node.js Application Running 24/7



#### 1. **Create a Screen Session**

A screen session allows the bot to keep running even when you close the terminal. To start a new screen session, run:

```bash
screen -S PlexTickets
```

Now, you're inside the new screen session. _(You can replace PlexTickets with a name of your choice)_



#### 2. **Start the Bot**

1.  Navigate to the folder where your application is installed:

    ```bash
    cd /path/to/plex-tickets
    ```

    _(Replace `/path/to/plex-tickets` with the actual path, e.g., `/home/PlexTickets`)_
2.  Start the application by running:

    ```bash
    node .
    ```



#### 3. **Detach from the Screen**

Once the bot is running, you can safely detach from the screen session without stopping the bot. To do this:

* Press `CTRL + A`, then press `D (All at the same time)`

You will return to the regular terminal, and the bot will continue running in the background.



#### 4. **Reconnect to the Screen**

If you ever need to access the bot or restart it, follow these steps:

1.  List all active screen sessions:

    ```bash
    screen -ls
    ```

    You’ll see a list of active screens, something like:

    ```
    12345.PlexTickets
    ```
2.  Reconnect to the screen session by running:

    ```bash
    screen -r <screen_id>
    ```

    _(Replace `<screen_id>` with the actual ID, e.g., `12345`)_



#### 5. **Stop or Restart the Application**

* To stop the application, simply press `CTRL + C` inside the screen session.
* To restart, run the `node .` command again.



{% hint style="warning" %}
The application will stop if you restart or shut down the VPS. After rebooting, repeat the steps to start the bot. Keep the VPS running to ensure the bot is active 24/7.
{% endhint %}

