# 🔐 Windows 10 Security Hardening Lab  
**Hands-On Defensive Practice | Built-In Tools Only | SOC Analyst Prep**

---

## 🧠 Why I Did This Lab

As part of my journey toward a Tier 1 SOC Analyst role, I wanted to go beyond reading security concepts and actually apply them. This lab is a hands-on walk-through of system hardening using only built-in Windows tools inside an Azure VM. My goal was to better understand how misconfigurations create alert noise, how to spot weak security controls, and how to validate defenses through proper logging and testing.

---

## 🛠️ Tools Used

- Azure Windows 10 Virtual Machine  
- Local Group Policy Editor (`gpedit.msc`)  
- Windows Defender Firewall  
- Event Viewer  
- Native Windows audit policies  
- PowerShell (light use)

All tools were free and came with the operating system.

---

## ✅ What I Did and Why It Matters

### 1. Opened Local Group Policy Editor  
> Used `gpedit.msc` to access and manage local security configurations. This tool is foundational for enforcing consistent password, lockout, and audit policies across a system.

### 2. Configured Password Policy  
- Enforced 12-character minimum  
- Enabled password complexity  
- Set expiration and history  
> These controls help reduce weak password usage and mitigate brute-force login attacks — a common alert type in SIEM tools.

### 3. Enforced Account Lockout Policy  
- Locked accounts after 5 failed login attempts  
- Configured auto-reset after 15 minutes  
> This stops repeated brute-force attempts and generates Event ID 4740, which is crucial for alert triage in a SOC.

### 4. Disabled Unnecessary Services  
- Disabled `Server` (SMBv1)  
- Disabled `Remote Registry`  
> These are commonly abused for lateral movement and remote access. Disabling them reduces the system's attack surface and Living-off-the-Land (LotL) risk.

### 5. Enabled Audit Logging  
- Enabled success/failure logging for logon events  
- Enabled account management and process creation events  
> Logs like 4625 (failed login) and 4688 (process creation) give analysts visibility into suspicious behavior and are essential for compliance and forensics.

### 6. Configured Windows Firewall  
- Blocked inbound SMB, RDP, and WinRM  
> This added a host-level layer of defense to prevent unauthorized access, which complements service hardening and helps detect malicious scanning.

### 7. Validated All Controls  
- Triggered lockout manually  
- Verified logs in Event Viewer  
> Validation ensures settings are enforced and events are captured. These tests mirror the type of validation SOC teams perform post-incident or after applying remediation.

---

## 📸 Screenshots

- `01_local_group_policy_editor.png`  
- `02_password_policy_settings.png`  
- `03_account_lockout_policy.png`  
- `04_disabled_services.png`  
- `05_audit_policy_settings.png`  
- `06_firewall_rules_configured.png`  
- `07_account_lockout_test.png`  
- `08_event_log_verification.png`

---

## 💡 What I Learned

This lab gave me a deeper appreciation for how prevention, detection, and visibility work together. It helped me practice interpreting Windows logs, configuring host-level defenses, and thinking like a SOC analyst when reviewing alerts or endpoint behavior. This is the kind of foundational work that supports accurate triage and effective escalation in real-world environments.

---
