# Cheap-ai-api

A hosted OpenAI-compatible API for Google's Gemini and Gemma, Anthropic's Claude Opus and Sonnet, and OpenAI's GPT models.

## 🚀 API Access

### Free API Key
- **API Key:** `sk-LealjQcrXfljR48o38hklg`
- **Base URL:** `http://server2.api.nikkcocompany.store:4000/v1/chat/completions`
- Currently has access to **all models** (same as paid keys)
- ⚠️ **Free API keys can be deleted, edited, or changed at any time, any day — with or without notice.** They are not guaranteed to remain active or functional.
- ⚠️ Model availability for free keys may change at any time, with or without notice
- Updates will **always** be shared first in [Discord](https://discord.gg/F6mBjR8Jnt), and later posted on GitHub
- 👉 For reliable, uninterrupted access, consider upgrading to a **paid API key**.

👉 **Join the [Discord server](https://discord.gg/F6mBjR8Jnt)** to stay updated!

### Paid API Keys – Pricing

Contact us on [Discord](https://discord.gg/F6mBjR8Jnt) to purchase a paid API key.

👉 **[View models & pricing](http://server2.api.nikkcocompany.store:4000/ui/model_hub_table/)**

> Models with `:search` suffix enable automatic Google Search grounding.
> **Support `:search`:** all Gemini models, `gemma-4-26b-a4b-it`, `gemma-4-31b-it`

## Features

- 🤖 **OpenAI Compatible** – Use with any OpenAI SDK or tool
- 👁️ **Vision Support** – Process images with Gemini Vision models
- 🛠️ **Tool Calling** – Full function calling support
- 🌐 **Web Search** – Models with `:search` suffix enable automatic Google Search grounding
- 🔑 **Simple Auth** – Just use your API key

## Quick Start

### Using the API

Set your API key and base URL in your OpenAI SDK:

**Python:**
```python
from openai import OpenAI

client = OpenAI(
base_url="http://server2.api.nikkcocompany.store:4000/v1",
api_key="sk-LealjQcrXfljR48o38hklg"
)

response = client.chat.completions.create(
model="gemini-3.1-pro-preview",
messages=[{"role": "user", "content": "Hello!"}]
)
print(response.choices[0].message.content)
```

**JavaScript:**
```javascript
import OpenAI from 'openai';

const openai = new OpenAI({
baseURL: 'http://server2.api.nikkcocompany.store:4000/v1',
apiKey: 'sk-LealjQcrXfljR48o38hklg'
});

const completion = await openai.chat.completions.create({
model: 'gemini-3.1-pro-preview',
messages: [{ role: 'user', content: 'Hello!' }]
});
console.log(completion.choices[0].message.content);
```

**cURL:**
```bash
curl http://server2.api.nikkcocompany.store:4000/v1/chat/completions \
-H "Authorization: Bearer sk-LealjQcrXfljR48o38hklg" \
-H "Content-Type: application/json" \
-d '{
"model": "gemini-3.1-pro-preview",
"messages": [{"role": "user", "content": "Hello!"}]
}'
```

## API Usage

### Endpoints

| Endpoint | Description |
|----------|-------------|
| `GET /v1/models` | List all available models |
| `POST /v1/chat/completions` | Create a chat completion |

### Chat Completions

**Example with vision:**
```json
{
"model": "gemini-3.1-pro-preview",
"messages": [
{
"role": "user",
"content": [
{"type": "text", "text": "What's in this image?"},
{
"type": "image_url",
"image_url": {
"url": "data:image/jpeg;base64,/9j/4AAQSkZJRg..."
}
}
]
}
]
}
```

**Example with tool calling:**
```json
{
"model": "gemini-3.1-pro-preview",
"messages": [{"role": "user", "content": "What's the weather in London?"}],
"tools": [{
"type": "function",
"function": {
"name": "get_weather",
"parameters": {
"type": "object",
"properties": {
"location": {"type": "string"}
}
}
}
}]
}
```

**Example with web search:**
```json
{
"model": "gemini-3.1-pro-preview:search",
"messages": [{"role": "user", "content": "Latest news about AI"}]
}
```

### Response Format

Standard OpenAI chat completion response:
```json
{
"id": "chatcmpl-123",
"object": "chat.completion",
"created": 1677652288,
"choices": [{
"index": 0,
"message": {
"role": "assistant",
"content": "AI response here"
},
"finish_reason": "stop"
}],
"usage": {
"prompt_tokens": 10,
"completion_tokens": 20,
"total_tokens": 30
}
}
```




## Support

For issues or questions, updates join our [Discord server](https://discord.gg/F6mBjR8Jnt)
