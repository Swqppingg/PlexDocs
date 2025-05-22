# Plex Tickets: AI AutoResponse

The AI AutoResponse system uses AI to automatically respond to common user questions and support requests. Unlike traditional keyword-based systems, this AI-powered solution understands the **intent** and **context** of user messages, providing much more accurate and helpful responses.

### Overview

The system analyzes every message sent in your Discord server and determines if it matches any of your predefined responses. When a match is found with sufficient confidence, the bot automatically replies with the appropriate information, helping to reduce support workload while providing instant assistance to users.

#### Key Benefits

* Uses OpenAI's language models to understand intent, not just keywords
* Provides immediate help to users 24/7
* Handles common questions automatically, freeing up staff time
* Detailed statistics help optimize response effectiveness
* Built-in buttons to gauge response quality and improve the system

### How It Works

#### 1. Message Analysis

When a user sends a message, the AI AutoResponse system:

1. Ensures the system is enabled and the user/channel meets criteria
2. Skips analysis for users with support roles to avoid interfering with staff responses
3. Sends the message to OpenAI for intelligent analysis
4. Compares against your configured response triggers
5. Only responds if confidence level meets the threshold

#### 2. AI Intelligence

The system uses a sophisticated prompt that instructs the AI to:

* Understand the **context** and **intent** of messages
* Identify the user's actual need or question
* Match against available response categories
* Provide a confidence score (0.0 to 1.0)
* Explain the reasoning behind the match

#### 3. Response Delivery

When a match is found:

* The bot replies with the configured message (text or embed format)
* Feedback buttons are added for user input
* The interaction is logged to the database
* Analytics data is updated in real-time

### Configuration

#### Basic Settings

```yaml
AIAutoResponse:
  Enabled: true # Enable/disable the entire system
  OnlyInTickets: false # Restrict to ticket channels only
  OpenAIAPIKey: "your_api_key_here" # Required OpenAI API key
  Model: "gpt-3.5-turbo" # AI model to use (gpt-3.5-turbo or gpt-4)
  ConfidenceThreshold: 0.7 # Minimum confidence to trigger response (0.0-1.0)
```

#### Response Configuration

Each response is defined with the following structure:

```yaml
Responses:
  response_key_name:
    Triggers: ["keyword1", "keyword2", "phrase"] # Help AI understand what to match
    Message: "Your response message here" # What the bot will say
    Type: "EMBED" # Response format: "EMBED" or "TEXT"
    Color: "#FF5D5D" # Embed color (only for EMBED type)
```

**Response Types**

**EMBED Format:**

* Professional appearance with title, description, and footer
* Customizable colors and styling
* Best for important information or detailed responses

**TEXT Format:**

* Simple text message
* Faster and more casual
* Best for quick answers or brief information

#### Understanding Triggers

The `Triggers` array helps guide the AI's understanding but **does not work like traditional keywords**. Instead:

* **Context Clues**: Triggers help the AI understand what topics this response covers
* **Intent Matching**: The AI looks for the underlying intent, not exact word matches
* **Flexible Matching**: Users can phrase questions differently and still get matched

**Example: Server Connection Response**

```yaml
server_connection:
  Triggers: ["server IP", "how to connect", "server address", "join server", "connection"]
  Message: "Our server IP is **play.example.com**. You can connect using any Minecraft client!"
  Type: "EMBED"
  Color: "#00FF00"
```

**This will match messages like:**

* "what's the server ip?"
* "how do i connect to your minecraft server?"
* "can't join the server, what's the address?"
* "server connection info please"
* "where do I play minecraft?"

**But won't match unrelated messages like:**

* "what's the weather today?"
* "how are you doing?"
* "random conversation"

#### Button Settings

```yaml
ButtonSettings:
  Enabled: true # Show feedback buttons
  HelpfulButton: "👍 This helped!" # Positive feedback button text
  NotHelpfulButton: "👎 Still need help" # Negative feedback button text
  ButtonTimeout: 300 # How long buttons stay active (seconds)
```

#### Analytics Configuration

```yaml
Statistics:
  Enabled: true # Track response statistics
  LogsChannelID: "CHANNEL_ID" # Channel for logging AI activity

Analytics:
  TrackUsage: true # Track which responses are used most
  TrackAccuracy: true # Track user feedback quality
  TrackUserSatisfaction: true # Overall satisfaction metrics
  MonthlyReports: true # Generate monthly reports
```

### Best Practices

#### Writing Effective Triggers

1. **Be Descriptive**: Include various ways users might ask about the topic
2. **Think Like Users**: Consider different phrasings and terminology
3. **Include Problems**: Add trigger phrases for issues users might have
4. **Avoid Overlap**: Make sure different responses have distinct trigger contexts

**Good Example:**

```yaml
password_reset:
  Triggers: ["password reset", "forgot password", "can't login", "account recovery", "lost password", "login issues"]
```

**Poor Example:**

```yaml
password_reset:
  Triggers: ["password"] # Too vague, might match unrelated messages
```



#### Setting Confidence Thresholds

* **0.9 - 1.0**: Extremely strict, only exact matches
* **0.7 - 0.9**: Recommended range, good balance of accuracy and coverage
* **0.5 - 0.7**: More lenient, may catch more questions but risk false positives
* **Below 0.5**: Too loose, likely to cause incorrect responses

### Command Usage

#### `/ai-analytics overview`

View overall system performance:

* Total responses sent
* Monthly statistics
* User feedback summary
* Success rates

#### `/ai-analytics responses`

Analyze individual response performance:

* Usage frequency for each response
* Average confidence scores
* User satisfaction rates
* Most/least effective responses

#### `/ai-analytics accuracy`

Review system accuracy:

* Helpful vs not helpful feedback breakdown
* Confidence correlation with user satisfaction
* Areas needing improvement

#### `/ai-analytics monthly [month] [year]`

Generate monthly reports:

* Historical performance data
* Trend analysis
* Response effectiveness over time

### Troubleshooting

#### Common Issues

**AI Not Responding to Questions:**

1. Check if `ConfidenceThreshold` is too high
2. Verify OpenAI API key is valid
3. Ensure user isn't staff (staff messages are ignored)
4. Check if `OnlyInTickets` is enabled when testing outside tickets

**Too Many False Positives:**

1. Increase `ConfidenceThreshold` value
2. Review and refine trigger keywords
3. Make response contexts more specific
4. Check for overlapping response topics

**Low User Satisfaction:**

1. Review response messages for clarity
2. Check if responses actually answer the questions
3. Consider adding more specific responses for common issues
4. Update outdated information in responses

####

The new system should be significantly more accurate and useful than the old keyword matching approach.
