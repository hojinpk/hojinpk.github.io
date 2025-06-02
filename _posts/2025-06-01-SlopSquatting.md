---
layout: single
title: What is SlopSquatting
categories: AI-Security
tags:
  - AI
  - Security
author_profile: false
sidebar:
  nav: docs
---
## What is SlopSquatting?
**SlopSquatting** is a portmanteau of _AI Slop_ and _Typosquatting_. When coding with GenAI, it may unknowingly suggest a malicious library based on web search results. For example, attackers can upload their modules to public repositories like GitHub and describe them using **plausible-sounding documentation or keywords** to make them appear trustworthy. This is intended to trick GenAI into recommending these malicious packages in generated code – especially when the AI relies on popularity signals or star ratings.

A real-world analogy is **typosquatting attacks in package managers** (e.g., `requests` vs `reqeusts` in PyPI), but **SlopSquatting** goes further by relying on sloppy, automated decision-making from LLMs rather than human error.
## How can we prevent it?
There are two major strategies to reduce risk:
### 1. CI/CD-Based Safeguards
Integrate security tools into your build pipeline to scan dependencies and detect supply chain risks. Examples include:
- **JFrog Xray**, **Snyk**, or **ChainGuard** for vulnerability scanning    
- **Terraform**, **CircleCI**, or **GitHub Actions** for automation and enforcement    
- **Software Bill of Materials (SBOM)** generation and validation    

These tools can detect known bad packages or unexpected transitive dependencies before your code hits production.
### 2. Prompt Engineering and Human-in-the-Loop
When using GenAI for code generation:
- Include **explicit instructions** in prompts such as "only use well-known, secure libraries" or "cross-check modules against official documentation".    
- Build a **verification step** into your workflow. For instance, ask the LLM to explain the purpose and origin of each module it suggests.    

> ⚠️ Note: This method is still experimental -- I haven't confirmed if it consistently works across different LLMs.
## Notable Real-World Example
In early 2024, researchers demonstrated that ChatGPT could be manipulated to recommend typosquatted or malicious `npm/PyPI` packages simply by seeding GitHub repositories with realistic-looking READMEs and keywords. This behavior is detailed in papers like:
- _"[Are LLMs Safe Package Recommenders?](https://arxiv.org/abs/2406.10279)"_ (arXiv 2024)    
- GitHub threat reports from [ReversingLabs](https://risky.biz/risky-bulletin-ai-slopsquatting-its-coming/) and [Checkmarx](https://checkmarx.com/blog/typosquatting-campaign-targeting-pythons-top-packages-dropping-github-hosted-malware-with-dga-capabilities/)

These findings highlight how LLMs trained on public code and search results can unknowingly propagate security threats when used naively in software development.
## See Also
- [The Rise of Slopsquatting: How AI Hallucinations Are Fueling a New Class of Supply Chain Attacks](https://socket.dev/blog/slopsquatting-how-ai-hallucinations-are-fueling-a-new-class-of-supply-chain-attacks), April 8, 2025
- [AI hallucinations lead to a new cyber threat: Slopsquatting](https://www.csoonline.com/article/3961304/ai-hallucinations-lead-to-new-cyber-threat-slopsquatting.html), Apr 14, 2025
- [AI's Phantom Packages Invite Slopsquatting Supply Chain Risk](https://www.bankinfosecurity.com/ais-phantom-packages-invite-slopsquatting-supply-chain-risk-a-28059), April 22, 2025