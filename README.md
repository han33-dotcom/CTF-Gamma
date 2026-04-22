# Gamma CTF Security Assessment Report

> Authorized academic CTF/lab environment only. This repository contains the final course-submission report and supporting scan evidence for the Gamma target.

## Repository Contents

- **Final report PDF:** [docs/Gamma_CTF_Report.pdf](../../raw/main/docs/Gamma_CTF_Report.pdf)
- **LaTeX source:** [docs/Gamma_CTF_Report.tex](docs/Gamma_CTF_Report.tex)
- **Report figures:** [docs/figures](docs/figures)
- **Nessus scan evidence:** [docs/Nessus_Scan.pdf](../../raw/main/docs/Nessus_Scan.pdf)

## Overview

The report documents an end-to-end assessment of the Gamma CTF virtual machine:

1. Reconnaissance and vulnerability assessment.
2. Initial access through a writable NFS export.
3. Privilege escalation through validated local misconfigurations.
4. Flag recovery and impact validation.
5. Remediation and post-remediation verification guidance.

## Key Findings

- A writable NFS export exposed Peter's home directory and enabled SSH key injection.
- Passwordless `sudo` access to `strace` allowed an immediate root shell.
- A root-owned cron backup workflow was vulnerable to wildcard injection.
- Docker group membership provided root-equivalent host access.
- A non-root `insecurity` account had UID 0.
- Weak SSH credentials and excessive sudo privileges enabled additional root paths.
- Nessus confirmed significant patch debt and an unsupported Ubuntu 18.04.x baseline.

## Build

Compile the report from the `docs/` directory:

```bash
pdflatex --miktex-disable-maintenance -interaction=nonstopmode -halt-on-error Gamma_CTF_Report.tex
pdflatex --miktex-disable-maintenance -interaction=nonstopmode -halt-on-error Gamma_CTF_Report.tex
```

The LaTeX source intentionally keeps flags, passwords, and hashes visible because this version is prepared for course submission.

## Author

Prepared by Hassan Nasrallah for EECE 503G - Introduction to Ethical Hacking.
