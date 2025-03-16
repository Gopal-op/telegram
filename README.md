# Grammy.js Telegram Bot Template with Bun.js

This project provides a robust template for building Telegram bots using Grammy.js and Bun.js with TypeScript support. It offers a structured architecture with conversation management, action handling, and command processing capabilities out of the box.

The template implements a modular design pattern that separates concerns into conversations, actions, and commands. It features built-in support for emoji parsing, markdown formatting, and session management. The project uses Bun.js as the runtime environment for enhanced performance and modern JavaScript features, while leveraging Grammy.js's powerful bot framework capabilities.


### 💕Credit
- Coded By github.com/uo1428 

---
<div align="center">
  <p>Your One Click Can Help Other Users To Find This Repo Quickly: Leave a star ⭐<p>
</div>

---

## Repository Structure
```
.
├── config/
│   └── index.ts                 # Environment configuration management
├── src/
│   ├── Actions/                 # Callback query handlers for bot interactions
│   │   └── Main/
│   │       └── conversations.ts
│   ├── Commands/                # Bot command implementations
│   │   └── Main/
│   │       └── start.ts        # Implementation of /start command
│   ├── Conversations/           # Interactive conversation flows
│   │   └── Example/
│   │       └── new.ts
│   ├── Database/               # Database connectivity (placeholder)
│   │   └── index.ts
│   ├── utils/                  # Utility functions and helpers
│   │   ├── client/            # Bot client setup and loading utilities
│   │   ├── functions/         # Common helper functions
│   │   └── stuff/             # TypeScript type definitions
│   └── index.ts               # Main application entry point
├── package.json               # Project dependencies and scripts
└── tsconfig.json             # TypeScript configuration
```

## Usage Instructions
### Prerequisites
- Bun.js runtime environment
- Telegram Bot Token (from @BotFather)
- TypeScript 5.0.0 or higher

### Installation
1. Clone the repository:
```bash
git clone https://github.com/Uo1428/grammy-bunjs-telegram-bot.git
cd grammy-bunjs-telegram-bot-template
```

2. Install dependencies:
```bash
bun install
```

3. Configure environment variables:
Create a `.env` file in the root directory:
```env
BOT_TOKEN=your_telegram_bot_token
```

### Quick Start

1. Start the bot:
```bash
bun start
```

2. Test the bot by sending the `/start` command in Telegram.

### More Detailed Examples

1. Creating a new command:
```typescript
// src/Commands/Main/example.ts
export default {
  name: "example",
  description: "An example command",
  execute: async (ctx) => {
    await ctx.reply("This is an example command!");
  }
};
```

2. Creating a new conversation:
```typescript
// src/Conversations/Example/new.ts
export default {
  name: "example",
  execute: async (conversation, ctx) => {
    await ctx.reply("What is your name?");
    const response = await conversation.waitFor(":text");
    await ctx.reply(`Hello, ${response.msg.text}!`);
  }
};
```

### Troubleshooting

Common Issues:

1. Bot Token Invalid
```
Error: 401 Unauthorized
```
Solution: Verify your BOT_TOKEN in the .env file is correct and properly formatted.

2. Module Not Found Errors
```
Error: Cannot find module '@config/index'
```
Solution: Ensure all TypeScript path aliases in tsconfig.json are properly configured.

Debug Mode:
```typescript
// Enable debug logging
import consola from 'consola';
consola.level = 5;
```

## Data Flow
The bot processes messages through a pipeline of middleware and handlers, transforming raw updates into structured responses.

```ascii
Input → Parser → Middleware → Handler → Response
 ↑                   ↓           ↓
 └───────── Session Store ──────┘
```

Key component interactions:
- Client initialization loads commands, actions, and conversations dynamically
- Middleware processes updates sequentially (hydration, emoji parsing, session management)
- Commands are triggered by text messages starting with "/"
- Actions handle callback queries from inline keyboards
- Conversations manage multi-step interactions with state management
- Error handler catches and formats all runtime errors

## Discord Profile
<div align="center">
  <a width="100%" href="https://patreon.com/uoaio"  target="_blank">
    <img align="mid" height="100%" width="100%" style="margin: 0 10px 0 0;" alt=" " src="https://discord.c99.nl/widget/theme-2/922120042651451423.png">
  </a>
</div>