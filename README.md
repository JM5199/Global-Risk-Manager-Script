Overview

The Trading Discipline Enforcer v14 is a Tampermonkey script designed to enforce strict trading discipline on platforms such as TopStep, Tradovate, and TradeZella. It automatically manages trading rules, including maximum trade limits, loss limits, session time windows, and contract rules. The script is ready for live trading and provides protection against violating your trading rules by locking your ability to trade under specific conditions.

This version ensures your trading practice stays disciplined and within your set rules, improving your trading performance and reducing emotional trading errors.

Features
1. Max Trade Limits:

Max Trades per Day: Limits the number of trades per day to 6.

Max Loss: Stops trading if you hit a daily loss of $300.

Max Win: Locks trading if your daily profit reaches $500.

2. Time Window:

The script ensures trading only happens during a defined time window: 9:55 AM - 12:00 PM EST.

Trading is locked outside of this time window.

3. Daily Contract Enforcement:

A pop-up enforces you to agree to a daily trading contract, ensuring you commit to:

Trading only 2 micros (MNQ / MES).

No more than 6 trades per day.

Max daily loss of $300.

Keeping a trading journal in TradeZella.

Respecting all locks and cooldowns.

4. Post-Fill Lock:

After every 4th trade, the script automatically locks you out for 15 minutes to prevent overtrading.

5. Hotkey Lock:

A hotkey lock is enabled by pressing == twice within a short time (1.2 seconds). This will trigger a 15-minute lock.

6. P&L Monitoring:

The script detects when you hit your max daily loss or max daily win and locks trading accordingly.

7. Automated Trade Detection:

The script scans the trading platform for filled orders and automatically updates your trade count, enforcing limits on trade counts, fills since lock, and position sizes.

8. Journaling & Check-ins:

You will be prompted to journal your trades in TradeZella every 25 minutes after 9:55 AM.

The system also detects and tracks trade fills and alerts you to any violations of your set rules.

Installation
1. Install Tampermonkey:

First, make sure you have Tampermonkey installed in your browser. You can get it from the Tampermonkey website
.

2. Install the Script:

Open Tampermonkey and create a new script.

Paste the entire script provided here into the script editor.

Save and enable the script.

3. Configure:

You may adjust the configuration parameters in the script, such as:

Max Trades per Day (MAX_TRADES)

Max Loss (MAX_LOSS)

Max Win (MAX_WIN)

Time Window Start (TRADE_WINDOW_START)

Time Window End (TRADE_WINDOW_END)

These values are set to defaults that match a disciplined trading strategy, but you can change them to suit your personal rules.

How It Works

Daily Contract: When you log in to a supported platform (TopStep, Tradovate, or TradeZella), you will be prompted with a daily contract requiring confirmation. Only after agreeing to the contract, will the script enable full functionality.

Trade Restrictions: As you place trades, the script will count them. It will stop you from trading if you reach the Max Trades per Day or exceed your Max Loss/Win. Additionally, after 4 trades, it will enforce a post-fill lock.

Time-Based Restrictions: You can only trade between 9:55 AM and 12:00 PM EST. If you attempt to trade outside of these hours, the script will prevent you from making the trade and lock your ability to trade.

Emergency Lock: If you press == twice within 1.2 seconds, the script will initiate an emergency lock for 15 minutes.

PNL Tracking: The script detects your Profit and Loss in real-time and will lock your account if you exceed the Max Loss or Max Win limits.

Trade Journaling: Every 25 minutes after 9:55 AM, the script prompts you to check in with your trade journal. It will redirect you to TradeZella to complete your journaling.

Troubleshooting

Script Not Running: Ensure Tampermonkey is enabled and the script is active. Reload the trading platform.

Missing Daily Contract: Ensure the platform is supported (TopStep, Tradovate, or TradeZella).

Hotkey Not Working: Double-press == quickly to trigger the emergency lock.

Trade Not Detected: The script uses multiple methods to detect trades (order grid, filled orders, console logs). Make sure your platform supports these features.

Developer Notes

The script is actively maintained to ensure compatibility with the supported platforms.

If you encounter issues or need new features, feel free to raise issues in the GitHub repository or fork the script for personal modifications.

Please ensure you're only using this script for personal use and within the bounds of your trading platform's terms of service.

# Hard Lock Script - Trading Discipline Enforcement
*For users wanting an OS lockout feature when the web risk rules trigger must build and debug to your custom lockout rules


## Overview

The **Hard Lock Script** is a Python-based application designed to help traders enforce discipline by blocking access to trading websites and applications during critical trading periods. The script locks your system, preventing any user input (mouse or keyboard) for a specified duration and blocks access to trading websites via the **hosts** file and **Windows Firewall** rules.

This script is intended to help traders avoid impulsive decisions by enforcing a temporary lockout and blocking access to specific sites.

---

## Features

### 1. **Hard Lock Functionality**
   - **Input Block**: Locks both mouse and keyboard inputs for a configurable time period (default: 1 minute).
   - **Website Blocking**: Blocks access to trading websites (e.g., Tradovate, Topstep) using **Windows Firewall** and **hosts** file.
   - **Hotkey Trigger**: Press `==` (double equal signs) on your keyboard to trigger the lock, which will prevent further input.

### 2. **IP Resolution and Blocking**
   - Resolves the IPs of blocked websites using DNS or Google DNS fallback.
   - Adds these IPs to the **Windows Firewall** and **hosts** file to block access to the sites.
   - Automatically updates blocked IPs as they change.

### 3. **Flask Server Integration**
   - Exposes a local HTTP API endpoint (`/lock`) to trigger the lock remotely via external tools or systems.

---

## Installation

### 1. **Install Python 3.10+**
   - Ensure you have Python version **3.10 or higher** installed. You can download it from the [official Python website](https://www.python.org/downloads/).

### 2. **Install Required Python Libraries**
   - Install the necessary dependencies using `pip`:
   ```bash
   pip install flask psutil pynput pyinstaller
