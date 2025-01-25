---
description: >-
  Our products requires different dependencies for different operating systems.
  Please make sure you have all dependencies installed for your OS or our
  products may not start or function properly.
---

# Requirements

## Dependencies:

* Node.js 20.x.x LTS or above
* Hosting (VPS, Dedicated Server, Bot Hosting) with at least 512MB of RAM and 1 CPU core
* A text editor
* A stable Internet connection
* All NPM packages listed in the package.json (automatically installed with `npm install`)

{% hint style="danger" %}
The use of **Replit**, **Heroku**, **Glitch**, or other similar free hosting platforms is strictly prohibited. These platforms often make your code publicly accessible by default, putting your intellectual property at risk. If you choose to upload your code to such services, you are solely responsible for any unauthorized access, sharing, or public disclosure that may occur. You may also have your license revoked if the code is publicly accessible.
{% endhint %}

## Windows Dependencies

1. **Visual Studio Desktop Development C++**
   * Required for compiling native Node.js modules.
2. **Install Node.js LTS**
   * Download and install the latest Long-Term Support (LTS) version of Node.js directly from the [official Node.js website](https://nodejs.org/en/).
3. **Install Build Tools**
   *   Open an administrative Command Prompt and run the following command to install the necessary build tools:

       ```bash
       npm install --global --production --vs2018 --add-python-to-path windows-build-tools
       ```

***

## Linux Dependencies <a href="#linux-dependencies" id="linux-dependencies"></a>

**Required Packages**

* **Common Packages:**
  * `autoconf`, `automake`, `g++`, `libtool`, `build-essential`
  * These tools are required to build and run native Node.js modules.

**Installing Node.js and Dependencies**

**For Debian/Ubuntu:**\
Run the following commands to install the required packages and the latest Node.js LTS:

```bash
# Install required build tools
sudo apt-get install -y autoconf automake g++ libtool build-essential

# Add NodeSource repository for the latest Node.js
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -

# Install Node.js
sudo apt-get install -y nodejs
```

**For CentOS/RHEL:**\
Run these commands to install the required packages and the latest Node.js LTS:

```bash
# Install Development Tools group for CentOS
sudo yum groupinstall -y "Development Tools"

# Add NodeSource repository for the latest Node.js
curl -fsSL https://rpm.nodesource.com/setup_20.x | sudo bash -

# Install Node.js
sudo yum install -y nodejs
```

**Verify Installation**

After installation, verify that Node.js and npm are correctly installed by running:

```bash
node -v
npm -v
```
