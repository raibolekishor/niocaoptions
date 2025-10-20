# NIOCA - NSE Index Options Chain Analyzer

## Overview

**NIOCA** (NSE Index Options Chain Analyzer) is a desktop application designed for traders and analysts to monitor and visualize real-time options chain data for the **NIFTY** and **BANKNIFTY** indices from the National Stock Exchange (NSE) of India. Built with Python and Tkinter, it provides an intuitive GUI for tracking key metrics like spot prices, open interest (OI), change in OI (COI), volume, implied volatility (IV), PCR ratios, and buildup patterns. The app includes live updates, visual alerts, dark/light themes, and market session handling.

- The app is free for trial use but expires after **3 trading days**.
- To get full version, WhatsApp on +91 7249016255
- For business queries or support, email: **niocaoptions@zohomail.in**.


### Key Highlights
- **Real-Time Data**: Fetches live option chain data from NSE API every 3 seconds.
- **Visual Analytics**: Color-coded tables for quick insights into bullish/bearish signals, max OI/COI/volume highlights, and IV skew.
- **Alerts**: Audio beep on OI/COI imbalance changes (Windows only).
- **Market Awareness**: Auto-switches to closing data post-market hours (Mon-Fri, 9:00 AM - 3:30 PM IST).
- **Themes**: Light/Dark mode toggle for better visibility.
- **India VIX Integration**: Displays live VIX value and change.

**Author**: Kishor Raibole  
**Version**: 1.0 (© 2025 NIOCA. All Rights Reserved)  
**Platform**: Windows (x64)  
**Dependencies**: None (standalone executable).

## Features

### Core Dashboard
- **Index Selection**: Toggle between **NIFTY** and **BANKNIFTY**.
- **Spot Price & Change**: Live index value, absolute/percent change with color-coding (green for up, red for down).
- **Expiry Selection**: Dropdown for available expiry dates (e.g., weekly/monthly).
- **Options Chain Table** (23 strikes centered around ATM):
  - **Columns (Left to Right)**: Call Buildup, Call IV, Call Volume, Call COI, Call OI, Call Change, Call LTP, Strike Price, Put LTP, Put Change, Put OI, Put COI, Put Volume, Put IV, Put Buildup.
  - **Color Coding**:
    - **Green**: Positive signals (e.g., Long Buildup, Short Covering for calls; opposite for puts).
    - **Red**: Negative signals (e.g., Short Buildup, Long Unwinding).
    - **Bold/Highlight**: Max values for OI, COI, Volume.
    - **ATM Row**: Bold font and highlighted background.
- **Summary Metrics** (Bottom Row):
  - **OI Sentiment (%)**: Bias based on call vs. put OI imbalance.
  - **Change OI (%)**: Bias from COI imbalance (triggers audio alert on sign change).
  - **IV Averages**: Over 23 strikes; color-coded by call vs. put skew (green if favorable).
  - **Totals**: Aggregated OI, COI, Volume with comparative coloring.

### Ratios & Indicators
- **Open Interest PCR**: Put OI / Call OI (green >1.2, red <0.8).
- **Change OI PCR**: Put COI / Call COI (similar thresholds).
- **Volume PCR**: Put Volume / Call Volume (green <1 for put-heavy volume, red >1).
- **India VIX**: Live value + change (green up, red down).

### Additional Tools
- **Clock**: Real-time IST clock.
- **Status Bar**: Shows "Online", "Offline", "Using cached data", or "Product Expired".
- **Theme Toggle**: Switch between Light (default) and Dark modes.
- **Expiry Check**: Auto-exits if past 31-Dec-2025; shows warning dialog.

### Data Sources
- **Option Chain**: NSE India API (`https://www.nseindia.com/api/option-chain-indices`).
- **Spot & VIX**: Yahoo Finance (yfinance library).
- **Fallbacks**: Uses cached closing data post-market; defaults to approximate values if API fails.

## System Requirements
- **OS**: Windows 10/11 (64-bit).
- **Hardware**: 2GB RAM minimum; internet connection for live data.
- **Permissions**: Microphone access optional (for alerts); no admin rights needed.
- **Screen Resolution**: Optimized for 1366x768+; resizable window (min 800x600, max 1366x696).

## Installation & Setup

1. **Download**:
   - Get `nioca.exe` from the official source (e.g., GitHub releases or direct from author).
   - File size: ~15-20 MB (includes all dependencies).

2. **Run**:
   - Double-click `nioca.exe` to launch.
   - No installation wizard—runs as a portable app.
   - First run: App checks expiry date. If valid, launches GUI.

3. **Troubleshooting Setup**:
   - **Antivirus False Positive**: Some AVs flag executables; whitelist if needed.
   - **No Internet**: App shows "Offline" and clears tables.
   - **Firewall**: Allow outbound HTTPS to `nseindia.com` and `finance.yahoo.com`.
   - **Logs**: Check console output (if run via cmd: `nioca.exe > log.txt`) for errors.

## Usage Guide

### Launching the App
- Run `nioca.exe`.
- Window maximizes to full screen (zoomed on supported systems).
- Default: NIFTY index, nearest expiry.

### Navigating the Interface
1. **Top Bar**:
   - **Index Dropdown**: Select NIFTY/BANKNIFTY—refreshes data instantly.
   - **Spot Price**: Current index value.
   - **Change**: Absolute + % change.
   - **Expiry Dropdown**: Pick from available dates.
   - **India VIX**: Value + change.
   - **PCRs**: Open Interest, Change OI, Volume ratios.
   - **Product Renewal**: Shows expiry (31-Dec-2025).
   - **Clock**: IST time.
   - **Theme Button**: "Dark" / "Light".

2. **Main Table**:
   - Scroll not needed (fixed 23 rows).
   - Hover/click cells for no action (read-only).
   - Updates every ~3 seconds during market hours.

3. **Interpreting Data**:
   - **Buildup Signals**:
     - **Long Buildup**: Rising OI + LTP (bullish for calls, bearish for puts).
     - **Short Buildup**: Rising OI + Falling LTP (bearish for calls, bullish for puts).
     - **Long Unwinding**: Falling OI + Falling LTP (bearish for calls, bullish for puts).
     - **Short Covering**: Falling OI + Rising LTP (bullish for calls, bearish for puts).
   - **Imbalance %**: Positive = Call-heavy (bullish); Negative = Put-heavy (bearish).
   - **IV Skew**: Higher Put IV vs. Call IV suggests downside protection.

4. **Alerts & Automation**:
   - Audio beep (1000Hz, 500ms) on OI/COI sign flip.
   - Post-3:30 PM IST: Freezes to closing snapshot.
   - Weekends/Holidays: Shows "Offline" or cached data.

### Example Workflow
- Open app during market hours.
- Select BANKNIFTY > Next weekly expiry.
- Monitor Volume PCR <1 (put buying) + Red Call Buildup = Potential downside.
- Toggle Dark theme for night analysis.

## Screenshots
*(Include images in repo: e.g., dashboard_light.png, dashboard_dark.png, table_closeup.png)*

- **Light Theme Dashboard**: <p> <img width="1366" height="729" alt="doc_2025-10-20_21-52-29" src="https://github.com/user-attachments/assets/08cfa64b-1234-43fb-bce6-dbaf2361a5ce" />
- **Dark Theme with Alerts**: <p> <img width="1366" height="730" alt="doc_2025-10-20_21-52-22" src="https://github.com/user-attachments/assets/9ca09dc4-fa32-4c05-b17e-3f901422f456" />


### API Reliability
- Retries: 3x with exponential backoff (5s delay).
- Headers: Mimics Chrome to avoid NSE blocks.
- Errors: Logged to console; GUI shows status.

### Limitations
- **No Mobile Support**: Desktop-only.
- **Internet Required**: Offline mode limited to cache.
- **Expiry**: Hard-coded to 31-Dec-2025; app exits post-date.
- **No Backtesting**: Live data only.
- **Windows Alerts**: Beep unsupported on non-Windows.

## Support & Contact
- **Email**: niocaoptions@zohomail.in (business queries, bugs, renewals).
- **Updates**: Check for new .exe versions periodically.
- **Feedback**: Share via email; no public issues tracker.

## License
© 2025 NIOCA. All Rights Reserved.  
Personal use only. Commercial use requires permission. No redistribution of executable without consent.

---

*Last Updated: October 20, 2025*  
*Built with ❤️ for Options Traders by Kishor Raibole.*
