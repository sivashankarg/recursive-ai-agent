# 🧠 Recursive AI Agent V6

A standalone, mobile-first recursive AI learning agent for **telecom, computer networking, cloud, troubleshooting, and interview preparation**.

> **Important:** This repository is completely separate from the portfolio repository. The portfolio is not modified by this project.

## Live site

https://sivashankarg.github.io/recursive-ai-agent/

If Safari shows an older version immediately after an update, use a private tab or append a cache-busting query such as `?v=6`. GitHub Pages deployments can take a few minutes to publish.

---

# What V6 is

V6 combines two separate agent pipelines:

### 💬 Direct Tutor

`Your question → previous memory → public research → AI model → direct answer → memory`

The direct-question pipeline is deliberately isolated from autonomous curriculum generation. Asking:

> Explain an S11 Create Session Request timeout.

should produce a troubleshooting answer, **not a random study plan**.

### 🧠 Autonomous Learning

`Goal → research → choose knowledge gap → teach → troubleshooting scenario → quiz → next gap → persistent memory`

The agent improves its **learning state, curriculum, knowledge memory and next actions**. It does not silently rewrite its own public source code.

---

# V6 features

## 🤖 Large-model / provider access

Cloud mode uses OpenRouter's model catalog.

V6 includes a curated starting list covering multiple providers, including:

- OpenRouter free router
- NVIDIA
- Google
- OpenAI
- Qwen
- MiniMax

The model selector can also call the OpenRouter model catalog API and load the **current catalog dynamically**, instead of depending entirely on a hard-coded list.

### Model size

The catalog may contain models ranging from small models to very large parameter-count models. The UI displays available parameter/context metadata when OpenRouter supplies it.

**Important:** parameter count is not the same thing as intelligence, speed, or quality. Large models can also be slower, more expensive, or unavailable on a free endpoint.

## 🆓 Free / $0 mode

The **Show free/$0 model endpoints only** option filters the live OpenRouter catalog to endpoints whose reported prompt and completion pricing are zero.

Free availability, rate limits, providers and model IDs can change. V6 therefore has a **Refresh live model catalog** button.

V6 also retains the automatic **OpenRouter Free Router** fallback when enabled.

## 🌐 Internet / research

V6 has multiple internet paths:

1. **Public research without an API key**
   - Uses Wikipedia's public API.
   - Available in direct Q&A and autonomous learning.
   - This is research/context, not a guarantee that every answer is authoritative.

2. **OpenRouter web search**
   - Optional in Cloud AI mode.
   - Intended for fresher web-grounded answers.
   - Web search is a separate service and may have different availability/cost from a free model endpoint.

## 🔑 No-API-key features

V6 can still do useful work without an OpenRouter key:

- Research planner
- Public Wikipedia research
- Persistent local learning memory
- Autonomous curriculum planning
- Local WebLLM AI when the browser/device supports WebGPU

For stronger cloud models, an OpenRouter API key is required.

## 💻 Local AI

V6 uses WebLLM for a small browser-local model when WebGPU is available.

No cloud API key is required.

Browser/device memory and WebGPU support limit how large a local model can practically be, especially on mobile devices.

---

# Telecom / Networking / Cloud curriculum

The default learning goal covers:

### Networking fundamentals
- OSI and TCP/IP
- Ethernet
- IPv4 / IPv6
- ARP
- VLANs
- Subnetting

### Switching / routing
- MAC learning
- STP
- Static routing
- OSPF
- BGP

### Service-provider / WAN
- MPLS
- VRF
- QoS
- NAT
- DNS
- DHCP

### Linux networking
- `ip`
- `ss`
- `ping`
- `traceroute`
- `tcpdump`
- sockets
- processes
- logs

### 4G LTE / EPC
- UE
- eNodeB
- MME
- SGW
- PGW / EPG
- HSS
- LTE interfaces
- Attach
- Authentication
- Default bearer
- GTP-C / GTP-U
- S11
- S5/S8
- EPC troubleshooting

### 5G
- gNB
- AMF
- SMF
- UPF
- NRF
- NSSF
- 4G → 5G evolution

### Cloud
- Virtualization
- Containers
- Networking
- IAM
- Storage
- Observability
- AWS
- OpenStack

### Troubleshooting / interview readiness
- Alarm → scope → evidence → isolate → fix → verify → prevent
- Logs
- Counters
- Packet captures
- Call flows
- Failure scenarios
- Commands
- Interview questions
- Incident communication

---

# Persistent memory

V6 stores learning records and chat history in the browser's `localStorage`.

Memory is device/browser-local.

It is **not** automatically uploaded to GitHub.

The UI supports:

- View recent learning memory
- Clear learning memory
- Export memory as JSON
- Remember OpenRouter settings locally

API keys are never hard-coded into the repository.

---

# V6 architecture

```
                         ┌────────────────────┐
                         │      USER          │
                         └─────────┬──────────┘
                                   │
                    ┌──────────────┴──────────────┐
                    │                             │
              💬 Direct Q&A                🧠 Learning
                    │                             │
                    ▼                             ▼
              Memory context                 Research
                    │                             │
                    ▼                             ▼
              Public research              Curriculum
                    │                             │
                    ▼                             ▼
              AI tutor                     Lesson + scenario
                    │                             │
                    ▼                             ▼
              Direct answer                 Quiz + next gap
                    │                             │
                    └──────────────┬──────────────┘
                                   ▼
                         🧠 Persistent memory
```

Cloud path:

```
Browser → OpenRouter → selected provider/model
                         │
                         └── optional web search
```

No-key research path:

```
Browser → public research API → deterministic research/planning
```

No-key local path:

```
Browser → WebGPU → WebLLM → local model
```

---

# Version history

## V1
Initial standalone recursive-agent site.

- Recursive goal iterations
- Wikipedia research
- Browser localStorage memory
- Stop / clear / export
- No API key stored in repository

## V2 / V3 development
Expanded the concept toward open-model/local execution and mobile browser use.

## V4
Major autonomous-learning upgrade.

- OpenRouter cloud AI
- Multiple model choices
- Optional web search
- WebLLM local mode
- Research-only mode
- Persistent curriculum memory
- Autonomous learning cycles
- Telecom/networking/cloud curriculum
- Troubleshooting exercises
- Quizzes
- Knowledge-gap progression

## V5
Major architecture correction.

- Added a real direct-question input
- Separated Direct Q&A from Autonomous Learning
- Direct questions became memory-aware
- Research is performed before cloud/local answers
- Troubleshooting-oriented tutor prompt
- Direct answers saved into memory
- Visible execution log
- V5 memory/chat storage separated from V4

## V6 — current
V5 rebuilt with the missing V4 capabilities restored and expanded.

- Multi-provider model catalog
- Google / OpenAI / NVIDIA / Qwen / MiniMax / OpenRouter support where available
- Dynamic OpenRouter model catalog refresh
- Free/$0 endpoint filter
- Large-model parameter/context metadata when supplied by provider
- OpenRouter Free Router fallback
- Optional live web search
- No-key public research
- No-key local WebLLM
- Direct Q&A remains isolated from autonomous learning
- Persistent learning + chat memory
- Exportable memory
- Full telecom/networking/cloud curriculum
- Updated documentation

---

# Privacy / security notes

- **Never commit an API key to GitHub.**
- The API key field is client-side.
- If "Remember API key" is enabled, the key is stored in this browser's localStorage.
- Anyone with access to that browser profile may potentially access locally stored data.
- Do not use a personal production secret if you are uncomfortable storing it in browser storage.
- This is a static client-side application; there is no private backend protecting the API key.
- Research requests go directly from the browser to the public research endpoint.
- Cloud AI requests go directly from the browser to OpenRouter.

---

# GitHub Pages setup

Repository:

`sivashankarg/recursive-ai-agent`

The site uses the top-level:

`index.html`

To configure Pages manually:

1. Open **Settings**
2. Open **Pages**
3. Under **Build and deployment**, choose **Deploy from a branch**
4. Select **main**
5. Select **/(root)**
6. Save

No Pages setting needs to be changed for ordinary code updates once this is configured.

---

# Known limitations

### Free cloud models
Free endpoints are controlled by providers and OpenRouter availability. Models, limits, rate limits and identifiers can change.

### Web search
Web search availability/cost is separate from whether a model endpoint is free.

### Local AI
WebLLM depends on browser WebGPU and device memory. Mobile Safari may not handle large local models reliably.

### Research quality
The no-key research path currently uses Wikipedia public search as a lightweight research source. It should not be treated as equivalent to authoritative 3GPP/RFC/vendor documentation.

### Self-learning
"Self-learning" means the agent recursively improves its learning plan and stored knowledge state. It does not autonomously modify and publish source code.

---

# Recommended workflow

### First-time setup
1. Open the live site.
2. Choose **Cloud AI** if you want a large model.
3. Enter your OpenRouter key directly into the page.
4. Keep **Show free/$0 model endpoints only** enabled if you want free endpoints.
5. Tap **Refresh live model catalog**.
6. Select a model.
7. Ask a direct technical question.

### For your telecom learning
Try:

> Explain LTE Attach from UE power-on to default bearer creation. Include every major interface and GTP message.

Then:

> Now give me an S11 Create Session Request timeout troubleshooting scenario.

Then:

> Quiz me without showing the answers until I respond.

Then start autonomous learning for multiple cycles.

---

# Roadmap

Possible future improvements:

- Official-source research connectors for 3GPP / IETF / AWS / OpenStack / Nokia / Ericsson
- Better source ranking and citations
- Streaming model output
- Conversation UI instead of one output panel
- More local models where device support permits
- Spaced-repetition scheduling
- Flashcards
- Progress analytics
- Packet-flow diagrams
- PCAP upload/analysis
- Interview simulation mode
- Provider health checks
- More robust model capability metadata

---

## Repository boundary

This project belongs only in:

`sivashankarg/recursive-ai-agent`

**Do not move this code into the portfolio repository.**
