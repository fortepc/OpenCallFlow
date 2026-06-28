# OpenCallFlow 📞

OpenCallFlow is a lightweight, zero-dependency, browser-based call flow assistant designed specifically for inbound sales and customer service teams. 

Whether you are handling high-volume inbound sales campaigns for organizations like my employer that I wrote this for, or managing a specialized help desk, OpenCallFlow keeps your team on track. It provides agents with instant access to dynamic scripts, objection-handling "panic buttons," and live reference sheets—all without requiring a backend server or complex database setup.

## 🚀 Features

* **Zero-Dependency Runtime:** Runs entirely in the browser using vanilla HTML, CSS, and JavaScript. No Node.js, PHP, or databases required.
* **Visual Configurator (`manager.htm`):** A point-and-click interface to build complex decision trees, customize objection handling, and manage reference links.
* **Instant Hotfixing:** Supervisors or agents can push script updates live during a shift using the Hotfix JSON injector.
* **Local Call Logging:** Automatically logs call paths and timestamps to the browser's `localStorage` for end-of-day reporting and QA.
* **State Management:** Agents can navigate forward, hit dead-ends, overcome objections, and reset the flow cleanly for the next caller.

---

## 🌐 Live Demos

You can test the tools directly in your browser using GitHub Pages (no installation required):

* **Agent Interface Demo:** [Test the live Agent view here](https://fortepc.github.io/OpenCallFlow/agent.html)
* **Manager Configurator Demo:** [Test the live Manager view here](https://fortepc.github.io/OpenCallFlow/manager.html)
* 

---

## 🛠️ Generating Call Flows (`manager.htm`)

The `manager.htm` file is your control center. It allows you to build and export your call flow logic without writing a single line of code.

### Step-by-Step Flow Creation:
1. **Open the Configurator:** Double-click `manager.htm` to open it in any modern web browser.
2. **Global Settings:** Set your flow version and the date it was last updated so agents know they are using the right script.
3. **Panic Buttons & References:** Add quick-access objection rebuttals (e.g., "Price is too high", "Wants a supervisor") and reference tables (e.g., Pricing Tiers). These will appear in the Agent's left sidebar.
4. **Build Flow Steps:**
   * Navigate to the **Flow Steps** tab. 
   * *Important:* Your very first step must always have the ID `step_1`. 
   * Add a Title, an optional Badge (e.g., "DISCOVERY"), and the Agent Script. You can use standard HTML like `<strong>` or `<br>` for formatting.
   * **Buttons:** For each step, add buttons and assign a "Target" (the ID of the next step it connects to). To create an end-of-call reset, set the target to `[RESET FLOW]`.
5. **Export Your Flow:** Once your tree is built, navigate to the **JSON Export/Import** tab and click **Copy to Clipboard**. 

---

## ⚡ Updating the Agent Interface (`agent.htm`)

The `agent.htm` file is the live production environment for your floor. When script changes need to be made, you don't need to edit the source code directly. You can inject updates instantly using the Hotfix tool.

### How to apply a Hotfix:
1. Copy the JSON output from `manager.htm` (as detailed in step 5 above).
2. send that JSON output to agents
3. Agents open `agent.htm` in the browser.
4. In the bottom-left corner of the sidebar, click the **⚙️ Hotfix Config** button.
5. A box will appear. Delete the existing code in the text box, paste your newly generated JSON, and click **Apply**.
6. The interface will instantly rebuild itself with the new scripts, reference blocks, and panic buttons. 

*(Note: To make an update permanent across all agent machines permanently, open `agent.htm` in a code editor, locate the `let appConfig = {...};` variable at the top of the `<script>` tag, and replace the object with your new JSON).*

---

## 📊 Managing Call History

OpenCallFlow saves a log of the paths agents take during their calls. 
* Click **📜 View Call History** in the agent sidebar to see timestamps and decision branches.
* You can **Export JSON** to send end-of-day metrics to a supervisor.
* Call logs are stored safely in `localStorage`, meaning they persist even if the browser is closed.

---

## 🤝 Contributing

This project is maintained by FortePC (me). Feel free to fork this repository, submit pull requests, or open issues for feature requests and bug reports.
