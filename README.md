# OpenCallFlow 📞

OpenCallFlow is a lightweight, zero-dependency, browser-based call flow assistant designed specifically for inbound sales and customer service teams. It provides agents with instant access to dynamic scripts, objection-handling "panic buttons," and live reference sheets—all without requiring a backend server or complex database setup.

---

## 🎓 Building Confident Agents

OpenCallFlow replaces rigid scripts with an interactive conversational blueprint. It keeps new hires on track and helps experienced agents maintain a natural call flow.

### Key Benefits for Training:
* **Dynamic Conversational Flow:** Agents navigate logically through steps based on real-time customer responses.
* **On-the-Spot Coaching Tips:** Embed custom formatting, visual cues (e.g., `[DISCOVERY]`), and delivery reminders directly inside the script blocks for each step of the call.
* **Objection-Handling "Panic Buttons":** Keep rebuttals for common hurdles (like *"Price is too high"* or *"I have to talk to my husband/wife"*) permanently visible in the sidebar so agents never freeze.

### How to Create & Deploy Scripts:
1. **Design visually:** Open `manager.htm` in any browser to build your tree step-by-step. Start your script at `step_1`.
2. **Export the flow:** Go to the **JSON Export/Import** tab and click **Copy to Clipboard**.
3. **Use that JSON to update agent.html:** Either update the hard coded `appConfig` in the agent.html or send that JSON code to your agents. They can click **⚙️ Hotfix Config** in their agent sidebar, paste it, and click **Apply** to refresh their script instantly.
4. **Performance Reviews:** Have agents use the **📜 View Call History** button to review their exact conversational path and timestamps for self-coaching or QA sessions.

---

## 📈 Operational Agility & Performance

OpenCallFlow eliminates the operational bottlenecks of traditional script management, allowing your floor to pivot instantly to changing market conditions.

### Business & Operational Impact:
* **Accelerated Time-to-Competency:** New hires reach target KPIs faster by following a guided, reactive decision tree.
* **Instant Strategy Deployment:** Bypasses IT deployment queues. Supervisors can update scripts or promotional offers and push them to the floor mid-shift via the Hotfix injector.
* **Zero Software Overhead:** Requires no licensing fees, hosting infrastructure, or database maintenance costs.
* **Floor Auditing:** Tracks conversational branches and cycle times locally, giving you downloadable metrics to verify script adherence and analyze script bottlenecks.

---

## Security & Zero-Footprint

OpenCallFlow is a client-side utility built entirely with vanilla HTML5, CSS3, and JavaScript. It is designed with a strict privacy-first architecture.

### Security & Privacy Compliance Profile:
* **Data Isolation (Strictly Client-Side):** The application does not transmit data over the network. All state logic and scripting configurations are processed entirely within the user's browser session.
* **No PII Transmission:** OpenCallFlow does not capture, store, or process Personally Identifiable Information (PII). It tracks node paths and timestamps, decoupling customer identities from call flow metrics.
* **Zero Attack Surface:** With no backend API, servers, or cloud databases, this tool introduces zero external system vulnerabilities.
* **LocalStorage Persistence:** Operational metrics are saved locally to the browser's sandboxed `localStorage`. This data persists through page reloads but can be programmatically cleared or wiped via standard browser cache policies.

### Technical Specifications:
* **Stack:** Vanilla JS (ES6+), HTML5, CSS3. No external CDNs or third-party dependencies.
* **Deployment:** Can be run locally as flat files on agent machines or hosted statically on an internal secure web server (IIS/Apache) or GitHub Pages.
* **Permanent Configuration:** To lock down a script baseline across the enterprise, paste your generated JSON object directly into the `let appConfig = {...};` block inside the `agent.htm` source file.

---

## 🌐 Live Demos & Setup

Test the tools directly in your browser (no installation required):
* **Agent Interface Demo:** [Test the live Agent view here](https://fortepc.github.io/OpenCallFlow/agent.html)
* **Manager Configurator Demo:** [Test the live Manager view here](https://fortepc.github.io/OpenCallFlow/manager.htm)
