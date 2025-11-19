# Portfolio Repository (Sample)

![Security Scan](https://img.shields.io/badge/GGShield-No%20Secrets%20Found-brightgreen)

This repository demonstrates reproducible security hygiene for portfolio preparation. All files here are placeholders; actual content is not exposed.

---

## 📖 Overview

This project is a demonstration of how to automatically check for "secrets" (like passwords or API keys) in a codebase. It uses a tool called `ggshield` to prevent sensitive information from being accidentally shared.

The main goals are:
- **Automate security:** Automatically scan for secrets before they are committed and pushed to a shared repository.
- **Ensure transparency:** Provide a clear and reproducible security workflow.
- **Promote best practices:** Showcase a professional approach to security and code management.

---

## 🏛️ Architecture & Workflow Diagram

The following diagram illustrates the complete security workflow, from local development to the remote repository.

```mermaid
graph TD
    subgraph "Local Environment"
        A["Developer writes code"]
        B{"git commit"}
        C{"pre-commit hook (ggshield)"}
        D{"Secret found?"}
        E["Commit BLOCKED"]
        F["Commit successful"]

        A --> B
        B --> C
        C --> D
        D -- "Yes" --> E
        D -- "No" --> F
    end

    subgraph "Remote Environment (GitHub)"
        G["Developer pushes to GitHub"]
        H{"GitHub Actions (CI/CD)"}
        I{"ggshield scan"}
        J{"Secret found?"}
        K["Workflow FAILS"]
        L["Workflow succeeds"]

        G --> H
        H --> I
        I --> J
        J -- "Yes" --> K
        J -- "No" --> L
    end

    F --> G
```

This diagram shows the two layers of protection:
1.  **Local:** The `pre-commit` hook prevents secrets from ever entering your local repository history.
2.  **Remote:** GitHub Actions provides a second layer of defense, scanning all code that is pushed to the shared repository.

*Note: "Secret found?" refers to sensitive information such as API keys, passwords, tokens, or other credentials that should not be exposed in code.*

---


## 🎯 Purpose

This workflow ensures:

- ✅ Transparent and reproducible security practices
- ✅ Verification that no sensitive information is committed
- ✅ Audit-ready structure aligned with public sector trust requirements
- ✅ Educational reusability for reproducible DevOps and security training
- ✅ CI/CD-integrated validation for continuous assurance
- ✅ Local developer enforcement via pre-commit hooks

---

## 🌟 Strategic Value & Alignment

This project is more than a technical demonstration; it's a strategic implementation aligned with key principles of modern, responsible software development.

*   **Public Sector & Educational Trust:** The dual-scan architecture (local pre-commit + remote CI/CD) and transparent, reproducible configuration make this project's workflow highly reliable and audit-ready, meeting the stringent trust requirements of public sector institutions and providing a clear, valuable resource for educational settings.

*   **Cost-Effective & Accessible:** By leveraging the generous free tiers of industry-standard tools like GGShield and GitHub Actions, this project demonstrates a powerful security posture that is accessible even for projects with limited budgets, making it a prime example of strategic open-source and SaaS utilization.

*   **Alignment with "Institutional Response Engineering":** This project embodies the principles of building technology that is not only technically sound but also institutionally aware. It is reproducible, auditable, cost-effective, and well-documented, ensuring it can be reliably adopted, maintained, and trusted within an organizational context.

---

## ✨ Best Practices in Action

This project doesn't just state that it follows best practices; it demonstrates them. Here's how:

### 1. Defense in Depth
Security is applied in multiple layers to provide robust protection:
- **Layer 1 (Local):** The `pre-commit` hook acts as the first line of defense, preventing secrets from being committed on the developer's machine.
- **Layer 2 (Remote):** If a secret slips past the local checks, GitHub Actions provides a second layer of scanning on the remote repository, ensuring nothing is missed.

### 2. Shift-Left Security
By using `pre-commit` hooks, we "shift security to the left" in the development lifecycle. This means we catch potential issues at the earliest possible stage (during development) rather than later in production, which saves time and reduces risk.

### 3. Automation
All security scans are automated. This removes the potential for human error (e.g., forgetting to run a scan) and ensures that security checks are consistently applied for every change.

### 4. Reproducibility and Transparency
The entire security workflow is defined as code (`.pre-commit-config.yaml`, `.github/workflows/secret-scan.yml`). This makes the process:
- **Transparent:** Anyone can see exactly how the security checks are configured.
- **Reproducible:** Any developer can set up the exact same security workflow with minimal effort.

---

## Setup

This project uses `ggshield` and `pre-commit` to prevent secrets from being committed to the repository. The following steps will guide you through the setup process.

### 1. Python Virtual Environment

It is recommended to use a Python virtual environment to isolate the project's dependencies from your system. The `venv-ggshield` directory in this repository is a placeholder for this purpose.

To create and activate a virtual environment, run the following commands:

```bash
# Create a new virtual environment named "venv-ggshield"
python3 -m venv venv-ggshield

# Activate the virtual environment
# On Windows
venv-ggshield\Scripts\activate
# On macOS and Linux
source venv-ggshield/bin/activate
```

### 2. Install Dependencies

Once the virtual environment is activated, install the necessary tools using pip (Python's package installer):

```bash
# Install ggshield and pre-commit
pip install ggshield pre-commit
```

### 3. Install Pre-commit Hooks

Install the pre-commit hooks defined in `.pre-commit-config.yaml`. This will enable `ggshield` to run automatically before each commit.

```bash
# Install the pre-commit hooks
pre-commit install
```

---

## 🔒 Security & Reproducibility Workflow

This repository is validated through automated and reproducible steps:

1.  **Initial Setup:**
    -   Created sample files (`cv_sample.txt`, `coverletter_sample.txt`, `notes.txt`)
    -   Initialized Git repository using `git init`
    -   Staged and committed files with `git add .` and `git commit`

2.  **Local Scanning (Manual):**
    -   You can manually run a scan on the entire repository at any time:
        ```bash
        ggshield secret scan repo .
        ```
    -   Confirmed result: **No secrets have been found**

3.  **Automated Local Scanning (Pre-commit):**
    -   The pre-commit hook automatically scans any changes you try to commit.
    -   If a secret is detected, the commit is blocked, preventing it from being saved to your local repository.

    **Example of a successful commit:**

    Here is a screenshot showing the `ggshield` pre-commit hook successfully scanning for secrets before a commit.

    ![ggshield pre-commit hook in action](images/pre-commit-success.png)

4.  **Automated Remote Scanning (CI/CD):**
    -   The GitHub Actions workflow (`.github/workflows/secret-scan.yml`) automatically scans the code on every push and pull request to the remote repository on GitHub.
    -   A nightly scan is also scheduled for continuous monitoring.

### 5. GitHub Actions Setup for ggshield

To ensure `ggshield` can authenticate and scan your repository in GitHub Actions, you need to provide it with a GitGuardian API Key.

#### a. Obtain your GitGuardian API Key
1.  Log in to your GitGuardian dashboard.
2.  Navigate to **API** -> **Personal access tokens**.
3.  Generate a new Personal Access Token. Copy this token, as it will only be shown once.

#### b. Create a GitHub Repository Secret
1.  In your GitHub repository, go to **Settings** -> **Secrets and variables** -> **Actions**.
2.  Click on **New repository secret**.
3.  Set the **Name** to `GG_API_KEY`.
4.  Paste your GitGuardian API Key (obtained in step 'a') into the **Secret** field.
5.  Click **Add secret**.

#### c. Update GitHub Actions Workflow
Ensure your `.github/workflows/secret-scan.yml` file includes the `GITGUARDIAN_API_KEY` environment variable, referencing the secret you just created. The updated section should look like this:

```yaml
      - name: Run ggshield scan
        env:
          GITGUARDIAN_API_KEY: ${{ secrets.GG_API_KEY }}
        run: ggshield secret scan repo .
```

#### d. Trigger the Workflow
After making these changes and pushing the updated `secret-scan.yml` to your repository, trigger a new workflow run:
1.  **Push a new commit:** Make a small change to any file, commit, and push.
2.  **Manually from GitHub:** Go to your repository's **Actions** tab, select "Secret Scan" workflow, and click "Run workflow".

This setup ensures that `ggshield` can securely authenticate and perform secret scans within your CI/CD pipeline.

---

## 📝 Notes

- This repository is designed for demonstration and documentation purposes.
- File contents are intentionally minimal and non-sensitive.
- The workflow is portable across any Git-tracked project folder.
- GitHub Actions configuration is located in `.github/workflows/secret-scan.yml`
- Pre-commit configuration is located in `.pre-commit-config.yaml`

---

## 📎 Related Tools

- [ggshield](https://github.com/GitGuardian/ggshield) — A command-line tool for detecting secrets in source code.
- [GitHub Actions](https://docs.github.com/en/actions) — An automation platform for CI/CD (Continuous Integration/Continuous Deployment).
- [pre-commit](https://pre-commit.com/) — A framework for managing and maintaining multi-language pre-commit hooks.

---

## 🌐 API Connectivity Notes

- `ggshield` normally verifies scans via the GitGuardian API.
- If the API is unreachable due to network restrictions, you can use local scanning:
  ```bash
  ggshield secret scan path .
  ```

---

## ☁️ Cloud Environment Notes

This workflow has been tested in environments with restricted connectivity.

### Key points

- `ggshield` scans remain reproducible even when API calls are blocked.
- Local scanning ensures security validation without external dependencies.
- `.gitignore` prevents environment-specific artifacts from being committed.
- The workflow is portable across cloud environments (Google, Azure, AWS).

---

## 💡 Challenges & Learnings

This project, while a demonstration, mirrors real-world software development challenges. Here are some of the key learnings from building this security workflow.

### 1. Challenge: Environment Inconsistency
- **Problem:** Initial attempts to run setup commands failed because the necessary tools (like `docker` or `pip`) were not available in every environment. This is a classic "it works on my machine" problem, which is a major source of friction in team projects.
- **Solution:** We addressed this by creating very explicit setup instructions in the `README.md`. By guiding the user to create a Python virtual environment (`venv`) and install dependencies into it, we ensure a consistent and reproducible environment for anyone working on the project. This is a fundamental best practice for collaborative development.

### 2. Challenge: Communicating Complex Technical Concepts
- **Problem:** The initial documentation was technically accurate but difficult for a wider audience (including non-developers or new developers) to understand. The "why" behind the workflow was not clear.
- **Solution:** We iteratively improved the `README.md` to make it more accessible without sacrificing technical detail. We achieved this by:
    1.  Adding a high-level **"Overview"** to explain the project's purpose in simple terms.
    2.  Creating a **Mermaid diagram** to provide a clear visual map of the workflow.
    3.  Adding a **"Best Practices in Action"** section to explain the reasoning and benefits behind our technical choices.
    This process highlighted the importance of clear communication in technical documentation.

### 3. Challenge: Persistent "Invalid GitGuardian API Key" in CI/CD

- **Problem:** Despite correctly configuring the GitHub Actions workflow to pass the `GG_API_KEY` secret and repeatedly regenerating the GitGuardian Personal Access Token, the CI/CD pipeline consistently failed with "Invalid GitGuardian API key."
- **Solution & Learning:** The root cause was a subtle but critical misunderstanding:
    -   **Token ID vs. Token String:** The user was mistakenly copying the *ID* of the GitGuardian Personal Access Token (a 36-character UUID) instead of the *actual, full token string* (a much longer alphanumeric string, typically 64+ characters) into the GitHub Secret.
    -   **Diagnostic Step:** A diagnostic step was added to the workflow (`echo "Length of GG_API_KEY: ${#GG_API_KEY}"`) to print the masked length of the secret. This revealed the 36-character length, immediately pointing to the token ID as the issue.
    -   **Importance of Exact Copying:** This highlighted the absolute necessity of carefully copying the *entire* token string immediately upon generation, as it's often only displayed once.

### 4. Challenge: Local Pre-commit Hook Authentication

- **Problem:** Even after the GitHub Actions workflow was addressed, the local `ggshield` pre-commit hook started failing with "Invalid GitGuardian API key" during `git commit`.
- **Solution & Learning:** The pre-commit hook's environment was not automatically loading the `GG_API_KEY` from the local environment or the `.env` file.
    -   **`.env` Integration:** The solution involved modifying the `.pre-commit-config.yaml` to explicitly load the `.env` file using `python-dotenv` before `ggshield` executes. This ensures that the local pre-commit hook has access to the `GG_API_KEY` defined in the `.env` file, providing a consistent and secure way to manage local secrets for pre-commit checks.
    -   **Environment Context:** This emphasized that pre-commit hooks run in a specific environment that might not inherit all shell environment variables or automatically load `.env` files, requiring explicit configuration.

### 5. Challenge: Inconsistent `ggshield` CLI Command Structure & Action Usage

- **Problem:** The `gitguardian/ggshield-action@v1` and the `gitguardian/ggshield:v1.45.0` Docker image exhibited inconsistent command structures, leading to "Error: No such command 'secret'." and "Error: No such command 'scan'." This required extensive debugging to determine the correct `ggshield` CLI invocation.
- **Solution & Learning:**
    -   **Direct CLI Execution:** The most robust solution was to bypass the `ggshield-action` entirely and directly execute the `ggshield` CLI within a `docker run` command in the GitHub Actions workflow. This provided granular control over the command and its arguments.
    -   **Command Structure Discovery:** Through iterative debugging, including running `ggshield --version` and `ggshield -h` inside the container, it was definitively determined that for `ggshield` version `1.45.0`, the correct command structure for scanning secrets is `ggshield secret scan path /repo --recursive --verbose`.
    -   **Version Incompatibility:** This highlighted potential version incompatibilities or unexpected behavior when relying on wrapper actions, emphasizing the value of understanding the underlying CLI tool's exact command structure.


---
*README last updated to trigger workflow re-run.*


