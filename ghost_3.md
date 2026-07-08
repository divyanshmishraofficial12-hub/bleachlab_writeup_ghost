# BreachLab Wargame (GHOST): Level 2 → 3 & Level 3 → 4

## 📖 Overview
This document covers the transition from Level 2 and the full solution for Level 3 → 4 (Access Denied) in the BreachLab GHOST wargame. The core focus of this challenge revolves around Linux file permissions, understanding the difference between user/group access rights, and navigating restricted directory structures.

---

## 🔍 Phase 1: Level 2 → 3 Dashboard Review

Before diving into the next terminal session, we review the dashboard for the transition into Level 3 to understand the underlying concepts.

### 1. Dashboard Reconnaissance
The platform dashboard for "Level 2 → Level 3 (In the Shadows)" highlights commands like `ls`, `cat`, and `find`. It notes the real-world application of hunting for hidden tools—a concept we utilized in the previous stage to retrieve the `ghost3` password.
*(Screenshot showing the BreachLab web interface and Level 2 → 3 briefing)*
 <img width="1920" height="922" alt="VirtualBox_kali linux_08_07_2026_15_23_14" src="https://github.com/user-attachments/assets/52b5c613-e7c4-4e62-862a-20162dc9a2da" />


---

## 💻 Phase 2: Level 3 → 4 (Access Denied) Initial Connection

We establish our connection to the server using the password recovered from the hidden `.source_omega` file in the previous level (`H1dd3nInSh4dow`).

### 1. SSH Connection & Briefing
We log in as `ghost3` on port 2222. The Message of the Day (MOTD) introduces the new obstacle: *"KAEL structured his storage by access level. Not everything is readable by everyone. Know who you are. Know what you can reach."* The recommended topics to study are `id`, `find`, and `chmod`.
*(Screenshot showing the SSH login, MOTD, and Level 3 briefing)*
 <img width="1920" height="922" alt="VirtualBox_kali linux_08_07_2026_13_34_59" src="https://github.com/user-attachments/assets/eb0f3049-c8e8-4212-9f6a-cc927e46d22e" />


---

## ⚙️ Phase 3: Enumeration & Storage Layout

To find the next password, we must explore the system and understand how KAEL structured his directories.

### 1. Discovering the Map
Listing the home directory reveals a `map.txt` file. Reading it outputs "KAEL'S STORAGE LAYOUT," which defines three key directories:
* `/var/intel/public/` - world readable
* `/var/intel/ops/` - restricted
* `/var/intel/archive/` - root only

### 2. Investigating the Public Directory
We navigate to `/var/intel/public/` and read `report_q1.txt`. The file states: *"This document contains no operational credentials. For restricted files, consult your access group."* This confirms the flag is not in the world-readable area.
*(Screenshot showing the map reading, navigation to the public directory, and the dummy report)*
 <img width="1920" height="922" alt="VirtualBox_kali linux_08_07_2026_13_39_03" src="https://github.com/user-attachments/assets/850b658b-129f-48ce-a674-9a9c5b9562a2" />

---

## 💥 Phase 4: Navigating Permissions & Password Retrieval

We must now test our user's access boundaries against the restricted directories mentioned in the storage map.

### 1. Testing Access Boundaries
We move up one directory level (`cd ..`) to `/var/intel/` and attempt to enter the `archive` directory using `cd archive/`. 
* **Result:** `-bash: cd: archive/: Permission denied`. Since the map stated this was "root only," our current user (`ghost3`) does not have the necessary privileges. Attempting to force entry with `sudo` fails as the command is not found/permitted.

### 2. Accessing the Restricted Operations Directory
Next, we attempt to enter the `ops` directory (`cd ops/`). This succeeds, indicating that `ghost3` belongs to the group with access to this restricted folder.

### 3. Retrieving the Target Password
Inside the `ops` directory, we run `ls` and find two files: `access_codes.dat` and `operative_list.txt`. We use `cat` to read the access codes.
bash
cat access_codes.dat
<img width="1920" height="922" alt="VirtualBox_kali linux_08_07_2026_13_39_26" src="https://github.com/user-attachments/assets/5e2ed294-8aa1-4a38-8aca-06fc0ca520e9" />
