# Plex Tickets: Categories & Panels

### Understanding the Basics

The ticket system is built around two main components:

1. **Ticket Panels** - These are the embed messages users interact with to create tickets
2. **Ticket Categories** - These define the different types of tickets users can create

Each panel can include multiple categories, and the same category can be used across different panels.

### Ticket Panels Configuration

Panels are defined in the `TicketPanels` section of your `config.yml` file. Here's how to set up a panel:

```yaml
TicketPanels:
  Panel1:  # This is the panel ID (must be unique)
    Name: "Support Panel"  # Display name for the panel
    Categories: ["TicketCategory1", "TicketCategory3"]  # List of category IDs to include
    Embed:  # Embed appearance settings
      Title: "Support Tickets"  # Panel title
      Description: "> If you need any assistance click on the button corresponding to the type of ticket you wish to open."
      Color: "#5e99ff"  # Hex color code, leave blank to use bot default
      PanelImage: "https://i.imgur.com/wOifew6.png"  # Large image in the embed
      CustomThumbnailURL: ""  # Small image in the corner of the embed
      Timestamp: false  # Whether to display timestamp
      Footer:  # Footer settings
        Enabled: true
        CustomIconURL: ""  # Footer icon
        text: ""  # Footer text
```

#### Adding Multiple Panels

You can create unlimited panels, To add another panel, simply add a new entry under `TicketPanels`:

```yaml
TicketPanels:
  Panel1:
    # Panel1 configuration...
    
  Panel2:  # This is the panel ID (must be unique)
    Name: "Applications Panel" 
    Categories: ["TicketCategory2", "TicketCategory5"]
    Embed:
      Title: "Staff Applications"
      Description: "Click a button below to apply for a staff position."
      Color: "#43B581"
      PanelImage: ""
      CustomThumbnailURL: ""
      Footer:
        Enabled: true
        text: "Plex Development"
        CustomIconURL: ""
      Timestamp: true
```

Each panel can be sent to different channels using the `/panel` command with the panel ID.

### Ticket Categories Configuration

Categories define the different types of tickets users can create. They're configured in the `TicketCategories` section:

```yaml
TicketCategories:
  TicketCategory1:  # This is the category ID (must be unique)
    CategoryName: "Example 1" # This will be the button and ticket name/category
    Description: "" # Category description, This only works if SelectMenu is enabled, Leave blank to disable
    ParentCategoryID: "731044694590750821"  # Discord category where tickets will be created
    EmbedTitle: "Support Ticket ({category})" # Use {category} to get the category name for the ticket opened
    EmbedMessage: "> Thank you for contacting support.\n> Please describe your issue and await a response." # Use {user} to get the user that created the ticket, {createdAt} to get when the ticket was created using a Discord timestamp
    CategoryEmoji: "" # Leave blank for no emoji
    ButtonColor: "Green" # Blurple, Gray, Green, Red
    SupportRoles: ["731044651078910012"] # Users with these roles can view tickets in this category, You can add multiple roles
    MentionSupportRoles: false # Mention all the Support Roles in new tickets?
    ChannelName: "ticket-{username}" # Variables: {total-tickets}, {username}, {user-id}
    LogsChannelID: "CHANNEL_ID" # Channel ID for category-specific logs (leave empty to use the default logs channel)
    RequiredRoles: [] # Require the user to have a specific role to open a ticket in this category? You can add multiple, leave blank to disable
    Questions: [] # Questions asked when creating a ticket in a modal
```

#### Adding More Categories

You can create unlimited categories, To add a new category, add a new entry under `TicketCategories`:

```yaml
TicketCategories:
  # Existing categories...
  
  TicketCategory4:
    CategoryName: "Feature Request"
    Description: "Suggest a new feature"
    ParentCategoryID: "731044694590750821"
    # Additional settings...
```

Once added, you can include the new category in any panel by adding its ID to the panel's `Categories` list.

### Adding Ticket Questions

Questions allow you to gather specific information when a user creates a ticket. Add questions to a category like this:

```yaml
Questions:
  - customId: "bugDescription"  # Unique identifier (no spaces)
    required: true  # Whether an answer is required
    minLength: 20  # Minimum character count (optional)
    question: "Describe the bug in detail"  # Question text
    placeholder: "Please provide as much information as possible"  # Placeholder text
    style: "Paragraph"  # "Paragraph" for long text, "Short" for single line
    
  - customId: "productVersion"
    required: true
    minLength: 2
    question: "Which version of the product?"
    placeholder: "1.0.0"
    style: "Short"
```

**Important Notes:**

* You can add up to 5 questions per category (Discord limitation)
* Each `customId` must be unique and contain no spaces
* Valid styles are "Paragraph" or "Short"

### Working Hours Placeholders

If you have working hours enabled, you can display them in your panel descriptions using these placeholders:

```
{workingHours-startTime-Monday} {workingHours-endTime-Monday}
{workingHours-startTime-Tuesday} {workingHours-endTime-Tuesday}
{workingHours-startTime-Wednesday} {workingHours-endTime-Wednesday}
{workingHours-startTime-Thursday} {workingHours-endTime-Thursday}
{workingHours-startTime-Friday} {workingHours-endTime-Friday}
{workingHours-startTime-Saturday} {workingHours-endTime-Saturday}
{workingHours-startTime-Sunday} {workingHours-endTime-Sunday}
```

Example usage:

```yaml
Description: "Our support team is available:\nMonday: {workingHours-startTime-Monday} - {workingHours-endTime-Monday}\nTuesday: {workingHours-startTime-Tuesday} - {workingHours-endTime-Tuesday}"
```

### Advanced Configuration Examples

#### Example: Support Panel with Multiple Categories

```yaml
TicketPanels:
  SupportPanel:
    Name: "Customer Support" 
    Categories: ["GeneralSupport", "TechnicalHelp", "BillingIssues"]
    Embed:
      Title: "Need Help?"
      Description: "Please select the appropriate category for your issue. Our team will respond as soon as possible.\n\n**Working Hours:**\nWeekdays: {workingHours-startTime-Monday} to {workingHours-endTime-Monday}"
      Color: "#3498db"
      PanelImage: "https://i.imgur.com/example.png"
      Timestamp: true
      Footer:
        Enabled: true
        text: "Response time: Usually within 24 hours"
```

#### Example: Application Form with Questions

```yaml
TicketCategories:
  StaffApplication:
    CategoryName: "Staff Application"
    Description: "Apply to join our team"
    ParentCategoryID: "123456789012345678"
    EmbedTitle: "Staff Application ({category})"
    EmbedMessage: "> Thank you for applying to join our team.\n> Your application has been submitted and will be reviewed soon."
    CategoryEmoji: "👥"
    ButtonColor: "Blurple"
    SupportRoles: ["123456789012345678"]
    MentionSupportRoles: true
    ChannelName: "application-{username}"
    RequiredRoles: ["123456789012345678"]  # Member role required
    Questions:
      - customId: "experience"
        required: true
        minLength: 50
        question: "What relevant experience do you have?"
        placeholder: "Tell us about your background and skills"
        style: "Paragraph"
        
      - customId: "availability"
        required: true
        question: "What is your weekly availability?"
        placeholder: "Hours per week and timezone"
        style: "Short"
        
      - customId: "whyJoin"
        required: true
        minLength: 100
        question: "Why do you want to join our team?"
        placeholder: "What motivates you to apply for this position?"
        style: "Paragraph"
```

By configuring these elements, you can create a customized ticket system tailored to your server's needs. Remember to use the `/panel` command to send your panels to the appropriate channels after setting up your configuration.
