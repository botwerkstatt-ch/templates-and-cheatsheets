# Templates & Cheat-Sheets for the Botwerkstatt-Hackathon

## What you'll find here

- [What tools can I use / How do I use them?](#what-tools-can-i-use--how-do-i-use-them)
- [Overview of tool access offered](#overview-of-tool-access-offered)
- [Access to n8n](#access-to-n8n)
    - [How to Get Started](#how-to-get-started)
- [Access to ElevenLabs](#access-to-elevenlabs)
    - [How to Get Started](#how-to-get-started-1)
    - [Included: Agents Platform](#included-agents-platform)
    - [Included: Additional APIs](#included-additional-apis)
    - [Cheatsheet](#cheatsheet)
- [Apertus API access on Swisscom AI Platform](#apertus-api-access-on-swisscom-ai-platform)
    - [1. Obtain your personal API Key](#1-obtain-your-personal-api-key)
    - [2. Set up your API Key (recommended)](#2-set-up-your-api-key-recommended)
    - [3. Requesting your first answer from Apertus 70B](#3-requesting-your-first-answer-from-apertus-70b)
- [Hugging Face Enterprise incl. compute credits](#hugging-face-enterprise-incl-compute-credits)
    - [How to Get Started](#how-to-get-started-2)
- [Access to Supertext](#access-to-supertext)
    - [How to Get Started](#how-to-get-started-3)
    - [Disclaimer / exclusion](#disclaimer--exclusion)


## What tools can I use / How do I use them?

The hackathon is tool and model agnostic: You choose what’s **best for you**.

In addition we want to **encourage everybody to try out [Apertus**, the Swiss LLM](https://huggingface.co/swiss-ai) and we supply you with additional API access as described on this page.

# **Overview of tool access offered**

- Free access to an n8n-Pro Account for the duration of 30 days
- **3 months Creator Plan access** from [ElevenLabs](https://elevenlabs.io/), with 750 minutes of conversations included.
- Access to Apertus-70B-Instruct-2509 via API hosted by Swisscom on their **Swiss AI Platform** using a private API key.
- Use Apertus (and other models) on **Hugging Face Enterprise** to execute tasks that need compute i.e. if you want to fine tune the model or if you only want to try it out.
- Free API access to the [Supertext](https://www.supertext.com/) API: **Automatically translate** text and files in 28 languages (including Swiss German and Romansh).

# Access to n8n

Build with the precision of code or the speed of drag-n-drop. [n8n](https://n8n.io/features/) gives you more freedom to implement multi-step AI agents and integrate apps than any other tool.

Every Team participating at BotWerkstatt can use **n8n Cloud Pro for free**.

**👉** [n8n Nods & Integrations](https://docs.n8n.io/integrations/) | [n8n Advanced AI Docs](https://docs.n8n.io/advanced-ai/)

### **How to Get Started**

- Register your team here: [https://app.n8n.cloud/register](https://app.n8n.cloud/register)
- Wait for Your Workspace to become ready
- From Your Instance click on “Upgrade Now”
    - Choose the “Pro”-Plan
    - Use the Voucher: BOTWERKSTATT-136A8911  
- Please DO NOT use mutiple Vouchers per person (50 vouchers available, use wisely)



# **Access to ElevenLabs**

The ElevenLabs Agents Platform allows you to **build voice-enabled AI agents** with real-time speech-to-text, LLM, and natural text-to-speech orchestration – powered by **industry-leading voice AI technology**. All participants receive **3 months of Creator Plan access** for the hackathon, with 750 minutes of conversations included.

**👉 [Agents Platform Quickstart](https://elevenlabs.io/docs/conversational-ai/quickstart) | [API Documentation](https://elevenlabs.io/docs/api-reference/agents/create)**

### **How to Get Started**

- Find your an access link for your Creator Plan access in your personal profile
    - Include your team name and project description
    - Each participant receives **3 months of Creator Plan** access
    - Access includes all Agents Platform features plus TTS and Music APIs
- Do NOT share access credentials across teams to prevent rate limiting issues
- Test your agent using our [Dashboard](https://elevenlabs.io/app/conversational-ai)

### **Included: Agents Platform**

- **Real-time Speech-to-Text** Low-latency voice recognition in 29+ languages
- **LLM Orchestration** Seamless integration with GPT-4, Claude, and custom models
- **Text-to-Speech** Natural voices with <500ms latency
- **WebSocket and WebRTC Support** For real-time bidirectional streaming
- **Knowledge Base** Equip agents with documents and external resources
- **Custom Tools** Extend agent capabilities with custom API integrations and MCP server support
- **Analytics Dashboard** Monitor conversations and agent performance

### **Included: Additional APIs**

- **V3 TTS Model**Latest text-to-speech model with enhanced quality ([TTS Models Docs](https://elevenlabs.io/docs/models))
- **Music Generation API** Create AI-generated music and sound effects ([Music API Quickstart](https://elevenlabs.io/docs/cookbooks/music/quickstart))

### Cheatsheet

- [AI Voice Agent Cheat Sheet by Deep Impact](https://github.com/botwerkstatt-ch/templates-and-cheatsheets/tree/main/ElevenLabs)

# **Apertus API access on Swisscom AI Platform**

In your hacker profile, you will find a key to access Apertus-70B-Instruct-2509 hosted by Swisscom on their **Swiss AI Platform**.

This guide will walk you through the basics of accessing and using our API to run inference with the new Apertus 70B model

### 1. Obtain your personal API Key

To get started, you'll need to have an API key. You can find your personal key in your ***hacker profile***.

With your API key, you can authenticate your requests to our API. There is a rate limit of 5 requests per second and 100,000 tokens per minute (tokens = input + output tokens). The HTTP response headers provide information about the status of available tokens:

- X-Ratelimit-Remaining-Tokens: The remaining number of tokens that are permitted before exhausting the rate limit.
- X-Ratelimit-Reset-Tokens: The time until the rate limit (based on tokens) resets to its initial state

### 2. Set up your API Key (recommended)

Configure your API key as an environment variable. This approach streamlines your API usage by eliminating the need to include the key in every request. Moreover, it enhances security by reducing the risk of accidental exposing your API key in your codebase.

For Linux or macOS, you can set the environment variable in your terminal session like this:

```
export SWISS_AI_PLATFORM_API_KEY=<your-api-key>
```

### 3. Requesting your first answer from Apertus 70B

Our API's are OpenAI API compatible, so you can query our models as you are used to with the OpenAI SDK.

Here's how to call a chat model using `curl`:

```
curl -X POST <https://api.swisscom.com/layer/swiss-ai-weeks/apertus-70b/v1/chat/completions> \\
-H "Authorization: Bearer $SWISS_AI_PLATFORM_API_KEY" \\
-H "Content-Type: application/json" \\
-d '{
  "model": "swiss-ai/Apertus-70B",
  "messages": [
    {"role": "user", "content": "Hello, how are you?"}
  ]
}'
```

Or, if you prefer Python, you can use the OpenAI Python SDK. First, install the SDK if you haven't already:

```
pip install openai
```

Then, you can use the following Python code to make a request:

```
import os
import openai

client = openai.OpenAI(
    api_key=os.getenv("SWISS_AI_PLATFORM_API_KEY"),
    base_url="<https://api.swisscom.com/layer/swiss-ai-weeks/apertus-70b/v1>"
)

stream = client.chat.completions.create(
    model="swiss-ai/Apertus-70B",
    messages=[
        {"role": "system", "content": "You are a travel agent. Be descriptive and helpful"},
        {"role": "user", "content": "What are the best places to visit in Switzerland?"}
    ],
    stream=True
)

for chunk in stream:
    print(chunk.choices[0].delta.content or "", end="", flush=True)

```

![🎉](https://fonts.gstatic.com/s/e/notoemoji/16.0/1f389/72.png)

**Congratulations** ! You have successfully made your first request to the Swiss AI Platform's Inference Endpoints!

# **Hugging Face Enterprise incl. compute credits**

We propose using Hugging Face to deploy Apertus 8B because it is almost as strong as 70B and it’s much easier to deploy.

### **How to Get Started**

- Join the following community on Hugging Face as early as possible: [huggingface.co/Swiss-AI-Weeks](https://huggingface.co/Swiss-AI-Weeks)
- Latest the day before the hackathon, you will be give compute grants

# **Access to Supertext**

The Supertext API allows you to **automatically translate** text and files in 28 languages (including Swiss German and Romansh) – exclusively on **secure Swiss servers**. It’s available for free for all participants of the Swiss AI Weeks.

**👉 [About the Supertext API](https://supertext.ubpages.com/api-swiss-ai-weeks/)   |   [API docs](https://www.supertext.com/en/documentation/swiss-ai-weeks)**

### **How to Get Started**

- Ask [nando@bosshart.sg](mailto:nando@bosshart.sg) for an API key for your team
    - The key is valid from the start until 24h after the event
- Do  use the same API key across multiple teams to prevent load trouble

  NOT

- If technical difficulties arise, follow these steps
    - Review your code and make sure it’s in line with the [API docs](https://www.supertext.com/en/documentation/swiss-ai-weeks)
    - Reach out to [hello@supertext.com](mailto:hello@supertext.com) which will be monitored during the hack (no response guaranteed)

### **Disclaimer / exclusion**

In it’s paid version, the Supertext API also offers near-instant Verification (getting translations reviewed by professional linguists). This service is NOT part of what we’re offering to the hack participants at the Swiss {ai} Weeks.
