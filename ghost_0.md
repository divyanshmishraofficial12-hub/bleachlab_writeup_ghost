# BreachLab Wargame (GHOST): Level 0 → 1 (First Contact)

## 📖 Overview
This document outlines the solution for the "First Contact" level of the GHOST wargame series on BreachLab. The objective of this level is to utilize basic Secure Shell (SSH) connectivity and fundamental Linux command-line navigation to locate the hidden password required to progress to the next user (`ghost1`).

---

## 🔍 Phase 1: Initial Access & Briefing

The challenge begins by establishing a connection to the target server using the starting credentials provided by the platform.

### 1. SSH Connection
We initiate a connection to the challenge server on a non-standard port (`2222`) using the initial user account, `ghost0`.
bash
ssh ghost0@204.168.229.209 -p 2222
<img width="1920" height="922" alt="VirtualBox_kali linux_08_07_2026_12_53_31" src="https://github.com/user-attachments/assets/71396875-9d07-41f0-a12b-dea19ae049b7" />
The file outputs the password required for the next level: W3lc0m3T0Gh0st.
(Screenshot showing the terminal commands used to navigate the directories and read the files)
<img width="1920" height="922" alt="VirtualBox_kali linux_08_07_2026_13_00_13" src="https://github.com/user-attachments/assets/2f208376-abec-4f32-91ae-f6b327c1aea3" />
