# Portfolio Repository (Sample)

![Security Scan](https://img.shields.io/badge/GGShield-No%20Secrets%20Found-brightgreen)

This repository demonstrates reproducible security hygiene for portfolio preparation.  
All files here are placeholders; actual content is not exposed.

---

## 🔒 Security & Reproducibility Workflow

This repository is validated through automated and reproducible steps:

1. Created sample files (`cv_sample.txt`, `coverletter_sample.txt`, `notes.txt`)
2. Initialized Git repository using `git init`
3. Staged and committed files with `git add .` and `git commit`
4. Executed GGShield scan: `ggshield secret scan repo .`
5. Confirmed result: **No secrets have been found**
6. Added GitHub Actions workflow (`.github/workflows/secret-scan.yml`) to automate secret scanning:
   - ✅ Runs on every push and pull request
   - 🌙 Scheduled nightly scan at 00:00 UTC
7. Integrated `pre-commit` hook with ggshield:
   - ✅ Scans staged changes before every commit
   - ✅ Blocks accidental inclusion of secrets locally

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

## 📝 Notes

- This repository is designed for demonstration and documentation purposes.  
- File contents are intentionally minimal and non-sensitive.  
- The workflow is portable across any Git-tracked project folder.  
- GitHub Actions configuration is located in `.github/workflows/secret-scan.yml`  
- Pre-commit configuration is located in `.pre-commit-config.yaml`  

---

## 📎 Related Tools

- [ggshield](https://github.com/GitGuardian/ggshield) — CLI tool for detecting secrets in source code  
- [GitHub Actions](https://docs.github.com/en/actions) — CI/CD automation platform  
- [pre-commit](https://pre-commit.com/) — Framework for managing and maintaining multi-language pre-commit hooks  

---

## 🌐 API Connectivity Notes

- ggshield normally verifies scans via GitGuardian API (`api.gitguardian.com`).  
- If the API is unreachable due to network restrictions, use local scanning:  
  ```bash
  ggshield secret scan path .
---

## ☁️ Cloud Environment Notes

This workflow has been tested in environments with restricted connectivity, including Google-related networks.

### Key points
- ggshield scans remain reproducible even when API calls are blocked.  
- Local scanning (`ggshield secret scan path .`) ensures security validation without external dependencies.  
- `.gitignore` prevents environment-specific artifacts (e.g., virtual environments, cache files) from being committed.  
- The workflow is portable across cloud environments (Google, Azure, AWS) and remains aligned with public sector reproducibility requirements.  

