# cisco_parser
This is a network configuration parser for cisco applicances
# Network Config Checker (Simple & Practical)

## What is this?

This is a simple Python tool that helps you **check network device configs for common security issues**.

You paste in outputs from a Cisco device, and the program:

* Organizes the data
* Stores it in a database
* Tells you what’s wrong (and how to fix it)

Think of it like a **basic network audit assistant**.

---

## What does it actually do?

### 1. You paste command outputs

The tool asks you to paste:

* `show version`
* `show vlan brief`
* `show interface`
* `show running-config`

Just paste → type `done` → move on.

---

### 2. It breaks everything down

It pulls out useful info like:

* Hostname, OS, uptime
* VLANs
* Interfaces (up/down, trunk/access, etc.)
* Security settings (SSH, Telnet, AAA, Syslog)

---

### 3. It stores everything

All data goes into a local SQLite database:

* Devices
* Interfaces
* VLANs
* Raw configs (so nothing is lost)
* Findings (issues)

---

### 4. It checks for problems

It looks for common mistakes like:

#### Device issues

* SSH not enabled ❌
* Telnet enabled ❌
* AAA not configured ⚠️
* No syslog ⚠️

#### Interface issues

* Trunk using VLAN 1 🚨
* Trunks allowing all VLANs 🚨
* No port security ⚠️
* No BPDU guard ⚠️
* Unused ports not secured ℹ️

---

### 5. It tells you what to fix

Each issue includes:

* What’s wrong
* How serious it is
* What you should do

---

## How to use it

### Step 1: Install stuff

```bash
pip install pandas tabulate
```

---

### Step 2: Run it

```bash
python your_script_name.py
```

---

### Step 3: Use the menu

You’ll see something like:

```
1 - Show current tables  
2 - Clear tables  
3 - Input configs  
4 - Export tables as CSV  
5 - View compliance issues  
6 - Exit  
```

---

### Step 4: Typical workflow

1. Press **3** → paste configs
2. Press **5** → see issues
3. Press **1** → view stored data
4. Press **4** → export to CSV (optional)

---

## What files get created?

* `part2.db` → your database
* `devices.csv`, `interfaces.csv`, etc. → exports

---

## Why this exists

This project is mainly for:

* Learning network automation
* Practicing parsing CLI output
* Understanding security best practices
* Building something practical for a portfolio

---

## Keep in mind

* It works best with **Cisco-style outputs**
* It’s not perfect (regex parsing can miss edge cases)
* You have to paste configs manually (no SSH automation yet)

---

## 🔮 Ideas for later

* Add ML risk scoring 🤖
* Build a web dashboard 🌐
* Auto-pull configs from devices 🔄
* Support other vendors

---

## Final note

This isn’t meant to be fancy — it’s meant to be **useful and easy to understand**.

If you can paste configs and read the output, you can use this tool.

---
