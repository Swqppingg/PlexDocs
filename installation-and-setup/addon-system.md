---
description: >-
  This guide explains how to create a basic addon for our bots. Addons allow
  users to extend the bot's functionality without modifying the main codebase.
---

# Addon System

#### **What is an Addon?**

An addon is a file or group of files inside the `addons/` folder that can:

* **Listen to events**: React to things happening in the bot (e.g., when a message is sent or a member joins).
* **Add slash commands**: Create commands that users can type into Discord starting with `/`.

You can choose to use **only events**, **only commands**, or **both** in an addon. It's up to you!



#### **Addon File Requirements**

1. **Event Listener Files**:
   * These files can be named **anything** (e.g., `myEvents.js`).
   * Use event listeners to react to bot activities, like a user sending a message.
2. **Slash Command Files**:
   * These files **must start with `cmd_`** (e.g., `cmd_exampleCommand.js`).
   * Use slash commands to create commands users can trigger with `/`.



#### **How the Addon System Works**

1. **Event Handlers**:
   * All events (like `messageCreate` or `guildMemberAdd`) are centralized in the bot using something called an `eventHandler`.
   * You can use `on` to listen for these events in your addon.
2. **Slash Command Handlers**:
   * If you include a file that starts with `cmd_`, the bot will automatically load it as a slash command.



#### **Step 1: Creating an Event Listener (Optional)**

To listen to events, create a new file in the `addons/` folder. The file name can be anything, like `myEventAddon.js`.

**Example: Listening to `messageCreate`**

Here’s how you can listen for messages and respond when someone says `!hello`:

```javascript
module.exports.register = ({ on }) => {
    on('messageCreate', (message) => {
        if (message.content === 'hello') {
            message.channel.send('Hello! This message is from my custom addon.');
        }
    });
};
```



#### **Step 2: Creating a Slash Command (Optional)**

If you want to create a slash command, the file must start with `cmd_`, for example: `cmd_greet.js`.

**Example: A Simple Slash Command**

Here’s how you can create a `/greet` command:

```javascript
const { SlashCommandBuilder } = require('@discordjs/builders');

module.exports = {
    data: new SlashCommandBuilder()
        .setName('greet')
        .setDescription('Sends a greeting message.'),
    async execute(interaction, client) {
        await interaction.reply('Hello! This is a slash command from my addon.');
    },
};
```

#### **Step 3: Combining Events and Commands**

You can create both an event listener and a slash command in the same addon. Just use a separate file for each.

**Example File Structure**

```bash
/addons/
  myAddon/
    myEvents.js        <-- Handles events like messageCreate
    cmd_greet.js       <-- Handles the /greet slash command
```

**Example: myEvents.js**

```javascript
module.exports.register = ({ on }) => {
    on('messageCreate', (message) => {
        if (message.content === '!ping') {
            message.channel.send('Pong! This message is from the event listener in my addon.');
        }
    });

    on('guildMemberAdd', (member) => {
        console.log(`${member.user.tag} joined the server.`);
    });
};
```

**Example: cmd\_greet.js**

```javascript
const { SlashCommandBuilder } = require('@discordjs/builders');

module.exports = {
    data: new SlashCommandBuilder()
        .setName('greet')
        .setDescription('Sends a greeting message.'),
    async execute(interaction, client) {
        await interaction.reply('Hello from the /greet command!');
    },
};
```

#### **Step 4: Loading Your Addon**

* Place your addon files in the `addons/` folder.
* The bot will automatically detect and load event listener files and slash commands when it starts.





#### **Advanced Example: Fully Featured Addon**

Here’s an example addon that listens for events and includes a slash command:

**File Structure**

```lua
/addons/
  exampleAddon/
    events.js        <-- Handles bot events
    cmd_example.js   <-- Handles a slash command
```

**File: `events.js`**

This file contains event listeners for various bot events.

<pre class="language-javascript"><code class="lang-javascript"><strong>const { ActionRowBuilder, ButtonBuilder, EmbedBuilder } = require('discord.js');
</strong>
module.exports.register = ({ on }) => {
    // Example: Respond to a specific message
    on('messageCreate', (message) => {
        if (message.content === '!info') {
            const embed = new EmbedBuilder()
                .setColor('#0099ff')
                .setTitle('Bot Information')
                .setDescription('This is an example addon showcasing embeds and buttons.')
                .setFooter({ text: 'Example Addon', iconURL: 'https://example.com/icon.png' });

            const row = new ActionRowBuilder().addComponents(
                new ButtonBuilder()
                    .setCustomId('info_button')
                    .setLabel('Click Me!')
                    .setStyle('Primary')
            );

            message.channel.send({ embeds: [embed], components: [row] });
        }
    });

    // Example: Handle a button click
    on('interactionCreate', async (interaction) => {
        if (!interaction.isButton()) return;

        if (interaction.customId === 'info_button') {
            await interaction.reply({
                content: 'You clicked the button! This response is from the example addon.',
                ephemeral: true,
            });
        }
    });

    // Example: Log when the bot is ready
    on('ready', () => {
        console.log('The advanced example addon is loaded and ready!');
    });
};
</code></pre>

**File: `cmd_advanced.js`**

This file contains a slash command definition and its execution logic.

```javascript
const { SlashCommandBuilder } = require('@discordjs/builders');
const { ActionRowBuilder, ButtonBuilder, EmbedBuilder } = require('discord.js');

module.exports = {
    data: new SlashCommandBuilder()
        .setName('advanced')
        .setDescription('An advanced slash command example.'),

    async execute(interaction, client) {
        const embed = new EmbedBuilder()
            .setColor('#00ff00')
            .setTitle('Advanced Slash Command')
            .setDescription('This command demonstrates an embed with buttons.')
            .setFooter({ text: 'Example Addon', iconURL: 'https://example.com/icon.png' });

        const row = new ActionRowBuilder().addComponents(
            new MessageButton()
                .setCustomId('slash_button')
                .setLabel('Press Me!')
                .setStyle('Success')
        );

        await interaction.reply({
            embeds: [embed],
            components: [row],
        });
    },
};
```





### How to Create an Addon with MongoDB Integration

Integrating MongoDB with your addon is simple and allows you to store and retrieve data from the same database used by the main bot. This guide will show you how to set up a MongoDB model in your addon and use it effectively.

#### **Step 1: Create a MongoDB Model**

Add your MongoDB models in the same folder as your addon. For example, you can create a file called `exampleModel.js` inside your addon folder.

**File: `exampleModel.js`**

Here’s an example model for storing example data:

```javascript
const mongoose = require('mongoose');

// Define the schema
const ExampleSchema = new mongoose.Schema({
  userId: { type: String, required: true }, // The user's ID
  points: { type: Number, default: 0 },    // Example: Points the user has
  createdAt: { type: Date, default: Date.now }, // When the entry was created
});

// Export the model
module.exports = mongoose.model('Example', ExampleSchema);
```

#### **Step 2: Use the Model in Your Addon**

To use the model in your addon, import it just like you would in any other Node.js project. You can now interact with the database using MongoDB methods.

Here’s an example slash command to interact with the database:

```javascript
const { SlashCommandBuilder } = require('@discordjs/builders');
const ExampleModel = require('./exampleModel'); // Import the model

module.exports = {
    data: new SlashCommandBuilder()
        .setName('setpoints')
        .setDescription('Set points for a user.')
        .addUserOption(option =>
            option.setName('target')
                .setDescription('The user to set points for')
                .setRequired(true))
        .addIntegerOption(option =>
            option.setName('points')
                .setDescription('The number of points to set')
                .setRequired(true)),

    async execute(interaction) {
        const targetUser = interaction.options.getUser('target');
        const points = interaction.options.getInteger('points');

        if (points < 0) {
            return interaction.reply('Points must be a non-negative number.');
        }

        // Update or create the user in the database
        let user = await ExampleModel.findOne({ userId: targetUser.id });
        if (!user) {
            user = new ExampleModel({ userId: targetUser.id, points });
        } else {
            user.points = points;
        }

        await user.save(); // Save the changes

        interaction.reply(`${targetUser.username} now has ${user.points} points.`);
    },
};
```





### **Full Example Addon with MongoDB integration**

**File Structure**

```lua
/addons/
  mongodbExample/
    events.js        <-- Handles bot events
    cmd_example.js   <-- Handles a slash command
    exampleModel.js  <-- MongoDB model
```

**Code Recap**

1. **`exampleModel.js`:**

```javascript
const mongoose = require('mongoose');

const ExampleSchema = new mongoose.Schema({
  userId: { type: String, required: true },
  points: { type: Number, default: 0 },
  createdAt: { type: Date, default: Date.now },
});

module.exports = mongoose.model('Example', ExampleSchema);
```

2. **`events.js`:**

```javascript
const ExampleModel = require('./exampleModel');

module.exports.register = ({ on }) => {
    on('messageCreate', async (message) => {
        if (message.content.startsWith('!addpoints')) {
            const userId = message.author.id;
            const pointsToAdd = parseInt(message.content.split(' ')[1]) || 0;

            let user = await ExampleModel.findOne({ userId });
            if (!user) user = new ExampleModel({ userId, points: pointsToAdd });
            else user.points += pointsToAdd;

            await user.save();
            message.channel.send(`${message.author.username} now has ${user.points} points!`);
        }

        if (message.content.startsWith('!checkpoints')) {
            const userId = message.author.id;
            const user = await ExampleModel.findOne({ userId });
            message.channel.send(user ? `You have ${user.points} points.` : 'You have no points yet!');
        }
    });
};
```

3. **`cmd_example.js`:**

```javascript
const { SlashCommandBuilder } = require('@discordjs/builders');
const ExampleModel = require('./exampleModel');

module.exports = {
    data: new SlashCommandBuilder()
        .setName('setpoints')
        .setDescription('Set points for a user.')
        .addUserOption(option =>
            option.setName('target')
                .setDescription('The user to set points for')
                .setRequired(true))
        .addIntegerOption(option =>
            option.setName('points')
                .setDescription('The number of points to set')
                .setRequired(true)),

    async execute(interaction) {
        const targetUser = interaction.options.getUser('target');
        const points = interaction.options.getInteger('points');

        let user = await ExampleModel.findOne({ userId: targetUser.id });
        if (!user) user = new ExampleModel({ userId: targetUser.id, points });
        else user.points = points;

        await user.save();
        interaction.reply(`${targetUser.username} now has ${user.points} points.`);
    },
};
```

