# OxAI - Minecraft AI Chat Companion

A Fabric mod for Minecraft 1.21.11 that integrates Ollama AI into chat, allowing players to ask questions and get AI-generated responses.

## Features

- 🤖 **Ollama Integration**: Uses local Ollama server for AI responses
- 💬 **Chat Trigger**: Responds when someone types `@ai` in chat
- ⚙️ **Fully Configurable**: Extensive configuration options
- 📝 **Context Awareness**: Maintains conversation history
- 🔄 **Message Chunking**: Automatically splits long responses
- 🎯 **Client-Side**: Runs entirely on your client

## Requirements

- Minecraft 1.21.11
- Fabric Loader 0.18.4+
- Fabric API
- Fabric Language Kotlin
- [Ollama](https://ollama.ai/) installed and running locally

## Installation

1. Install Fabric Loader for Minecraft 1.21.1
2. Download and place the mod JAR in your `mods` folder
3. Install and run Ollama with your preferred model:
   ```bash
   ollama pull llama3.2
   ollama serve
   ```
4. Launch Minecraft

## Configuration

### 1. Config File
Edit `config/oxai.json` directly:

```json
{
  "enabled": true,
  "trigger": "@ai",
  "ollamaUrl": "http://localhost:11434",
  "model": "llama3.2",
  "systemPrompt": "You are a helpful AI assistant in a Minecraft server. Keep responses concise and friendly.",
  "maxTokens": 150,
  "temperature": 0.7,
  "responsePrefix": "[AI] ",
  "maxMessageLength": 256,
  "showErrors": true,
  "requestTimeout": 30000,
  "contextMessages": 5
}
```

### Configuration Options

- **enabled**: Enable/disable the mod
- **trigger**: Text that triggers AI responses (default: "@ai")
- **ollamaUrl**: URL of your Ollama server
- **model**: Ollama model to use (e.g., llama3.2, mistral, phi3)
- **systemPrompt**: System prompt that defines AI behavior
- **maxTokens**: Maximum tokens in AI response
- **temperature**: AI creativity (0.0 = focused, 1.0 = creative)
- **responsePrefix**: Prefix added to AI messages
- **maxMessageLength**: Maximum characters per chat message
- **showErrors**: Show error messages in chat
- **requestTimeout**: Request timeout in milliseconds
- **contextMessages**: Number of previous messages to remember

## Usage

1. Start Minecraft with the mod installed
2. In chat, type: `@ai What is the best way to find diamonds?`
3. The AI will respond with helpful information

### Examples

```
Player: @ai How do I make an iron golem?
[AI] To make an iron golem, place 4 iron blocks in a T shape and put a carved pumpkin on top!

Player: @ai What's the best food in Minecraft?
[AI] Golden carrots are considered the best food, providing excellent saturation and hunger restoration.
```

## Supported Models

Any Ollama model works, but recommended models:
- `llama3.2` - Fast and accurate
- `llama3.2:1b` - Very fast, good for quick responses
- `mistral` - Balanced performance
- `phi3` - Lightweight and fast

## Building from Source

```bash
git clone <repository>
cd oxai
./gradlew build
```

The built JAR will be in `build/libs/`

## Troubleshooting

**Mod doesn't respond:**
- Ensure Ollama is running: `ollama serve`
- Check if the model is installed: `ollama list`
- Verify the configuration file settings

**Responses are slow:**
- Use a smaller model (e.g., `llama3.2:1b`)
- Reduce `maxTokens` in config
- Reduce `contextMessages` to use less context

**"Connection refused" error:**
- Ensure Ollama is running on the correct port
- Check `ollamaUrl` in config matches your Ollama server

## License

MIT License

## Credits

Created by oxod
