# Certiport ITS Device Configuration and Management (Windows 10) — Student Study Guide

A self-paced review for the Certiport / GMetrix Information Technology Specialist (ITS) Device Configuration and Management certification exam.

---

## How to Use This Guide

This guide is structured as **fourteen short modules**, building from Windows accounts and permissions up through troubleshooting, backup, networking, cloud, security, and finishing with test-taking strategy. Work through them in order — each module assumes the ones before it.

Every module follows the same rhythm:

1. **Concept** — read the explanation.
2. **Anchor** — a small diagram, table, or rule of thumb you should be able to redraw from memory.
3. **Self-check** — exam-style question(s) plus "explain the distractor" practice.

The single most powerful study habit for this exam is **explaining why the wrong answers are wrong**. If you can do that, the right answer takes care of itself.

### What This Exam Tests Most Heavily

Across the practice exams (83 questions captured), the heaviest weight is on:

- **Windows Settings categories** — knowing where each task lives (Ease of Access vs. Update & Security vs. Apps).
- **Accessibility features** — Magnifier, Narrator, Sticky/Toggle/Filter Keys, Color Filters.
- **NTFS vs. share permissions** and the **move-vs-copy** rule.
- **Group Policy precedence** (the LSDOU order).
- **Troubleshooting tools** — Device Manager, Disk Management, Task Manager, Performance Monitor, SFC, chkdsk.
- **Backup types and behavior** — Full, Incremental, Differential, Mirror.
- **Authentication and MFA** — the three factors.

Lighter but reliable: connectors and cables, MDM enrollment, cloud-service vocabulary (OneDrive vs. SharePoint vs. Teams vs. Azure), and OS recovery options.

---

## Table of Contents

1. [Windows Account Types and User Account Control](#module-1--windows-account-types-and-user-account-control)
2. [Active Directory, Domains, and Group Policy](#module-2--active-directory-domains-and-group-policy)
3. [NTFS Permissions, Share Permissions, and Move/Copy](#module-3--ntfs-permissions-share-permissions-and-movecopy)
4. [Windows Settings and Accessibility Features](#module-4--windows-settings-and-accessibility-features)
5. [Application Installation, Drivers, and Windows Update](#module-5--application-installation-drivers-and-windows-update)
6. [Troubleshooting Tools and the Diagnostic Process](#module-6--troubleshooting-tools-and-the-diagnostic-process)
7. [Backup, Restore, and Power Management](#module-7--backup-restore-and-power-management)
8. [Connectors, Cables, and Network Troubleshooting](#module-8--connectors-cables-and-network-troubleshooting)
9. [Networks, Cloud Services, and Cloud Concepts](#module-9--networks-cloud-services-and-cloud-concepts)
10. [Mobile Device Management and Remote Wipe](#module-10--mobile-device-management-and-remote-wipe)
11. [Authentication, MFA, and Biometrics](#module-11--authentication-mfa-and-biometrics)
12. [Security Policies, Malware, and Mitigations](#module-12--security-policies-malware-and-mitigations)
13. [OS Recovery, Installation Methods, and Printers](#module-13--os-recovery-installation-methods-and-printers)
14. [Test-Taking Strategy and Final Review](#module-14--test-taking-strategy-and-final-review)
15. [Exam-Day Cheat Card](#exam-day-cheat-card)
16. [Master Glossary](#master-glossary)

---

## Module 1 — Windows Account Types and User Account Control

### Concept

The exam expects fluency in the difference between local and Microsoft accounts, the privilege levels (standard vs. administrator vs. guest), and the role of User Account Control (UAC) in temporarily elevating a standard user.

### Anchor: The Account Types

| Type                    | What It Is                                                                                       |
| ----------------------- | ------------------------------------------------------------------------------------------------ |
| **Local account**       | Exists only on this device; works without internet                                               |
| **Microsoft account**   | Cloud-based; works on any internet-connected device (PC, tablet, phone, watch). Not a subscription; doesn't require a VPN. |
| **Standard user**       | Limited rights; can be promoted to Administrator from Manage Accounts                            |
| **Administrator**       | Full **local** control. A *local* admin does **not** make changes to other domain computers — that's a domain admin role. |
| **Guest**               | Minimal access; UAC will **not** elevate guests to standard users                                |

### Anchor: User Account Control (UAC)

UAC's purpose is to grant **temporary admin permissions** to a standard user so they can install applications or change Windows settings without permanently elevating their account.

```
Standard user clicks "install"
            ↓
   UAC prompt: "Allow this app to make changes?"
            ↓
   YES → app installs with admin rights, just for this action
   NO  → app blocked; user remains standard
```

Things to memorize:

- UAC's default behavior is to **notify the user when apps try to make changes**.
- UAC triggers on **app installs**, not just Windows settings changes.
- UAC will **not** promote a guest account to standard.

### Self-Check

> A standard user wants to install a printer driver that requires admin rights. What does Windows use to give them temporary admin permission for that single action?
> A) Domain Admins membership
> B) User Account Control (UAC)
> C) A Microsoft account
> D) Group Policy

**Answer:** B.
**Why the others are wrong:** A would permanently elevate them. C is unrelated. D enforces settings, doesn't grant runtime elevation.

> Which best describes a Microsoft account?
> A) Subscription-based; requires a VPN
> B) Local-only; works offline only on the device that created it
> C) Cloud-based; works on any internet-connected device
> D) Available only on Windows Pro and Enterprise

**Answer:** C.

---

## Module 2 — Active Directory, Domains, and Group Policy

### Concept

Active Directory is the spine of corporate Windows environments. The exam tests both the **directory services vocabulary** (AD DS, Azure AD, Azure AD Connect) and the **Group Policy precedence rule** that decides which setting wins when multiple GPOs apply.

### Anchor: Directory Services

| Term                                        | What It Does                                                                                          |
| ------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| **Active Directory Domain Services (AD DS)** | On-prem directory service for user, computer, and group accounts                                     |
| **Azure Active Directory (Azure AD)**       | Cloud directory; hosts user accounts for Microsoft cloud offerings                                    |
| **Azure AD Connect**                        | Windows server-based service that **syncs** on-prem AD DS to Azure AD                                 |
| **Domain join**                             | Adds a computer to a domain. Needs the *Create computer object* permission — **not** Domain Admins membership |
| **Workplace Join**                          | Joins a single device to a workplace (different from a full domain join)                              |

A common trap: domain join does **not** require Windows Pro specifically; Enterprise can also join.

### Anchor: The LSDOU Precedence Order

When multiple Group Policy Objects target the same setting, the **last applied wins**. The application order from lowest priority to highest is:

```
1. LOCAL              (the device's own policy)
2. SITE               (AD site)
3. DOMAIN
4. ORGANIZATIONAL UNIT (OU)   ← applied LAST, wins
```

Memorize the mnemonic: **L–S–D–O–U** ("Like Sysadmins Dance On Updates").

Things to memorize:

- **OU settings override domain settings** because OU is applied later.
- In a domain, Group Policy **does** override local system policy.
- Multiple GPOs combine into an effective policy hierarchically.

### Self-Check

> A user is a member of a domain. A domain GPO sets the desktop wallpaper to corporate blue, and an OU GPO sets it to white. Which wallpaper does the user see?
> A) Corporate blue (domain wins)
> B) White (OU wins because it's applied last)
> C) Whichever was set first
> D) The local desktop wallpaper

**Answer:** B. LSDOU — OU is applied last and overrides earlier levels.

> Which service syncs an on-prem Active Directory to Azure AD?
> A) Azure Files
> B) Azure AD Connect
> C) Microsoft Intune
> D) Windows Hello

**Answer:** B.

---

## Module 3 — NTFS Permissions, Share Permissions, and Move/Copy

### Concept

This is one of the highest-leverage modules on the exam. You must distinguish **NTFS file permissions** from **share permissions**, know which permissions are **basic** vs. **advanced**, and apply the **move-vs-copy** rule that decides whether permissions are retained or inherited.

### Anchor: Basic NTFS File Permissions

```
Full Control
Modify
Read & Execute
Read
Write
```

These are the five **basic** NTFS permissions. Advanced NTFS permissions (Read attributes, Write attributes, Take Ownership) are *not* in the basic set.

### Anchor: Share Permissions

Share permissions are **simpler** than NTFS:

```
Read / Write
Owner
```

Share permissions do **not** include Modify or Read & Execute — those are NTFS file permissions, not share permissions. When sharing from a cloud server, permissions are assigned to **users and groups** (not sites or domains).

### Anchor: The Move-vs-Copy Rule

This single rule answers most permission-behavior questions on the exam:

```
MOVE within the same partition          → permissions RETAINED
MOVE to a different partition            → permissions INHERITED from the new parent
COPY anywhere                            → permissions INHERITED from the destination
                                           (treated as a NEW file)
```

The intuition: a **copy** creates a new file, so it picks up the destination's permissions. A **move within the same partition** is essentially a rename — the original file (with its explicit permissions) just gets a new path.

### Anchor: Share Types

| Type             | Behavior                                                                  |
| ---------------- | ------------------------------------------------------------------------- |
| **Basic share**  | Simple sharing; no custom user/group permissions; no connection limits    |
| **Advanced share** | Supports custom user/group permissions and a limit on simultaneous users |
| **Public share** | Files available to all accounts on the device                             |

The **Security tab** in a folder's Properties is for **NTFS permissions**, not share permissions.

### Self-Check

> A file in `D:\Reports\Q3.docx` has explicit "Modify" for Alice. The file is **moved** to `D:\Archive\` (same partition). What are Alice's permissions on the moved file?
> A) Inherited from `D:\Archive\`
> B) Modify is retained
> C) Read-only by default
> D) Removed

**Answer:** B. Move within the same partition retains explicit permissions.

> A file is **copied** from `D:\` to a USB drive (`E:\`). What governs the copied file's permissions?
> A) The original file's explicit permissions
> B) Permissions inherited from `E:\`
> C) The user's account type
> D) Group Policy

**Answer:** B. Copies always inherit from the destination.

> Which is **not** a basic NTFS permission?
> A) Full Control
> B) Modify
> C) Take Ownership
> D) Read

**Answer:** C. Take Ownership is an advanced NTFS permission.

---

## Module 4 — Windows Settings and Accessibility Features

### Concept

The exam frequently asks "which Settings category contains this option?" and "which accessibility feature does this?" Memorize the categories cold, then drill the accessibility features individually.

### Anchor: The Windows Settings Categories

| Category                | Holds…                                                                       |
| ----------------------- | ---------------------------------------------------------------------------- |
| **System**              | Display, sound, notifications, power                                         |
| **Devices**             | Bluetooth, printers, mouse                                                   |
| **Phone**               | Link Android / iPhone                                                        |
| **Network & Internet**  | Wi-Fi, airplane mode, VPN                                                    |
| **Personalization**     | Background, lock screen, colors                                              |
| **Apps**                | Uninstall, defaults, optional features                                       |
| **Accounts**            | Sign-in, email, sync, work, family                                           |
| **Time & Language**     | Speech, region, date                                                         |
| **Gaming**              | Xbox Game Bar, captures, Game Mode                                           |
| **Ease of Access**      | Narrator, Magnifier, high contrast, **audio accessibility**                  |
| **Search**              | Find files, permissions                                                      |
| **Privacy**             | Location, camera, microphone                                                 |
| **Update & Security**   | Windows Update, recovery, backup, **Windows Defender / Firewall**            |

Two scenarios that come up repeatedly:

- "Audio alerts shown visually" → **Ease of Access**.
- "Enable / disable Windows Defender" → **Update & Security**.

### Anchor: Accessibility Features

| Feature                | Does What                                                              |
| ---------------------- | ---------------------------------------------------------------------- |
| **Magnifier**          | Enlarges text **as the mouse hovers** over it                          |
| **Narrator**           | Reads text aloud                                                       |
| **High Contrast**      | Helps vision-impaired users see the screen                             |
| **Color Filters**      | For color-blindness (red/green, blue/yellow)                           |
| **On-Screen Keyboard** | Helps users with mobility issues                                       |
| **Sticky Keys**        | Press multi-key combos (e.g., Ctrl+S) one key at a time                |
| **Toggle Keys**        | Plays a sound when Caps / Num / Scroll Lock are pressed                |
| **Filter Keys**        | Keyboard ignores brief or repeated keystrokes                          |
| **Speech Recognition** | Input via voice — helps users avoid typing (does **not** help hearing) |

A common trap: **Mouse settings** and **Text size** are general system settings — *not* in the Accessibility category.

### Self-Check

> Which feature enlarges text as the mouse hovers over it?
> A) Narrator
> B) Magnifier
> C) High Contrast
> D) Color Filters

**Answer:** B.

> A user with limited finger mobility wants to press Ctrl+Shift+Esc one key at a time instead of all at once. Which feature should they enable?
> A) Toggle Keys
> B) Filter Keys
> C) Sticky Keys
> D) Speech Recognition

**Answer:** C.

> In which Settings category do you enable or disable Windows Defender?
> A) Privacy
> B) System
> C) Update & Security
> D) Personalization

**Answer:** C.

---

## Module 5 — Application Installation, Drivers, and Windows Update

### Concept

You should know **where applications install**, **how to repair / uninstall them**, and **what kinds of updates Windows Update handles** (versus the app itself or the manufacturer's website).

### Anchor: Where Apps Install

| App Type                                  | Default Install Location          |
| ----------------------------------------- | --------------------------------- |
| **64-bit applications**                   | `C:\Program Files\`               |
| **32-bit applications on 64-bit Windows** | `C:\Program Files (x86)\`         |
| **User-specific application data**        | `AppData` folder                  |

`Documents` is for user files, **not** apps.

### Anchor: Install / Repair / Update / Uninstall

| Task                                      | Where to Do It                                                         |
| ----------------------------------------- | ---------------------------------------------------------------------- |
| **Repair / reinstall a desktop app**      | **Apps & Features** *or* **Control Panel**                             |
| **Update / rollback a driver**            | **Device Manager**                                                     |
| **OS updates**                            | **Windows Update**                                                     |
| **App updates**                           | Mostly inside the app itself; some via Microsoft Store                 |
| **Uninstall properly**                    | Start menu (right-click → Uninstall) or Settings → Apps & Features    |

After a Windows Update that gates a Store install, **reboot** before the install will succeed.

### Anchor: Windows Update Categories

| Category               | What It Covers                                                                |
| ---------------------- | ----------------------------------------------------------------------------- |
| **Automatic updates**  | Turn on so the user never misses critical fixes or driver updates             |
| **Optional updates**   | Typically include **driver** updates and some Windows updates                 |
| **Security updates**   | **Not** optional                                                              |
| **Firmware updates**   | Device-specific (e.g., Microsoft Surface line)                                |

Auto-config is supported for the OS and most software apps. Drivers update less commonly via auto.

### Self-Check

> A user reports that a 32-bit utility installed on their 64-bit Windows 10 PC. Where did Windows place it by default?
> A) `C:\Program Files\`
> B) `C:\Program Files (x86)\`
> C) `C:\AppData\`
> D) `C:\Users\Public\`

**Answer:** B.

> Where do you go to **roll back** a graphics-card driver after a problematic update?
> A) Apps & Features
> B) Device Manager
> C) Disk Management
> D) Microsoft Store

**Answer:** B.

---

## Module 6 — Troubleshooting Tools and the Diagnostic Process

### Concept

Match the tool to the job. The exam asks "which tool would you use to…?" repeatedly, so memorize the canonical task for each tool. Also remember the **first step** in the general troubleshooting process: gather information.

### Anchor: Troubleshooting Tools — Tool to Job

| Tool                                       | Use For                                                                            |
| ------------------------------------------ | ---------------------------------------------------------------------------------- |
| **Device Manager**                         | Hardware device problems; driver install / update / rollback                       |
| **Disk Management** (Computer Management)  | Initialize, create / delete / extend / shrink volumes; change drive letter; verify disk recognition |
| **Performance Monitor**                    | Measure CPU, RAM, network, disk performance                                        |
| **Task Manager**                           | See running processes and their resource use                                       |
| **Program Compatibility Troubleshooter**   | Fix older apps that won't run                                                      |
| **Error Checking** (Tools tab) / `chkdsk`  | Scan a disk for errors / bad sectors                                               |
| **Optimize** (formerly Defragment)         | Defragments a disk — does **not** check for errors                                 |
| **System File Checker (SFC)**              | Checks for corrupted system files (not disk errors)                                |

A common trap: **Optimize** is for defragmentation; **Error Checking** / `chkdsk` is for bad sectors. Don't swap them.

### Anchor: The General Troubleshooting Process

```
1. GATHER INFORMATION   → describe the issue (you can't fix what you can't define)
2. CHECK THE BASICS     → power, cabling, restart, swap cables for hardware-not-recognized issues
3. UPDATE / VERIFY      → get the latest driver from the manufacturer's website
4. ESCALATE             → only after the above
```

Specific gotchas the exam loves:

- For **external device** issues, get the latest driver from the **manufacturer's website** — Device Manager often lacks the newest drivers.
- For **Bluetooth** connectivity that worsens with distance, replace the **batteries** in the Bluetooth device.

### Anchor: What Disk Management Cannot Do

Disk Management **cannot** create system restore points — that's **System Protection / System Restore**.

### Self-Check

> Which tool is best for shrinking a partition to free up space for a new volume?
> A) Performance Monitor
> B) Disk Management
> C) Task Manager
> D) Device Manager

**Answer:** B.

> A user calls in saying "the printer doesn't work." What's the **first** step in troubleshooting?
> A) Reinstall the printer driver
> B) Replace the printer
> C) Gather information about exactly what's happening
> D) Run System File Checker

**Answer:** C.

> Which tool checks a hard disk for **bad sectors**?
> A) Optimize (Defragment)
> B) Error Checking / `chkdsk`
> C) Task Manager
> D) Disk Management

**Answer:** B.

---

## Module 7 — Backup, Restore, and Power Management

### Concept

Two related operational topics share this module: **backup strategy** (which type of backup to run when) and **power states** (Sleep vs. Hibernate vs. Standby vs. Shutdown).

### Anchor: Windows Backup and Restore Features

| Feature           | What It Does                                                            |
| ----------------- | ----------------------------------------------------------------------- |
| **File History**  | Backs up and restores **multiple versions** of files                    |
| **File Recovery** | Recover deleted files (Windows 10 v2004+)                               |
| **Recycle Bin**   | Temporary holding before permanent deletion                             |
| **System Restore**| Restore system files to a saved restore point                           |

### Anchor: Backup Types

| Type             | Backs Up                                            | Resets Archive Bit? |
| ---------------- | --------------------------------------------------- | ------------------- |
| **Full**         | All selected data; usually weekly                   | ✅ Yes              |
| **Mirror**       | Exact copy of source; updates as source changes     | (n/a — mirror)      |
| **Incremental**  | Data created or changed since the **last backup**   | ✅ Yes              |
| **Differential** | Data created or changed since the **last full**     | ❌ No               |

The trick to remember: **Incremental** stacks small backups since the *last* one, but **Differential** always references the last *full* backup and grows over the week.

### Anchor: Recommended Balanced Strategy

```
FULL backup, weekly  +  DIFFERENTIAL backup, nightly

Restore = last full + most recent differential   (only two steps)
```

This conserves storage (compared to nightly fulls) and minimizes restore steps (compared to nightly incrementals).

### Anchor: Power States

| State         | Where State Is Stored | Notes                                          |
| ------------- | --------------------- | ---------------------------------------------- |
| **Sleep**     | RAM                   | Quick wake; loses state on power loss          |
| **Hibernate** | Hard drive            | Slower resume; state survives power loss       |
| **Standby**   | (Inactive mode)       | Laptop's actual inactive mode                  |
| **Shutdown**  | (Nothing)             | Fully off; unsaved data is lost                |

### Self-Check

> A company runs a full backup on Sunday and incremental backups Monday through Friday. The system fails on Friday afternoon. How many backups must be restored to recover?
> A) 1 (the latest incremental)
> B) 2 (the full and the latest incremental)
> C) 6 (the full + each incremental Mon–Fri)
> D) 7

**Answer:** C. To restore from incrementals, you need the full plus **every** incremental since.

> Which power state stores the system's state on the **hard drive** so it survives a power loss?
> A) Sleep
> B) Hibernate
> C) Standby
> D) Shutdown

**Answer:** B.

---

## Module 8 — Connectors, Cables, and Network Troubleshooting

### Concept

Match the connector to the use case, and recognize the symptoms of common network problems (especially **APIPA** addresses).

### Anchor: Cable / Connector Reference

| Connector         | Carries                       | Common Use                                       |
| ----------------- | ----------------------------- | ------------------------------------------------ |
| **HDMI**          | Video + digital audio         | Game consoles, streaming devices to HD TVs       |
| **Mini-HDMI**     | Same as HDMI, smaller         | Tablets, portable cameras                        |
| **DisplayPort**   | Video                         | Daisy-chained monitors                           |
| **VGA**           | Analog video only             | Legacy monitors                                  |
| **DVI**           | Video only                    | Older PC monitors                                |
| **3.5 mm audio**  | Analog audio only             | Headphones / headsets                            |
| **Ethernet**      | Wired networking              | Connect a device to a wired network              |
| **USB**           | Power + data                  | Universal accessory connection                   |
| **USB-C**         | Reversible USB; power + data  | Modern laptops, cameras                          |

Memorize: HDMI carries **both** video and audio; VGA and DVI carry **only** video.

### Anchor: APIPA — The Tell-Tale Sign of a DHCP Failure

```
169.254.x.x   →  device couldn't reach a DHCP server
                  (Automatic Private IP Addressing kicks in as a fallback)
```

APIPA is **neither static nor dynamic**. If you see a `169.254.…` address, the device couldn't get an IP from DHCP.

### Anchor: Network Troubleshooting Order

For a wired Ethernet user:

1. **First** verify the cable is plugged in correctly.
2. For **intermittent slow Ethernet**, suspect a **faulty cable** or **bad port** before blaming the switch power or drivers.
3. DNS or web-server issues are **separate** from APIPA symptoms — don't conflate.

### Self-Check

> A user reports their laptop has the IP address `169.254.42.18`. What is most likely happening?
> A) The user manually set a static IP.
> B) The DHCP server is unreachable, so the laptop self-assigned an APIPA address.
> C) The laptop is on a public IP.
> D) The DNS server is misconfigured.

**Answer:** B.

> A user wants to connect a console to a TV with **both** video and audio over a single cable. Which connector?
> A) VGA
> B) DVI
> C) HDMI
> D) 3.5 mm audio

**Answer:** C.

---

## Module 9 — Networks, Cloud Services, and Cloud Concepts

### Concept

A short but reliable cluster of vocabulary questions covers internal vs. partner-facing networks, Microsoft's main cloud services, and the difference between **elasticity** and **scalability**.

### Anchor: Network Scopes

| Term          | Who Can Access                                                                       |
| ------------- | ------------------------------------------------------------------------------------ |
| **Intranet**  | Strictly internal / confidential to the organization; not directly on the public internet |
| **Internet**  | The largest **public** network                                                       |
| **Extranet**  | Gives partners / suppliers / customers **limited** (not full) access to internal resources |

### Anchor: Networking and Cloud Vocabulary

| Term         | Meaning                                                                  |
| ------------ | ------------------------------------------------------------------------ |
| **VPN**      | Secure tunnel between two endpoints                                      |
| **SIEM**     | Collects security alerts and analysis                                    |
| **MDM**      | Mobile Device Management — enforces BYOD policy on personal/mobile devices |
| **SMB (Server Message Block)** | File / print sharing protocol                              |

### Anchor: Microsoft Cloud Services

| Service        | Best For                                                                     |
| -------------- | ---------------------------------------------------------------------------- |
| **OneDrive**   | Cloud file storage (like traditional file storage in the cloud)              |
| **Azure**      | High-workload apps, virtual machines, multi-platform access                  |
| **SharePoint** | Intranet-based collaboration site for storing and sharing files and folders  |
| **Teams**      | Chat, virtual meetings, and file sharing for collaboration                   |

### Anchor: Elasticity vs. Scalability

```
ELASTICITY    →  a SINGLE resource (one VM) automatically gains or releases CPU/RAM
                  as workload changes

SCALABILITY   →  the NUMBER of resources (multiple VM instances) grows or shrinks
                  to meet demand
```

Other cloud terms:

- **Offline file synchronization** — lets users keep working on cloud files when offline; syncs when reconnected.
- **Blob storage** — object storage for files (not the offline-work feature).
- **Hot storage tier** — for frequently accessed data.

### Self-Check

> A vendor needs limited access to a customer-tracking system inside the company. Which network type fits?
> A) Intranet
> B) Internet
> C) Extranet
> D) VPN

**Answer:** C.

> A workload spike causes one VM to automatically gain more RAM and CPU without changing the number of VMs. This is best described as:
> A) Scalability
> B) Elasticity
> C) Replication
> D) Failover

**Answer:** B.

---

## Module 10 — Mobile Device Management and Remote Wipe

### Concept

Mobile Device Management (MDM) lets an organization apply security policies to phones and tablets — including BYOD devices. The exam tests **enrollment**, **agent installation**, **policy compliance**, and the difference between **full** and **account-only** remote wipes.

### Anchor: How MDM Works

```
1. ADMIN sets policies in the MDM server (e.g., Microsoft Intune)
2. DEVICE installs an agent (an app, sometimes a certificate) and enrolls
3. SERVER pushes policy: passcode, encryption, app restrictions, etc.
4. SERVER monitors compliance; non-compliant devices are flagged
```

Things to memorize:

- A device must be **enrolled** in the MDM before it can interact with it.
- An **agent** (usually an app) must be installed to enroll and communicate.
- **Microsoft Intune** is an example of an MDM server.
- An MDM policy can change OS requirements; older devices that no longer meet them are flagged **non-compliant**.

### Anchor: Location Tracking Setup

For location tracking, **Location** (Android) or **Location Services** (iOS) must be turned on. Wi-Fi or cellular alone is not enough.

### Anchor: Remote Wipe Types

| Type                          | Erases                                                |
| ----------------------------- | ----------------------------------------------------- |
| **Full wipe**                 | **Everything** — personal + business; resets to factory |
| **Account-only remote wipe**  | Business data only; personal data **remains intact**   |

The exam loves to ask which type fits a BYOD scenario. The answer when "the employee owns the device" is usually **account-only**.

### Self-Check

> A BYOD employee leaves the company. The company wants to remove its data from the employee's personal phone **without** touching the employee's photos and personal apps. Which remote wipe should they use?
> A) Full wipe
> B) Account-only remote wipe
> C) Factory reset
> D) Disable the SIM

**Answer:** B.

> Which is **required** for a mobile device to receive policies from an MDM server?
> A) The device must be plugged in
> B) An agent (app) must be installed and the device enrolled
> C) The user must have a Microsoft account
> D) The device must be on Wi-Fi only

**Answer:** B.

---

## Module 11 — Authentication, MFA, and Biometrics

### Concept

Authentication shows up two ways on the exam: **what is and isn't true MFA**, and **what biometric methods exist** and their trade-offs.

### Anchor: The Three Authentication Factors

```
1. KNOWLEDGE (something you KNOW)   →  password, PIN, security question
2. POSSESSION (something you HAVE)  →  token, smart card, badge, phone code
3. INHERENCE (something you ARE)    →  biometric — fingerprint, voice, iris, face
```

**True MFA = at least two *different* factor categories.**

| Combination                    | True MFA?                                  |
| ------------------------------ | ------------------------------------------ |
| Password + PIN                 | ❌ Both are knowledge                      |
| Card + PIN (an ATM)            | ✅ Possession + Knowledge                  |
| Fingerprint + iris scan        | ❌ Both are inherence                      |
| Smart card + fingerprint       | ✅ Possession + Inherence                  |

### Anchor: Smart Cards

A **smart card** is a small computing device (CPU + small storage) used for **authentication only**. It is **not** a storage device, and it does **not** itself encrypt or decrypt data.

### Anchor: Biometric Trade-offs

| Method               | Notes                                                                  |
| -------------------- | ---------------------------------------------------------------------- |
| **Fingerprint**      | Can be replicated; cuts/swelling reduce accuracy                       |
| **Iris / retinal**   | Newer, expensive, less universal                                       |
| **Voice**            | Can be spoofed under certain conditions                                |
| **Facial**           | Can be spoofed under certain conditions                                |
| **Signature**        | Can be spoofed under certain conditions                                |

### Self-Check

> An ATM requires you to insert your card and type your PIN. This is:
> A) Single-factor authentication
> B) True MFA — possession + knowledge
> C) True MFA — inherence + knowledge
> D) Not authentication at all

**Answer:** B.

> Which is **true** about a smart card?
> A) It stores all of a user's encrypted files.
> B) It is used for authentication only and contains a small CPU and storage.
> C) It performs all encryption and decryption for the host PC.
> D) It is a type of biometric.

**Answer:** B.

---

## Module 12 — Security Policies, Malware, and Mitigations

### Concept

This module groups three reliable question clusters: the **policy / contract documents** (AUP, BCP, DRP, MOU, retention), the **malware family**, and the **physical and network mitigations** that defend the organization.

### Anchor: Policies and Documents

| Document                              | Purpose                                                                                |
| ------------------------------------- | -------------------------------------------------------------------------------------- |
| **Acceptable Use Policy (AUP)**       | What employees can / can't do on company devices and the internet                      |
| **Retention Policy**                  | How long data is kept; defines purge schedules                                         |
| **Retention Labels**                  | Implement the details (retain / delete / hold)                                         |
| **Legal Hold**                        | Indefinite hold on a document during litigation                                        |
| **Disposition Review**                | Final check before deletion                                                            |
| **Memorandum of Understanding (MOU)** | Agreement between two parties                                                          |
| **Business Continuity Plan (BCP)**    | Keep the business running during disaster                                              |
| **Disaster Recovery Plan (DRP)**      | Restore IT systems after a disaster                                                    |

### Anchor: The Malware Family

| Type            | One-Liner                                                       |
| --------------- | --------------------------------------------------------------- |
| **Virus**       | Needs an executable to be **run by a user**                     |
| **Worm**        | **Self-replicates**; exploits OS vulnerabilities                |
| **Trojan horse**| **Disguised** as legitimate software                            |
| **Spyware**     | Secretly gathers personal info / activity                       |
| **Adware**      | Unwanted ads / promotions                                       |
| **Ransomware**  | Encrypts data and demands payment                               |

Social-engineering training is warranted when employees give out info on phone calls or click apparently legitimate phishing emails. (Forgetting badges or skipping meetings are not social-engineering issues.)

### Anchor: Mitigation by Threat

| Threat                          | Best Mitigation                                              |
| ------------------------------- | ------------------------------------------------------------ |
| **Physical attacks (server room)** | Lock the room + authentication to enter                   |
| **Unwanted network packets**    | **Firewall**                                                 |
| **Lure attackers, study them**  | **Honeypot** (decoy)                                         |
| **Known malware signatures**    | **Anti-malware**                                             |
| **Phishing**                    | User training; email filtering; MFA                          |

### Self-Check

> Which document defines the maximum time non-essential records may be kept before they are purged?
> A) Acceptable Use Policy
> B) Retention Policy
> C) Memorandum of Understanding
> D) Business Continuity Plan

**Answer:** B.

> A piece of malware spreads automatically across the network without any user action, exploiting a vulnerability in the operating system. This is a:
> A) Virus
> B) Worm
> C) Trojan
> D) Spyware

**Answer:** B.

---

## Module 13 — OS Recovery, Installation Methods, and Printers

### Concept

The closing content module covers what to do when Windows itself needs help (**recovery options**), how to install Windows in the first place (**upgrade vs. custom**), and the small but reliable **printer permissions** topic.

### Anchor: OS Recovery Options

| Option              | Behavior                                                                  |
| ------------------- | ------------------------------------------------------------------------- |
| **Reset OS**        | Keeps user files but reinstalls Windows                                   |
| **Safe Mode**       | Loads with a minimal driver set; can be loaded with or without networking |
| **System Restore**  | Rolls system files back to a saved restore point                          |

A common trap: to **roll back the OS** to before an app caused issues, use **System Restore** — *not* Safe Mode. Safe Mode is for troubleshooting *while* in Windows, not for time-travel.

### Anchor: Installation Methods

| Method                  | Behavior                                                                                |
| ----------------------- | --------------------------------------------------------------------------------------- |
| **Upgrade installation**| Keeps existing apps, files, and settings; only the OS version changes; **no format**    |
| **Custom installation** | Formats the destination drive; clean install. **Back up first.**                        |

Things to memorize:

- Installations **can** be done over a network share.
- A Microsoft account is **not** required for installation.
- The installer prompts for **time zone** (default: Pacific in U.S. media).
- Multi-language support may require a **downloadable language pack**.

### Anchor: Printer Permissions

To **manage** a printer, a user needs:

- **Manage this printer** permission, and
- **Manage documents** permission.

Being in the **Administrators group is not required**. The **Print** permission is granted to **Everyone** by default.

### Anchor: Productivity Customization

- For frequent access to a network resource, create a **desktop shortcut**. Dragging the icon to the desktop *moves* the resource by default — not safe.
- Windows 10 lets users add a **custom toolbar** to the taskbar.
- Start menu icons **can** be customized.
- Window controls: minus = minimize; square = maximize/restore; X = close.

### Self-Check

> A user wants Windows reinstalled but wants to keep their personal documents and photos. Which option fits best?
> A) Custom installation
> B) Reset OS (keep user files)
> C) Safe Mode
> D) Upgrade to a different OS

**Answer:** B.

> A help-desk technician needs to be able to pause and cancel print jobs from a shared printer for the entire team. Which permissions does the technician need?
> A) Print only
> B) Manage this printer + Manage documents
> C) Membership in Administrators
> D) Domain Admin rights

**Answer:** B.

---

## Module 14 — Test-Taking Strategy and Final Review

### The Distractor-Autopsy Method

For every practice question, do this:

1. Pick your answer.
2. **For each *wrong* option, write one sentence explaining why it is wrong.**
3. Only then check the answer key.

If you can articulate why every distractor is wrong, you have actually mastered the concept. If you can't, that's where to study next.

### Reading "Where Is This Setting?" Questions Under Time Pressure

When a Settings question appears, before reading the answers:

1. **Identify the keyword** — "Defender / Firewall," "Narrator / Magnifier," "Wi-Fi / VPN," "Bluetooth / printer."
2. **Map it to a category** — Defender → Update & Security, Narrator → Ease of Access, Wi-Fi → Network & Internet, Bluetooth → Devices.
3. **Then** scan the answer choices.

### Reading Permission Questions

For move/copy questions, walk this decision tree:

```
Was it COPIED?           → inherits from destination
Was it MOVED?
   ├── same partition?   → permissions retained
   └── different partition? → permissions inherited
```

For NTFS-vs-share questions, ask: **Is this list a basic NTFS permission, an advanced NTFS permission, or a share permission?**

### One Sentence to Repeat During the Exam

Pick one of these and repeat it under your breath whenever you get stuck:

- *"LSDOU — OU wins because it's last."*
- *"Move within = retain; move across or copy = inherit."*
- *"169.254 means DHCP failed."*
- *"Sleep = RAM; Hibernate = disk."*
- *"True MFA needs two different factor categories."*
- *"System Restore rolls back; Safe Mode just loads minimal drivers."*

### Mock Quiz (12 Questions Across the Whole Exam)

Try these timed — about 75 seconds per question.

1. UAC's primary purpose is to do what for a standard user?
2. Two GPOs target the same setting — one at the domain level, one at the OU level. Which wins?
3. A file is moved within the same partition. What happens to its NTFS permissions?
4. Which Settings category is used to enable / disable Windows Defender?
5. Which feature enlarges text as the mouse hovers?
6. Where does Windows install a 32-bit app on a 64-bit system?
7. Which tool rolls a graphics-card driver back to a previous version?
8. A company runs a full backup Sunday and differentials Mon–Fri. To restore Friday's data, how many backups are needed?
9. A laptop has IP `169.254.10.5`. What does that mean?
10. A BYOD phone needs business data wiped without touching personal data. Which wipe?
11. Smart card + fingerprint — true MFA?
12. Which malware self-replicates across a network without user action?

#### Answer Key (cover until done)

1. **Grant temporary admin permissions** to install apps or change settings — Module 1.
2. **OU wins** (LSDOU) — Module 2.
3. **Permissions retained** — Module 3.
4. **Update & Security** — Module 4.
5. **Magnifier** — Module 4.
6. **`C:\Program Files (x86)\`** — Module 5.
7. **Device Manager** — Module 5 / 6.
8. **2** (last full + last differential) — Module 7.
9. **DHCP failed; APIPA self-assigned the address** — Module 8.
10. **Account-only remote wipe** — Module 10.
11. **Yes** — possession + inherence — Module 11.
12. **Worm** — Module 12.

---

## Exam-Day Cheat Card

Read this on the morning of the exam. It's the whole guide compressed into a single paragraph:

> Windows account types: **local** (device-only), **Microsoft** (cloud, any device), **standard** (limited), **administrator** (full local, not domain), **guest** (minimal). **UAC** grants temporary admin rights to a standard user for app installs and Windows-settings changes; it does not promote guests. **AD DS** is on-prem; **Azure AD** is cloud; **Azure AD Connect** syncs them. Domain join needs *Create computer object* permission, not Domain Admins. Group Policy precedence: **L → S → D → OU**, last applied wins (OU overrides domain). Basic NTFS permissions: **Full Control, Modify, Read & Execute, Read, Write**. Advanced NTFS: Read attributes, Write attributes, Take Ownership. Share permissions: **Read/Write, Owner**. **Move within partition → retain; move across partitions or copy anywhere → inherit from destination.** Basic share has no custom user perms; advanced share does and supports user limits; the Security tab controls NTFS, not shares. Settings categories: System (display/sound/power), Devices (Bluetooth/printers), Network & Internet (Wi-Fi/VPN), Personalization (background), Apps (uninstall), Accounts (sign-in), Time & Language, Gaming, **Ease of Access** (Narrator/Magnifier/audio accessibility), Search, Privacy (location/camera/mic), **Update & Security** (Windows Update/Defender/Firewall/recovery). Accessibility: **Magnifier** (hover-zoom), **Narrator** (reads aloud), **High Contrast**, **Color Filters** (color blindness), **Sticky Keys** (one key at a time), **Toggle Keys** (Caps/Num sound), **Filter Keys** (ignores brief/repeat), **On-Screen Keyboard**, **Speech Recognition**. 64-bit apps install in `C:\Program Files\`; 32-bit on 64-bit Windows go to `C:\Program Files (x86)\`; user app data lives in `AppData`. Repair / uninstall apps in **Apps & Features** or **Control Panel**; update / rollback drivers in **Device Manager**; OS updates in **Windows Update**; reboot after a Store-gating Windows Update. Tools: **Disk Management** initializes/creates/extends/shrinks volumes (no system-restore points); **chkdsk / Error Checking** finds bad sectors; **Optimize** defragments (doesn't check); **SFC** finds corrupted system files. Troubleshooting starts with **gathering information**; check power and cabling first; get newest drivers from the **manufacturer's website**; weak Bluetooth → replace device batteries. Backup types: **Full** (resets archive bit), **Incremental** (since last backup, resets bit), **Differential** (since last full, doesn't reset), **Mirror** (live copy). **Full + Differential** is the balanced strategy. Power: **Sleep = RAM**, **Hibernate = disk**, Standby (laptop inactive), Shutdown (off). Cables: **HDMI** = video + audio; **DisplayPort** for daisy-chain monitors; **VGA / DVI** = video only; **3.5 mm** = analog audio; **Ethernet** = wired networking; **USB / USB-C** = data + power. **APIPA `169.254.x.x`** means DHCP failed — neither static nor dynamic. Networks: **intranet** (internal only), **internet** (public), **extranet** (limited partner access). Microsoft cloud: **OneDrive** (file storage), **Azure** (VMs, big workloads), **SharePoint** (intranet collaboration), **Teams** (chat/meetings/sharing). **Elasticity** scales one resource (CPU/RAM); **scalability** changes the number of resources. **MDM** needs an enrolled device with an agent; older devices that no longer meet OS requirements are **non-compliant**. **Full wipe** removes everything; **account-only wipe** removes only business data. Authentication factors: **know / have / are**; true MFA = two different categories. **Smart card** is for authentication only — not storage, not encryption. Documents: **AUP** (acceptable use), **Retention Policy** (purge schedules), **Legal Hold** (indefinite during litigation), **MOU** (two-party agreement), **BCP** (business running), **DRP** (IT restoration). Malware: virus needs user action; worm self-replicates; trojan disguises; spyware exfiltrates; adware promotes; ransomware encrypts and demands. Mitigations: server-room locks for physical, firewall for packets, honeypot for decoys, anti-malware for known signatures. Recovery: **Reset** keeps files but reinstalls Windows; **System Restore** rolls back to a restore point; **Safe Mode** loads minimal drivers. Install: **Upgrade** keeps everything; **Custom** formats the drive. Printer management needs **Manage this printer + Manage documents**, not Administrators.

---

## Master Glossary

**Acceptable Use Policy (AUP)** — what employees can and can't do on company devices and the internet.

**Active Directory Domain Services (AD DS)** — on-prem directory service for users, computers, and groups.

**Administrator (local)** — full control of one device; not the same as a domain admin.

**Adware** — malware that displays unwanted advertisements.

**APIPA** — Automatic Private IP Addressing; `169.254.x.x` indicates the device couldn't reach a DHCP server.

**AppData** — folder holding user-specific application data.

**Azure** — Microsoft's cloud platform for VMs and large workloads.

**Azure Active Directory (Azure AD)** — Microsoft's cloud directory.

**Azure AD Connect** — service that syncs on-prem AD DS to Azure AD.

**Backup (Full / Incremental / Differential / Mirror)** — full backs up everything; incremental captures changes since the last backup; differential captures changes since the last full; mirror is a live copy.

**Basic Share** — simple share without custom user permissions or limits.

**Biometrics** — authentication factor based on what you are (fingerprint, voice, iris, face, signature).

**Business Continuity Plan (BCP)** — keeps the business running during a disaster.

**chkdsk** — Windows utility that scans a disk for errors and bad sectors.

**Color Filters** — accessibility feature aiding users with color-blindness.

**Custom Installation** — clean Windows install that formats the destination drive.

**Device Manager** — Windows tool for installing, updating, and rolling back hardware drivers.

**Differential Backup** — backs up data changed since the last **full** backup; doesn't reset the archive bit.

**Disaster Recovery Plan (DRP)** — restores IT systems after a disaster.

**Disk Management** — Windows tool to initialize, create, delete, extend, and shrink volumes.

**Disposition Review** — final check before data is permanently deleted.

**Domain Join** — adding a computer to an Active Directory domain.

**Ease of Access** — Settings category containing Narrator, Magnifier, Sticky Keys, etc.

**Elasticity** — automatic scaling of a single resource's capacity (e.g., one VM).

**Error Checking** — Windows feature on the Tools tab of disk Properties; same purpose as `chkdsk`.

**Extranet** — gives partners limited access to internal resources.

**File History** — Windows feature that backs up multiple versions of files.

**Filter Keys** — accessibility feature that ignores brief or repeated keystrokes.

**Firewall** — blocks unwanted network packets.

**Full Backup** — backs up all selected data; resets the archive bit.

**Full Wipe** — remote wipe that erases everything (personal + business).

**Group Policy Object (GPO)** — set of policies applied at the local, site, domain, or OU level.

**Guest Account** — minimal-access account; UAC won't elevate it to standard.

**Hibernate** — power state that stores system state on the **hard drive**.

**High Contrast** — accessibility theme aiding vision-impaired users.

**Honeypot** — decoy system designed to attract attackers.

**Incremental Backup** — backs up data changed since the last backup of any kind; resets the archive bit.

**Intranet** — internal-only company network.

**LSDOU** — Group Policy precedence order: Local → Site → Domain → OU.

**Magnifier** — accessibility feature that enlarges text on hover.

**MDM (Mobile Device Management)** — server that pushes policies to enrolled mobile devices (e.g., Microsoft Intune).

**Memorandum of Understanding (MOU)** — agreement between two parties.

**Microsoft Account** — cloud-based account usable on any internet-connected device.

**Mirror Backup** — exact copy of source that updates as source changes.

**Move (within same partition)** — preserves the original NTFS permissions.

**Move (across partitions)** — file inherits NTFS permissions from the new parent folder.

**Narrator** — accessibility feature that reads on-screen text aloud.

**NTFS Permissions** — file-system permissions: Full Control, Modify, Read & Execute, Read, Write.

**OneDrive** — Microsoft's cloud file storage.

**Optimize** — defragments a disk; does not check for errors.

**Organizational Unit (OU)** — AD container for grouped objects; OU GPOs apply last and win precedence.

**Performance Monitor** — measures CPU, memory, network, and disk performance.

**Power Plan** — Windows-wide configuration of power and sleep behavior.

**Print Permission** — granted to Everyone by default; allows submitting print jobs.

**Program Compatibility Troubleshooter** — Windows tool for getting older apps to run.

**Public Share** — share whose files are available to all accounts on the device.

**Reset OS** — Windows recovery option that reinstalls Windows while keeping user files.

**Retention Policy** — defines how long different data classes are kept.

**Safe Mode** — Windows boot mode loading minimal drivers for troubleshooting.

**Scalability** — changing the **number** of resources to meet demand.

**Security Tab (Properties)** — controls NTFS permissions, not share permissions.

**SharePoint** — Microsoft's intranet collaboration platform.

**SIEM** — collects and analyzes security alerts.

**Sleep** — power state that stores system state in **RAM**.

**SMB (Server Message Block)** — Windows file/print sharing protocol.

**Smart Card** — authentication device with a small CPU; not for storage; not an encryption engine.

**Speech Recognition** — accessibility feature for voice input; doesn't help hearing impairments.

**Standard User** — limited rights; can be promoted to administrator.

**Sticky Keys** — accessibility feature for pressing multi-key combos one at a time.

**System File Checker (SFC)** — Windows tool that checks for corrupted system files.

**System Restore** — Windows feature that rolls system files back to a saved restore point.

**Task Manager** — Windows tool showing running processes and their resource use.

**Teams** — Microsoft's chat / meetings / collaboration platform.

**Toggle Keys** — accessibility feature that plays a sound when Caps / Num / Scroll Lock are pressed.

**Trojan Horse** — malware disguised as legitimate software.

**Upgrade Installation** — Windows install that keeps existing apps, files, and settings.

**User Account Control (UAC)** — grants standard users temporary admin permissions for elevated actions.

**Virus** — malware that needs an executable to be run by a user.

**VPN** — secure tunnel between two endpoints.

**Windows Update** — Microsoft's OS update mechanism; security updates are not optional.

**Workplace Join** — joins a single device to a workplace; not the same as a full domain join.

**Worm** — self-replicating malware that exploits OS vulnerabilities.
