# Autonomous Browser Control AI & Top 5 Agent Architectures 🌐🤖

A pure frontend, zero-build suite of client-side web applications demonstrating autonomous agent architectures powered by **WebLLM (WebGPU)** and **Groq LPUs**.

---

## 🏛️ Top 5 Reusable Agent Architecture Apps

Rather than building 30 disconnected chatbots, this suite prioritizes reusable agent architectures:

| Rank | Architecture | Live App | Why It's Interesting |
|:---:|:---|:---|:---|
| **1** | **Self-Improving Agent** | [`self_improving_agent.html`](self_improving_agent.html) | Tests whether agents can autonomously improve their own problem-solving via recursive trajectory reflection and heuristic mutation. |
| **2** | **Autonomous Knowledge Engineer** | [`autonomous_knowledge_engineer.html`](autonomous_knowledge_engineer.html) | Combines ontology, causal knowledge graphs (+/- loops), and multi-hop symbolic path traversal reasoning. |
| **3** | **Autonomous Software Company** | [`autonomous_software_company.html`](autonomous_software_company.html) | Tests complex 6-role multi-agent coordination (PM, Architect, Engineer, QA, Security, DevOps). |
| **4** | **Digital Twin Experiment Agent** | [`digital_twin_experiment_agent.html`](digital_twin_experiment_agent.html) | Connects reasoning models with numerical physics/system simulators to run Monte Carlo parameter sweeps before live actuation. |
| **5** | **Human Intelligence Exoskeleton** | [`human_intelligence_exoskeleton.html`](human_intelligence_exoskeleton.html) | Explores human-AI cognitive symbiosis: captures intentions, externalizes working memory, challenges assumptions, and compiles plans. |

---

## 🌟 Highlights

- **Pure HTML / Client-Side Architecture**: Single-file web application without Node.js, Webpack, Vite, or backend server requirements. Runs directly via `file://`, GitHub Pages, or any static host.
- **Dual Inference Engine**:
  - **Local On-Device GPU (WebLLM)**: Private, client-side inference powered by `@mlc-ai/web-llm` running directly inside WebGPU VRAM. Supports models like Qwen 2.5 0.5B, SmolLM2 135M, Llama 3.2 1B, and Llama 3.2 3B.
  - **Groq LPU (Ultra-Fast Cloud)**: Lightning-fast inference (300–800+ tokens/sec) powered by Groq LPUs (`Llama 3.3 70B Versatile`, `Llama 3.1 8B Instant`).
  - **Rule-Based Fallback**: Immediate UI interaction testing without waiting for model downloads or API keys.
- **Autonomous Agentic Loop**:
  - **DOM & Accessibility Tree Serialization**: Parses visible interactive elements, inputs, buttons, and links, assigning structured `data-agent-id` indexes.
  - **Structured Action Schema**: Outputs JSON action plans (`click`, `type`, `navigate`, `finish`).
  - **Visual AI Cursor**: Smoothly moves an animated cursor to target elements, applies pulsing highlight halos, and triggers realistic click ripples and keystroke sequences.
- **Interactive Sandbox Environments**:
  - **NovaMart E-Commerce**: Product cards, search bar, live slide-out shopping cart drawer, and checkout.
  - **TaskFlow SaaS Dashboard**: Sprint backlog, task creation bar, priority tagging, and completion toggles.
  - **GlobalAir Flight Booking**: Route selection, passenger counts, cabin class, and seat reservation.
  - **Enterprise 1-Click Bookmarklet (Zero Extension Required)**: Uses native `BroadcastChannel` to automate ANY live external website (Wikipedia, Amazon, Jira, internal portals) without installing browser extensions or requiring IT approval.
  - **Interactive Examples & Recipes Gallery**: 9 pre-built executable scenarios across E-Commerce, SaaS sprint management, flight booking, and **Autonomous Eval & Red-Teaming (adversarial edge case fuzzing against deterministic assertions)**.

---

## 🚀 Quick Start

### 1. Open the App
Simply open `index.html` or `browser_control_ai.html` in any modern web browser supporting WebGPU (Google Chrome, Microsoft Edge, Brave, Opera):

```bash
# On Windows
start index.html

# Or with python simple HTTP server
python -m http.server 8000
```

### 2. Choose Your AI Brain
- **WebLLM (WebGPU)**: Click **"Load Model into WebGPU"** to download and initialize the model directly into your GPU VRAM.
- **Groq LPU**: Enter your Groq API Key (saved securely only in your browser's `localStorage`) and pick a model like `Llama 3.3 70B Versatile`.

### 3. Issue Natural Language Directives
Type instructions in the directive box or click any demo chip:
- *"Search for headphones and add the top rated one to cart"*
- *"Open Cart and proceed to checkout"*
- *"Type 'Fix authentication token timeout' and click Add Task"*
- *"Book a flight from New York to Tokyo for 2 passengers"*

Click **"Run Autonomous Agent"** to watch the agent plan, target elements, and execute the workflow step-by-step.

---

## 🔌 Controlling Real External Websites

Modern browser security (CORS & `X-Frame-Options`) restricts iframes from clicking across origins. To automate any live website on the web:

1. In the app, switch the environment preset to **🔌 Connect Real Browser Tab**.
2. Open any external website (e.g., Google, Amazon, Jira, GitHub) in a separate tab.
3. Open DevTools Console (`F12` or `Ctrl+Shift+I`) and paste:
   ```javascript
   const bc = new BroadcastChannel('agent_nav_channel');
   bc.onmessage = (e) => {
     if (e.data.action === 'click') document.querySelector(e.data.selector)?.click();
     if (e.data.action === 'type') { 
       const el = document.querySelector(e.data.selector); 
       if (el) { el.value = e.data.text; el.dispatchEvent(new Event('input', {bubbles:true})); }
     }
   };
   console.log('✅ Connected to AgentNavigator!');
   ```
4. Actions triggered in AgentNavigator will broadcast to and execute directly in your live tab.

---

## 🛠️ Tech Stack

- **Runtime**: Vanilla HTML5, CSS3, ES Modules
- **Inference**: WebGPU, `@mlc-ai/web-llm`, Groq Cloud API
- **Inter-tab Communication**: Web BroadcastChannel API
- **Design System**: Responsive Dark Mode Cybernetic Deck with custom SVG animations

---

## 📄 License

MIT
