# BreachLab Wargame (GHOST): Level 1 → 2  

## 📖 Overview
This document outlines the solutions for the subsequent levels of the BreachLab GHOST wargame. The focus of these challenges is mastering Linux shell fundamentals, specifically dealing with shell quoting, escaping special characters (spaces, dashes), and enumerating hidden directories and files.
<img width="1920" height="922" alt="VirtualBox_kali linux_08_07_2026_15_31_14" src="https://github.com/user-attachments/assets/57fe0cab-c374-43f1-8b8f-a8162058f3e9" />

---

## 🔍 Phase 1: Level 1 → 2 (Name Game) - Challenge Briefing

Before accessing the terminal for the next level, we review the challenge parameters on the BreachLab dashboard.

### 1. Dashboard Reconnaissance
The platform dashboard for "Level 1 → Level 2 (Name Game)" highlights the core concepts: `cat`, `ls`, and `man`. The briefing explicitly states the real-world significance: *"Shell quoting is the foundation for shell injection, path traversal, and every real attack that abuses how operators pass arguments to other programs."*
*(Screenshot showing the BreachLab web interface and Level 1 briefing)*
![Level 1 Dashboard Briefing](IMG-20260708-WA0005.jpg)

---

## 💻 Phase 2: Access & File System Enumeration

We establish our connection to the server using the password recovered from Level 0 (`W3lc0m3T0Gh0st`).

### 1. SSH Connection & Briefing
We log in as `ghost1` on port 2222. The Message of the Day (MOTD) sets the stage: *"KAEL was paranoid. He named his files in ways that make the shell fight you. Read the MANIFEST. Then figure out how."*
```bash
ssh ghost1@204.168.229.209 -p 2222
