# 0xAI

Minecraft Fabric mod (1.21.11) that adds AI chat via Ollama. Type `@ai` in chat to ask questions.

## Requirements

- Minecraft 1.21.11
- Fabric Loader 0.18.4+
- Fabric API
- Fabric Language Kotlin
- Ollama running locally

## Install

1. Put the mod JAR in your `mods` folder
2. Run Ollama:
   ```
   ollama pull llama3.2
   ollama serve
   ```
3. Launch Minecraft

## Usage

In chat:
```
@ai how do i find diamonds
@ai what's the best food
@ai how to make a nether portal
```

## Config

Edit `config/oxai.json`:

```json
{
  "enabled": true,
  "trigger": "@ai",
  "ollamaUrl": "http://localhost:11434",
  "model": "llama3.2",
  "systemPrompt": "You are a helpful AI assistant in Minecraft.",
  "maxTokens": 150,
  "temperature": 0.7,
  "responsePrefix": "[AI] ",
  "maxMessageLength": 256,
  "showErrors": true,
  "requestTimeout": 30000,
  "contextMessages": 5
}
```

| Option | What it does |
|--------|--------------|
| enabled | Turn mod on/off |
| trigger | Text to trigger AI (default: @ai) |
| ollamaUrl | Ollama server address |
| model | Which model to use |
| maxTokens | Max response length |
| temperature | How creative the AI is (0-1) |
| responsePrefix | Text before AI messages |
| maxMessageLength | Max characters per chat line |
| showErrors | Show errors in chat |
| requestTimeout | Timeout in ms |
| contextMessages | How many past messages to remember |

## Models

Works with any Ollama model. Common ones:

- llama3.2
- llama3.2:1b (faster, uses less memory)
- mistral
- phi3

## Build

```
git clone <repo>
cd oxai
./gradlew build
```

JAR ends up in `build/libs/`.

## Troubleshooting

**Mod doesn't respond:**
- Check Ollama is running: `ollama serve`
- Check model is installed: `ollama list`
- Verify config file

**Slow:**
- Use smaller model (llama3.2:1b)
- Lower maxTokens
- Lower contextMessages

**Connection refused:**
- Check ollamaUrl in config
- Make sure Ollama is running on correct port
