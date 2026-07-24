# AI Governance & Cyber Risk Framework Navigator 🛡️🤖

A beginner-friendly, client-side web application designed to help technology teams, risk officers, and compliance engineers navigate the complex landscape of AI governance and cybersecurity frameworks. By entering a technology concern or risk description, users receive real-time, weighted alignment recommendations pointing them toward relevant standards.

## 🌟 Key Features

*   **Concern-Based Mapping**: Describe any tech-risk or compliance issue in plain English to see which framework applies.
*   **Transparent Scoring**: Fully audit-friendly, deterministic scoring using keyword weights rather than an opaque AI model.
*   **Zero-Server Architecture**: Runs entirely locally in the browser. Submissions are processed locally, ensuring privacy and preventing data leaks.
*   **Light/Dark Themes**: Sleek, modern responsive interface designed for readability.
*   **Framework Blueprints**: Quick control checklists and official website links for four premier industry standards:
    *   NIST Artificial Intelligence Risk Management Framework (AI RMF 1.0)
    *   NIST Cybersecurity Framework (CSF 2.0)
    *   NIST Privacy Framework 1.0
    *   ISO/IEC 42001:2023 (Artificial Intelligence Management System)

---

## 📂 Repository Directory Structure

The project is structured logically to keep data separate from user interface controls, making it easy to review and modify:

*   [**index.html**](file:///C:/Users/trini/.gemini/antigravity/scratch/ai-governance-cyber-risk-toolkit/index.html): The landing portal and layout structure of the application.
*   [**src/mappings/**](file:///C:/Users/trini/.gemini/antigravity/scratch/ai-governance-cyber-risk-toolkit/src/mappings/): Curated datasets and weights mapped separately for review and updates.
    *   `nist_ai_rmf.js`, `nist_csf.js`, `nist_privacy.js`, `iso_42001.js`
*   [**src/scoring.js**](file:///C:/Users/trini/.gemini/antigravity/scratch/ai-governance-cyber-risk-toolkit/src/scoring.js): Core keyword scanner and math formula calculations.
*   [**src/main.js**](file:///C:/Users/trini/.gemini/antigravity/scratch/ai-governance-cyber-risk-toolkit/src/main.js): User interface controller managing themes, examples, button clicks, and expansion toggles.
*   [**src/index.css**](file:///C:/Users/trini/.gemini/antigravity/scratch/ai-governance-cyber-risk-toolkit/src/index.css): Custom CSS styles and variables defining light/dark themes and responsive grids.
*   [**tests/**](file:///C:/Users/trini/.gemini/antigravity/scratch/ai-governance-cyber-risk-toolkit/tests/): Test suite verifying scoring arithmetic. Contains:
    *   `scoring.test.js`: Assertions verifying the scoring logic.
    *   `run_tests.html`: Visual test runner displaying results in any browser.

---

## 🚀 Setup & Usage Instructions

As a zero-install static application, running this project is extremely simple and requires no software compilation:

### Option A: Local File Double-Click (Absolute Easiest)
1. Clone or download the repository.
2. Navigate to the root directory `ai-governance-cyber-risk-toolkit/`.
3. Double-click [**index.html**](file:///C:/Users/trini/.gemini/antigravity/scratch/ai-governance-cyber-risk-toolkit/index.html) to open the application in any modern web browser (Chrome, Edge, Firefox, Safari).

### Option B: Local Web Server (Recommended for Development)
If you want to run it via a local web server (to test code changes or simulate a production environment):
*   **Using Python** (if installed):
    ```bash
    python -m http.server 8000
    ```
    Then open [http://localhost:8000](http://localhost:8000) in your browser.
*   **Using VS Code "Live Server" Extension**:
    Right-click `index.html` and select **"Open with Live Server"**.

---

## 🔢 Scoring Methodology

To ensure transparency, reproducibility, and compliance with data privacy, we do not send user input to external AI APIs. The scoring is fully client-side and deterministic:

1.  **Risk Theme Identification**: The application scans the user's input text for pre-defined keyword lists mapping to **10 Core Risk Themes** (Cybersecurity, Privacy, AI Bias, Transparency, Accountability, Data Quality, Third-Party Risk, Human Oversight, Incident Response, and Regulatory Risk).
2.  **Binary Matching**: If a keyword for a theme matches, that theme is marked as **Active (Value: 1)**; otherwise, it is **Inactive (Value: 0)**.
3.  **Weighted Average**: For each framework, we look at the weights assigned to the **Active Themes** (weights range from `0.0` to `1.0` representing how strongly a framework covers that specific topic).
4.  **relevance score Formula**:
    $$\text{Relevance Score} = \left( \frac{\sum \text{Weights of Active Themes}}{\text{Total Number of Active Themes}} \right) \times 100\%$$
5.  **Relevance Categorization**:
    *   **High Relevance**: $\ge 70\%$
    *   **Moderate Relevance**: $40\% \le \text{Score} < 70\%$
    *   **Low Relevance**: $< 40\%$

---

## ⚠️ Limitations & Disclaimers

### Technical Limitations
*   **Keyword Sensitivity**: Because this version uses direct keyword substring matching, it does not analyze context or semantics (e.g., matching "unfair" might not trigger "bias" unless added to the mappings). We mitigated this by defining comprehensive keyword banks.
*   **Static Dataset**: Framework mappings and weight metrics are static files in `src/mappings/` and must be updated manually as standards evolve.

### Legal Disclaimers
*   **Informational Only**: The Navigator is an educational tool meant to suggest starting points for risk assessments. 
*   **No Compliance Guarantee**: A high relevance score does **not** signify that your organization is compliant. It only indicates that your concern is highly aligned with the topics covered in that framework.
*   **Not Legal Advice**: Do not make final compliance, legal, or technology deployments based solely on this tool. Consult certified auditors and legal counsel for official compliance assessments.
*   **ISO Copyright Compliance**: This tool does not reproduce copyrighted ISO standard text. Only public summaries and high-level control references are used, with links to official sources.

---

## 📝 Licensing

This software is licensed under the **MIT License**. You are free to copy, modify, distribute, and run this code commercially, provided you include the original copyright and license notice. See the [LICENSE](./LICENSE) file for the full text.
