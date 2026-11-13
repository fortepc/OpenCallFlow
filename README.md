# OpenCallFlow 📞

OpenCallFlow is a lightweight, zero-dependency, browser-based call flow assistant designed specifically for inbound sales and customer service teams. It provides agents with instant access to dynamic scripts, objection-handling "panic buttons," and live reference sheets—all without requiring a backend server or complex database setup.

## Version 1.0.0

This release provides two self-contained offline-capable tools: a visual flow configurator and an agent assistant. It includes a unified searchable response/reference list, validated schema-versioned JSON configuration, editable light/dark palettes, and local history with JSON import/export.

The bundled agent flow is illustrative sample content. Review and replace all scripts, prices, refund terms, security instructions, and other policies with organization-approved material before operational use.

---

## 🎓 Building Confident Agents

OpenCallFlow replaces rigid scripts with an interactive conversational blueprint. It keeps new hires on track and helps experienced agents maintain a natural call flow.

### Key Benefits for Training:
* **Dynamic Conversational Flow:** Agents navigate logically through steps based on real-time customer responses.
* **On-the-Spot Coaching Tips:** Embed custom formatting, visual cues (e.g., `[DISCOVERY]`), and delivery reminders directly inside the script blocks for each step of the call.
* **Objection-Handling "Panic Buttons":** Keep rebuttals for common hurdles (like *"Price is too high"* or *"I have to talk to my husband/wife"*) permanently visible in the sidebar so agents never freeze.

### How to Create & Deploy Scripts:
1. **Design the flow:** Open `manager.htm` in a browser and select **Flow Canvas**. Start at `step_1`, use **Auto arrange** to lay out larger flows, or drag node headers to position them manually. The dashed work-area boundary expands as nodes are moved outward. The **Reset flow** terminal is a normal movable node. Connections route around other nodes where possible. Connect a button output to a step input to set that response's destination. Select a node to edit its script, alerts, and ordered response buttons.
2. **Export the flow:** Open **JSON Import/Export** and copy the configuration. The optional `canvas` property preserves node positions; the agent ignores it and continues to use the existing step and button fields.
3. **Update the agent:** Use the agent’s **Import Config JSON** control, paste the JSON through **⚙️ Hotfix Config**, or edit the embedded `appConfig` for a managed baseline.
4. **Performance Reviews:** Have agents use the **📜 View Call History** button to review their exact conversational path and timestamps for self-coaching or QA sessions.

## Configuration, Appearance & Styles

The current configuration format is schema version `2`. Panic responses and reference material share the searchable `panicButtons` collection; each item uses `type: "response"` or `type: "reference"`. The former separate `referenceLinks` format is no longer accepted.

Step scripts, alerts, notes, and panic-button content support Markdown. Use `**bold**` or `__bold__`, `*italic*` or `_italic_`, `++underline++`, `~~strikethrough~~`, and `[link text](https://example.com)` for inline formatting. The renderer also supports headings, paragraphs, blockquotes, inline and fenced code, horizontal rules, ordered and unordered lists, and pipe tables. Raw HTML is not supported; use Markdown instead. For safety, links are limited to HTTP(S), email, telephone, and relative URLs.

```json
{
	"schemaVersion": 2,
	"panicButtons": [
		{ "id": "refunds", "type": "reference", "label": "Refund policy", "content": "Refunds are available within 14 days." },
		{ "id": "supervisor", "type": "response", "label": "Caller requests supervisor", "content": "I can connect you with a supervisor." }
	]
}
```

The manager’s **Appearance** tab provides paired light and dark palettes for the agent and manager interfaces. Presets include OpenCallFlow Blue, T-Mobile Magenta, Verizon Red, AT&T Sky Blue, Rich Purple, Forest Green, Amber Gold, and Monochrome. Every color token can be edited with a color picker or hex value; custom palettes are included in exported JSON. The agent’s mode switch remembers its choice locally when browser storage is available and otherwise uses the configured default.

Flow steps support these alert types:

| Alert type | Example | Use |
| --- | --- | --- |
| `warning` | `"alert_type": "warning"` | Caution or reminder |
| `stop` | `"alert_type": "stop"` | Required stop or escalation |
| `info` | `"alert_type": "info"` | Neutral guidance |
| `success` | `"alert_type": "success"` | Confirmation or successful outcome |

Response buttons support these styles:

| Button style | Appearance |
| --- | --- |
| `btn-primary` | Brand color, primary action |
| `btn-secondary` | Neutral secondary action |
| `btn-success` | Success color |
| `btn-danger` | Danger color |
| `btn-warning` | Warning color |
| `btn-outline` | Transparent with brand outline |

Example step fragment:

```json
{
	"alert_type": "info",
	"alert_text": "Confirm the preferred installation date.",
	"buttons": [
		{ "label": "Confirm", "target": "orderConfirmation", "style": "btn-success" },
		{ "label": "Review options", "target": "handleObjections", "style": "btn-outline" }
	]
}
```

---

## Operational Features

* **Guided call flows:** Agents navigate configured steps and responses based on the conversation.
* **Editable references:** Keep response scripts and reference material searchable from one sidebar.
* **Local history:** Review and export recorded flow paths and timestamps from the current browser profile.
* **Portable configuration:** Move manager-generated JSON to agent copies without a service or database.

---

## Local Operation & Data Handling

OpenCallFlow is a client-side utility built entirely with vanilla HTML5, CSS3, and JavaScript. Each page is self-contained and can be opened locally without a server.

### Data Handling:
* **Local processing:** The HTML files contain no network requests or external runtime dependencies. Hosted demos require a network connection; local copies do not.
* **Data handling:** Call history records flow paths, configured labels, and timestamps. Custom scripts, references, or labels may contain sensitive information; do not include customer payment data or other unnecessary PII.
* **Browser storage:** Agent config, theme preference, and history use browser storage when available. Persistence for pages opened as local files varies by browser and profile. Use JSON config/history export for portable backups.

### Technical Specifications:
* **Stack:** Vanilla JS (ES6+), HTML5, CSS3. No external CDNs or third-party dependencies.
* **Deployment:** Both HTML files run locally as standalone files without a server. They can also be hosted statically on an internal web server or GitHub Pages.
* **Configuration:** To ship a managed baseline, paste the manager-generated schema-version 2 JSON object into the embedded `appConfig` in `agent.html`.

---

## 🌐 Live Demos & Setup

Test the tools directly in your browser (no installation required):
* **Agent Interface Demo:** [Test the live Agent view here](https://fortepc.github.io/OpenCallFlow/agent.html)
* **Manager Configurator Demo:** [Test the live Manager view here](https://fortepc.github.io/OpenCallFlow/manager.htm)
