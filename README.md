
# Anti-DDoS & Trigger Flood Protection for FiveM

A lightweight standalone FiveM script that detects and blocks:
- Join spam (connection flood)
- NetEvent/Trigger flood
- Potential server slowdowns (tickrate monitoring)

---

## 🔒 Features

- ✅ IP-based join flood protection  
- ✅ Trigger flood detection (event spam)  
- ✅ Tickrate watchdog (lag / DDoS slow detection)  
- ✅ Console logging  
- ✅ Optional Discord webhook logging  
- ✅ Fully configurable via `config.lua`  
- ✅ Standalone (no dependencies)

---

## ⚙️ Configuration (`config.lua`)

```lua
Config.WebhookLogging = true
Config.WebhookURL = 'https://discord.com/api/webhooks/...'

-- Connection spam protection
Config.ConnectionThreshold = 10       -- Max joins per window (per IP)
Config.ConnectionWindow = 10          -- Time window in seconds

-- Trigger spam protection
Config.LogTriggers = true
Config.TriggerLimit = 20              -- Trigger count per player
Config.TriggerWindow = 10             -- Trigger time window in seconds

-- Lag / DDoS detection via tickrate
Config.LagDetection = true
Config.MaxTickTime = 250              -- ms (anything over this = flagged)
Config.TickCheckInterval = 5000       -- How often to check (in ms)
```

---

## 🛡️ Tickrate Monitoring (Lag / DDoS Detection)

This script continuously monitors the server's **tick time** using `GetHostTickTime()`.

If tick time exceeds the threshold (default: `250 ms`), the script:
- Logs a warning to the console
- Sends a Discord webhook alert (if enabled)
- Includes the current number of players

This helps detect:
- Extreme lag caused by resource abuse
- Heavy NetEvent spam
- Possible low-level DDoS slowdowns

---

## 📦 Installation

1. Place the resource in your server's `resources` folder (e.g. `resources/[anticheat]/anti_ddos`)
2. Add the resource to your `server.cfg`:
   ```
   ensure anti_ddos
   ```
3. Configure your settings inside `config.lua`
4. (Optional) Add your Discord webhook

---

## ❗ Important Notice

This script does **not** prevent real network-layer DDoS attacks such as:
- UDP flood
- SYN flood
- TCP exhaustion

It **does** protect against:
- In-game NetEvent spam
- Connection/join spam
- Cheater-induced lag
- Trigger abuse

For real DDoS protection, use proper infrastructure (e.g. OVH Game, TCPShield, Cloudflare Spectrum).

---

## 🧠 Author

Script created by [Phon1x Projects](https://discord.gg/phon1xprojects)

Need help or custom features? Join the Discord above.
