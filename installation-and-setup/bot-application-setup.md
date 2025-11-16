# Bot Application Setup

### Creating your bot <a href="#creating-your-bot" id="creating-your-bot"></a>

1. Visit the [Discord Developer Portal](https://discord.com/developers/applications).
2. Click **"New Application"** and give it a name.
3. Go to the **"Installation"** tab:
   * Uncheck **User Install**
   * Set **Install Link** to `"None"`

<figure><img src="https://docs.drakodevelopment.net/~gitbook/image?url=https%3A%2F%2F793846788-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FH32pcDz3SxP8UThFTci3%252Fuploads%252FWYV7Wy9ch6YYBkmBqVdM%252F%257B508D5FA0-C009-41BB-BE1F-7A5B5810FD65%257D.png%3Falt%3Dmedia%26token%3D9c1880ad-ae5f-488a-ab12-a8e9ddc728e8&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=db8b6afc&#x26;sv=2" alt=""><figcaption></figcaption></figure>

\
1\. Navigate to the **"Bot"** tab:

* Click **"Add Bot"**
* Under **Privileged Gateway Intents**, enable:
  * `PRESENCE INTENT`
  * `SERVER MEMBERS INTENT`
  * `MESSAGE CONTENT INTENT`
* Under **Public Bot** settings:
  * Disable **Public Bot**
  * Untick **Require OAuth2 Code Grant**

<figure><img src="https://docs.drakodevelopment.net/~gitbook/image?url=https%3A%2F%2F793846788-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FH32pcDz3SxP8UThFTci3%252Fuploads%252Fxs5tgC3GPqmoq7OZL9JO%252F%257BB228AEFE-BD1B-415D-A001-A7675A7C6053%257D.png%3Falt%3Dmedia%26token%3Dab0e1aac-876f-4dec-af51-e21bdaf2c9bd&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=fc3a1863&#x26;sv=2" alt=""><figcaption></figcaption></figure>

* Click **Save Changes**
* Copy your **Bot Token** from the Token section

{% hint style="success" %}
**Note:** All of these options are found under the **Bot** tab.
{% endhint %}
