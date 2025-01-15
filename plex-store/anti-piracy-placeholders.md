---
description: Guide to Using Anti-Piracy Placeholders
---

# Anti-piracy placeholders

When distributing digital products, it's essential to ensure that each copy is securely tied to the user who downloaded it. This helps in preventing piracy and unauthorized distribution. The anti-piracy placeholders provide a simple yet effective way to embed unique information into each file downloaded by a user. Here’s how you can use these placeholders effectively:



**Placeholder Overview**

* **%%\_\_USER\_\_%%**:
  * **Function**: Inserts the downloader’s Discord user ID.
  * **Use Case**: Identifying the specific user who downloaded the file.
* **%%\_\_PRODUCT\_\_%%**:
  * **Function**: Inserts the name of the product being downloaded.
  * **Use Case**: Embedding the product name for personalization and clarity in the file.
* **%%\_\_NONCE\_\_%%**:
  * **Function**: Inserts a unique hash for each download.
  * **Use Case**: A critical component for tracking and anti-piracy measures. This hash ensures that the download cannot be faked or altered.
* **%%\_\_PLEXSTORE\_\_%%**:
  * **Function**: Indicates that the product was downloaded through the Plex Store.
  * **Use Case**: Verification that the download originated from the official store (returns 'true' if downloaded from your Plex Store)



**Include Placeholders in Your Original Files**:

* Before uploading your product file to the Plex Store, insert the following placeholders into your file(s) wherever appropriate. These placeholders will be automatically replaced with actual data when a user downloads the file.

**Upload the Product File**:

* After including the placeholders, upload your product file to the Plex Store as usual. There’s no need for any additional steps; the placeholders will be automatically replaced during the download process.

**Automatic Replacement During Download**:

* When a user downloads the product, the placeholders in all files will be replaced with the following information:
  * **%%\_\_USER\_\_%%**: The Discord user ID of the downloader.
  * **%%\_\_PRODUCT\_\_%%**: The name of the product being downloaded.
  * **%%\_\_NONCE\_\_%%**: A unique hash generated for each download. This hash is unique to the download and cannot be faked or modified.
  * **%%\_\_PLEXSTORE\_\_%%**: A marker that indicates the product was downloaded through Plex Store. This will always return 'true'.

You don't have to use all placeholders, you can use how many you want, and spread them out in multiple files, etc..



**Tracking and Authenticity**:

* The **%%\_\_NONCE\_\_%%** placeholder is particularly important. This unique identifier is saved in the database along with the download details. If your product is ever found to be distributed without authorization, you can use the NONCE to trace the download back to the original user.
* Simply search for the NONCE ID in the staff panel’s anti-piracy page to retrieve all information about that specific download, including the user’s identity.



**Supported File Formats**: The placeholders can be embedded in various text-based files, including:

* `.txt` - Plain Text files
* `.md` - Markdown files
* `.rst` - reStructuredText files
* `.log` - Log files
* `.html`, `.htm` - HTML files
* `.xml`, `.xhtml` - XML files
* `.js`, `.ts`, `.jsx`, `.tsx` - JavaScript and TypeScript files
* `.json` - JSON files
* `.yml`, `.yaml` - YAML files
* `.sh`, `.bat`, `.py` - Shell scripts, Batch scripts, Python scripts
* `.java`, `.c`, `.cpp`, `.cs` - Java, C, C++, and C# source code files
* `.php`, `.rb`, `.go`, `.pl` - PHP, Ruby, Go, Perl scripts
* `.sql` - SQL scripts
* `.ini`, `.conf`, `.env` - Configuration files
* `.css`, `.scss`, `.less` - Stylesheets
* `.ejs`, `.hbs`, `.handlebars`, `.twig`, `.mustache`, `.njk`, `.jinja` - Templating files
* `.toml`, `.cfg` - Configuration files for various applications
* `.class`

**Special Handling of `.zip` and `.jar` Files**

In addition to the supported text-based file formats, the system can also handle `.zip` and `.jar` files. Here’s how it works:

* When you upload a `.zip` or `.jar` file containing text-based files with placeholders, the system will automatically:
  * **Extract the contents of the archive.**
  * **Identify and process all supported text files within the archive, replacing placeholders as described.**
  * **Recompress the modified files into a new `.zip` or `.jar` file.**

This means you can include placeholders in any text-based files inside a `.zip` or `.jar` archive, and they will be replaced just like standalone text files. The archive will then be reassembled with the placeholders replaced.
