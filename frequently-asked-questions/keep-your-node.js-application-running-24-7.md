---
description: >-
  To keep a Node.js application running 24/7 on your VPS, you can use the screen
  command. Follow these steps:
---

# Keep Your Node.js Application Running 24/7

## Option 1: Using screen

### 1. **Create a Screen Session**

A screen session allows the bot to keep running even when you close the terminal. To start a new screen session, run:

```bash
screen -S PlexTickets
```

Now, you're inside the new screen session. _(You can replace PlexTickets with a name of your choice)_



### 2. **Start the Bot**

1.  Navigate to the folder where your application is installed:

    ```bash
    cd /path/to/plex-tickets
    ```

    _(Replace `/path/to/plex-tickets` with the actual path, e.g., `/home/PlexTickets`)_
2.  Start the application by running:

    ```bash
    node .
    ```



### 3. **Detach from the Screen**

Once the bot is running, you can safely detach from the screen session without stopping the bot. To do this:

* Press `CTRL + A`, then press `D (All at the same time)`

You will return to the regular terminal, and the bot will continue running in the background.



### 4. **Reconnect to the Screen**

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



### 5. **Stop or Restart the Application**

* To stop the application, simply press `CTRL + C` inside the screen session.
* To restart, run the `node .` command again.



## Option 2: Using tmux



### 1. Install tmux

First you have to install tmux to your vps using:

```bash
sudo apt install tmux -y
```

### 2. Create a tmux session

To create a tmux session you just have to run:

```bash
tmux
```

### 3. Start the bot

Next you have to start the bot by running:

```bash
node .
```

in the plex directory.&#x20;

### 4. Detach session

To detach the session you have to press `ctrl+B` then D.

### 5. Reattach the session

To attach the session again you have to run the command:

```bash
tmux attach -t ID
```

If you dont know the ID yet:

```bash
tmux ls
```



### 6. Stop or restart the bot&#x20;

To restart or stop the but you just have to reattach the session, then press `ctrl+C`



{% hint style="warning" %}
The application will stop if you restart or shut down the VPS. After rebooting, repeat the steps to start the bot. Keep the VPS running to ensure the bot is active 24/7.
{% endhint %}

