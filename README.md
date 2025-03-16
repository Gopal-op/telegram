# Grammy.js Telegram Bot Template with Bun.js - A Modern TypeScript Bot Framework

This project provides a robust template for building Telegram bots using Grammy.js and Bun.js with TypeScript support. It offers a structured architecture with conversation management, action handling, and command processing capabilities out of the box.

The template implements a modular design pattern that separates concerns into conversations, actions, and commands. It features built-in support for emoji parsing, markdown formatting, and session management. The project uses Bun.js as the runtime environment for enhanced performance and modern JavaScript features, while leveraging Grammy.js's powerful bot framework capabilities.

## Repository Structure
```
.
├── config/                     # Configuration files and environment variables
│   └── index.ts               # Central configuration management
├── src/                       # Source code directory
│   ├── Actions/              # Bot action handlers
│   │   └── Main/            # Main action implementations
│   ├── Commands/            # Bot command definitions
│   │   └── Main/           # Core bot commands
│   ├── Conversations/       # Conversation flow definitions
│   │   └── Example/        # Example conversation implementations
│   ├── Database/           # Database connection and models (placeholder)
│   ├── utils/              # Utility functions and helpers
│   │   ├── client/        # Bot client utilities
│   │   ├── functions/     # Common helper functions
│   │   └── stuff/         # Type definitions
│   └── index.ts            # Application entry point
├── package.json            # Project dependencies and scripts
└── tsconfig.json          # TypeScript configuration
```

## Usage Instructions
### Prerequisites
- Bun.js runtime environment
- Telegram Bot Token (from @BotFather)
- TypeScript 5.0.0 or higher

### Installation
1. Clone the repository:
```bash
git clone <repository-url>
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
  description: "Example command",
  execute: async (ctx) => {
    await ctx.reply("This is an example command!");
  }
};
```

2. Creating a conversation:
```typescript
// src/Conversations/Example/new.ts
export default {
  name: "example",
  execute: async (conversation, ctx) => {
    await ctx.reply("What's your name?");
    const response = await conversation.wait();
    await ctx.reply(`Hello, ${response.message.text}!`);
  }
};
```

### Troubleshooting
Common issues and solutions:

1. Bot Token Issues
- Error: "Bot token is invalid"
- Solution: Verify your BOT_TOKEN in the .env file and ensure it matches the token from @BotFather

2. Module Resolution Issues
- Error: "Cannot find module"
- Solution: Check tsconfig.json path aliases and ensure all imports use the correct path format

Debug Mode:
```typescript
// Enable debug logging
import consola from 'consola';
consola.level = 5;
```

## Data Flow
The bot processes messages through a pipeline of middleware, handlers, and conversations.

```ascii
Input → Parser → Middleware → Handler → Response
 ↑                   ↓           ↓
 └───────── Session Store ──────┘
```

Component interactions:
1. Incoming messages are first processed by the Grammy.js core
2. Middleware chain handles parsing, hydration, and emoji processing
3. Session middleware maintains user state
4. Messages are routed to appropriate handlers (commands, actions, or conversations)
5. Responses are formatted with markdown and sent back to users