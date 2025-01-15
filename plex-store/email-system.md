---
description: Plex Store comes with SendGrid support
---

# Email System

**What is SendGrid?**

SendGrid is a service that helps you send emails from your apps or websites, like receipts, password resets, or newsletters. It’s free to get started and easy to set up—just create an account and use an API key to start sending emails quickly and securely.

\
Plex Store uses emails for the following:

* When a customer purchases an item it sends them a confirmation email with a list of what they bought.
* General notifications



### How to Get an API Key from SendGrid (Free)

### Step 1: Create a SendGrid Account

1. **Visit SendGrid**: Go to [SendGrid's website](https://sendgrid.com/).
2.  **Sign Up**: If you don’t have an account, click on the **Sign Up** button. Fill out the required information. (You will most likely need to add 2FA, or verify your phone number)

    _Image Description_: An image showing the SendGrid homepage with the **Sign Up** button highlighted.
3. **Choose a Free Plan**: During the sign-up process, choose the free plan.

<figure><img src="../.gitbook/assets/step1.png" alt=""><figcaption></figcaption></figure>

### Step 2: Log In to Your SendGrid Account

1. **Log In**: After signing up, log in to your SendGrid account using your credentials.

### Step 3: Navigate to API Keys

1.  **Access the Dashboard**: Once logged in, you’ll be directed to the SendGrid dashboard.

    _Image Description_: The SendGrid dashboard, highlighting the left-side navigation panel.
2. **Go to API Keys**: On the left sidebar, click on **Settings** and then select **API Keys** from the dropdown menu.

<figure><img src="../.gitbook/assets/step2.png" alt=""><figcaption></figcaption></figure>

### Step 4: Create an API Key

1. **Create a New API Key**: Click on the **Create API Key** button.
2. **Name Your API Key**: A prompt will appear asking you to name your API Key. Enter a descriptive name, such as “MyAppAPIKey”.
3. Click the **Create & View** button. Your API Key will be displayed. **Make sure to copy and store it securely**. You won’t be able to view it again.

<figure><img src="../.gitbook/assets/step3.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/step5.png" alt=""><figcaption></figcaption></figure>

### Step 5: Copy the API Key into Your `config.yml` File

1. Open the `config.yml` and paste the API Key wherever you need it.
