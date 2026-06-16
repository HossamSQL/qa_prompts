# QA Prompt Studio

[QA Prompt Studio](file:///d:/AI%20Tools/Hossam/prompt_generator/index.html) is a premium, fully client-side web application designed to accelerate quality assurance workflows. By acting as a bridge between raw testing notes and LLMs (such as Gemini, ChatGPT, or Qwen), it helps engineers compile raw testing facts into structured, developer-ready **Bug Reports** and multimodal **Test Case Specifications**.

---

## 🎨 Design & UX Highlights

*   **3D Interactive Experience:** Powered by **Three.js** to render a real-time particle constellation background and interactive 3D wireframe models.
*   **Mouse-Reactive Parallax & 3D Tilt:** Hovering over elements triggers responsive 3D card rotation and depth translation of text layers.
*   **Dual Themes:** Dark and light theme switcher with state persistence via `localStorage`.
*   **Frictionless Layout:** A single-screen glassmorphic workspace that adapts to varying viewport resolutions without unnecessary scrolling.
*   **Micro-Interactions:** Custom clipboard copy animations, visual toast alerts, and real-time character counters.

---

## 🛠️ Main Feature Modules

The studio consists of two primary prompt workspaces, accessible from the unified **Landing Hub**:

### 1. Bug Report Prompt Generator
Converts raw, unstructured feedback, log fragments, and reproduction steps into developer-friendly markdown bug tickets.
*   **Input Fields:** Bug Title, Preconditions, Steps to Reproduce, Expected Result, Actual Result, Attachments.
*   **Sample Data Loader:** One-click generation of a retail POS transaction mismatch example to demonstrate formatting capability.
*   **Output Structure:** Formulates a prompt instructing a **Senior QA Engineer** role to output the following standardized categories:
    *   🐛 **Bug Title**
    *   ⚙️ **Preconditions**
    *   👣 **Steps to Reproduce** (atomic numbered list)
    *   ✅ **Expected Result**
    *   ❌ **Actual Result**
    *   📎 **Attachments** (supporting files/evidence)

### 2. Test Case Prompt Generator
Drafts manual testing scripts, allowing QA teams to submit partial metadata and instruct multimodal AI to infer missing parameters directly from user interface screenshots.
*   **Input Fields:** Test Case ID, Scenario Type, Test Case Name, Targeted Table / Sheet Name, Priority, Preconditions, Steps to Execute, Expected Result, Screenshot References.
*   **Visual Inference Engine:** When fields are left blank, the generated prompt instructs the AI to analyze uploaded screenshot visual structures, states, and toast warnings to automatically deduce values.
*   **Traceable Suggestions:** All AI-inferred inputs are prefixed with `✨ [Suggested]` and backed by a required `💡 Suggestion Rationale` section at the end.

---

## ⌨️ Productivity Shortcuts

| Shortcut | Description |
| :--- | :--- |
| **`Ctrl + Enter`** / **`Cmd + Enter`** | Instantly compile and generate the structured prompt for the active workspace. |
| **Form Reset** | Quick-clear buttons to empty all active workspace inputs and reset state. |
| **Persistence** | Auto-saves input states to `localStorage` to prevent data loss on browser refresh. |

---

## 🚀 Getting Started

No compilation, local servers, or command-line installations are necessary to run the studio:

1.  Locate the [index.html](file:///d:/AI%20Tools/Hossam/prompt_generator/index.html) file.
2.  Open the file directly in any modern browser (Chrome, Edge, Firefox, or Safari) using the double-click gesture or dragging it into a browser tab.
3.  Alternatively, serve it locally using Python:
    ```bash
    python -m http.server 8080
    ```
    And navigate to `http://localhost:8080/index.html`.

---

## 📜 Compiled Prompt Architectures

### Bug Report Generation Prompt Template
When compiling a Bug Report prompt, the tool generates the following framework:
```markdown
# Role
Act as a Senior QA Engineer. Transform the supplied raw bug notes into a concise, developer-ready bug report while preserving every confirmed fact the reporter already provided.

# Source of Truth
The user inputs below are the source of truth. Do not overwrite or contradict any provided title, preconditions, steps, expected result, actual result, or attachment references...

# Input Data
- **Bug Title:** [User Input]
- **Preconditions:** [User Input]
- **Steps to Reproduce:** [User Input]
- **Expected Result:** [User Input]
- **Actual Result:** [User Input]
- **Attachments:** [User Input]

# Instructions
1. Preserve every provided fact and field meaning exactly as supplied.
2. Rewrite the content into cleaner QA language only where clarity improves...
```

### Test Case Generation Prompt Template
When compiling a Test Case prompt (designed for multimodal LLMs), it exports this template:
```markdown
# Role
Act as a Principal Software Quality Assurance Engineer. Analyze the attached user interface screenshot(s) and any provided metadata to generate or refine a production-ready manual QA test case.

# Source of Truth & Context
- **Primary Source:** The attached screenshots/evidence represent the actual user interface and system state.
- **Secondary Source:** The explicit metadata inputs listed below represent user constraints...

# Metadata Input Configuration
- **Test Case ID:** [User Input or NULL]
- **Scenario Type:** [User Input or NULL]
- **Test Case Name:** [User Input or NULL]
- **Targeted Table / Sheet Name:** [User Input or NULL]
- **Priority:** [User Input or NULL]
- **Preconditions:** [User Input or NULL]
- **Steps to Execute:** [User Input or NULL]
- **Expected Result:** [User Input or NULL]
```
