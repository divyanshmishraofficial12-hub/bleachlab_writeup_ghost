# BreachLab Wargame (GHOST): Level 4 → 5 (Signal in the Noise)

## 📖 Overview
This document outlines the solution for Level 4 → 5 (Signal in the Noise) of the BreachLab GHOST wargame. The core focus of this challenge is log analysis and threat hunting. It requires using command-line text processing utilities, specifically `grep`, to filter through hundreds of decoy files and locate a single anomaly containing the next credential.
<img width="1920" height="922" alt="VirtualBox_kali linux_08_07_2026_15_23_36" src="https://github.com/user-attachments/assets/cc4ac7c6-b239-4fa5-9598-c39c60dcc992" />

---

## 🔍 Phase 1: Challenge Briefing & Setup

Before jumping into the terminal, we review the platform dashboard to understand the expected methodology for this stage.

### 1. Dashboard Reconnaissance
The dashboard for "Level 4 → Level 5 (Signal in the Noise)" highlights `grep` and `find` as the primary commands needed. It contextualizes the challenge in the real world: *"Threat hunting. This is the core loop of every SOC analyst on the planet - find the needle in the log haystack."*
*(Screenshot showing the BreachLab web interface and Level 4 → 5 briefing)*
![Level 4 to 5 Dashboard Briefing](IMG-20260708-WA0014.jpg)

---

## 💻 Phase 2: Initial Connection

We establish our SSH connection using the password recovered from the restricted operations directory in the previous level (`P3rm1ss10ns_M4tt3r`).

### 1. SSH Connection & MOTD
We log in as `ghost4` on port 2222. The Message of the Day (MOTD) sets our objective: *"KAEL dumped everything into the vault. Hundreds of log entries. One of them isn't like the others. The real signal has a different format. Find it."*
```bash
ssh ghost4@204.168.229.209 -p 2222
