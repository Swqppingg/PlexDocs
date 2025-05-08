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
    TicketName: "General Support"  # Display name
    Description: "General support questions"  # Short description (shown in select menus)
    TicketCategoryID: "731044694590750821"  # Discord category ID where tickets will be created
    TicketMessageTitle: "Support Ticket ({category})"  # Title of the message in new tickets
    TicketMessage: "> Thank you for contacting support.\n> Please describe your issue and await a response."  # Message content
    ButtonEmoji: "🔧"  # Emoji displayed on the button
    ButtonColor: "Green"  # Button color (Green, Red, Blurple, Gray)
    SupportRoles: ["731044651078910012"]  # Role IDs that can access these tickets
    MentionSupportRoles: false  # Whether to mention support roles when ticket is created
    ChannelName: "ticket-{username}"  # Naming pattern for ticket channels
    RequiredRoles: []  # Roles required to create this type of ticket (empty = anyone)
    Questions: []  # Form questions (explained below)
```

#### Adding More Categories

You can create unlimited categories, To add a new category, add a new entry under `TicketCategories`:

```yaml
TicketCategories:
  # Existing categories...
  
  TicketCategory4:
    TicketName: "Feature Request"
    Description: "Suggest a new feature"
    TicketCategoryID: "731044694590750821"
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
    TicketName: "Staff Application"
    Description: "Apply to join our team"
    TicketCategoryID: "123456789012345678"
    TicketMessageTitle: "Staff Application ({category})"
    TicketMessage: "> Thank you for applying to join our team.\n> Your application has been submitted and will be reviewed soon."
    ButtonEmoji: "👥"
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
