# AI Edge Gallery: Privacy-First Productivity Skills

## Overview
Welcome to the Privacy-First Productivity Skills collection for the AI Edge Gallery. This repository contains practical, implementable skills for Gemma 4 Agent Mode on Android. Designed specifically for personal productivity and task automation, these capabilities run using on-device Large Language Models (LLMs) and offline-first execution paths (Text-Only, JavaScript Webviews, and Native Android Intents). 

Our primary architectural philosophy is maximum capability with zero telemetry: what happens on your device, stays on your device.

---

## Included Skills & Security Assessments

### 1. Send WhatsApp Message (`send-whatsapp`)
- **Execution:** Native (`run_intent`)
- **Data Safety Assessment:** Processes highly sensitive personal data, including contact phone numbers and private message content.
  - **Risk:** Potential exposure if prompt history is extracted or if the intent is maliciously intercepted.
  - **Mitigation:** The skill delegates execution entirely to the Android OS using native intents (`android.intent.action.SEND`). No networking APIs are invoked by the LLM or the Gallery App directly for this action.
- **Public Distribution Readiness:** Suitable. Requires the host app to correctly implement the intent handling in `IntentHandler.kt`.

### 2. Bill Splitter (`bill-splitter`)
- **Execution:** JavaScript (`run_js`)
- **Data Safety Assessment:** Processes personal financial data, including spending habits, locations, and dining companions.
  - **Risk:** Financial data modeling could be stored or logged.
  - **Mitigation:** 100% offline execution. Operates via a local JS webview (`index.html`) without calling the `fetch()` API or external CDNs.
- **Public Distribution Readiness:** Suitable. No privacy concerns as it relies entirely on local execution sandboxing.

### 3. Focus & Pomodoro Optimizer (`focus-optimizer`)
- **Execution:** Text-Only
- **Data Safety Assessment:** Processes user schedules, meeting names, and daily priorities.
  - **Risk:** Exposure of corporate or personal daily routines.
  - **Mitigation:** Because it is a text-only skill, data never bridges into an external runtime. The on-device LLM structures the response in real-time.
- **Public Distribution Readiness:** Suitable and highly safe for public distribution.

### 4. Secure Vault (`secure-vault`)
- **Execution:** JavaScript (`run_js`)
- **Data Safety Assessment:** Processes passwords, passkeys, and highly sensitive journal entries.
  - **Risk:** Storing unencrypted keys or decrypted payloads in persistent local storage.
  - **Mitigation:** Employs the `require-secret: true` framework feature, ensuring the master password is never passed through the LLM prompt. Uses the Web Crypto API (`crypto.subtle`) for local AES-GCM encryption before storing/displaying text.
- **Public Distribution Readiness:** Suitable. Reviewers should verify that `index.html` does not persist the master key anywhere within the WebView DOM or `localStorage`.

### 5. Flashcard Generator (`flashcard-generator`)
- **Execution:** JavaScript (`run_js`)
- **Data Safety Assessment:** Processes educational material, text excerpts, or proprietary study manuals.
  - **Risk:** Low risk, but copyright content could be processed.
  - **Mitigation:** Local rendering. The script parses the LLM output into offline HTML components without sending telemetry.
- **Public Distribution Readiness:** Suitable. Fully safe for public GitHub distribution.

### 6. Smart Alarm (`smart-alarm`)
- **Execution:** Native (`run_intent`)
- **Data Safety Assessment:** Processes daily habits, waking hours, and calendar rhythms.
  - **Risk:** Low. Timestamps are generated and delegated.
  - **Mitigation:** Passed directly to Android’s clock interface via `IntentHandler.kt`. No tracking of user geographic locations or habits.
- **Public Distribution Readiness:** Suitable (requires OS-level app compilation to support the custom intents).

### 7. Habit Kanban Board (`habit-tracker`)
- **Execution:** JavaScript (`run_js`)
- **Data Safety Assessment:** Processes continuous behavioral data, medical habits (e.g. "take vitamins"), and personal goals.
  - **Risk:** Persistent cross-session data tracking could leak behavior history if the device is compromised.
  - **Mitigation:** Uses the WebView's siloed `localStorage`. Android enforces strict isolation, meaning external apps cannot read this WebView's local storage.
- **Public Distribution Readiness:** Suitable.

---

## Instructions for Installing and Using Skills

You can load these skills into your AI Edge Gallery app via three primary methods:

### Method A: Import from Local File (Recommended for Privacy)
1. Download this repository to your Android device (e.g., to your `/Download` folder).
2. Open the Agent Skills use case in the app and navigate to the Skill Manager.
3. Tap **(+)** -> **Import local skill**.
4. Select the specific skill folder (e.g., `secure-vault`).

### Method B: Add from URL
1. Host the raw folders via GitHub Pages (with `.nojekyll` enabled) or Cloudflare Pages.
2. In the Skill Manager, tap **(+)** -> **Load skill from URL**.
3. Enter the URL pointing to the skill folder itself.

### Method C: Add from Community-Featured Skills
1. Tap **(+)** -> **Add skill from featured list**.
2. Select any officially merged skills directly from the app.

---

## Security and Privacy Practices

This collection is built strictly with an **offline-first** mandate. 
- **No Cloud Inference:** Prompts are processed using Gemma's on-device models. 
- **No Telemetry:** The JavaScript execution environments (`index.html`) within these skills do not feature tracking pixels, analytics, or remote logging.
- **Secret Handling:** We rely on the AI Edge Gallery's `require-secret: true` UI for API keys and passwords to ensure sensitive tokens are never echoed back into the LLM context window.

## Data Handling Guidelines

- All persistent storage relies on isolated WebView `localStorage` that respects Android application sandboxing.
- Skills are forbidden from initiating background network `fetch` calls unless explicitly requesting the user's permission for an explicit external public API.
- If a device is wiped, all data generated by these skills within the gallery app is completely wiped.

## How to Report Security Concerns

We take vulnerabilities—especially concerning prompt-injection or WebView escapes—very seriously. 
If you find a security vulnerability:
1. **Do not** open a public GitHub issue.
2. Please send a direct email to `security@example-edge-gallery.com` (replace with actual contact point).
3. We aim to verify and patch vulnerabilities within 48 hours.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details. You are free to fork, modify, and distribute these skills for personal or commercial productivity use.
