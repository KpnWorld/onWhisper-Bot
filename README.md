# 🤫 onWhisper

A feature-rich Discord bot built with Pycord, designed to make your server feel personal, powerful, and organized. From advanced moderation to a uniquely private **Whisper System**, onWhisper helps you manage your community with ease.

---

## 🌟 Key Features

### 🧩 Whisper System (Signature Feature)
- Users can `/whisper` staff for private help or reports  
- Creates a **private thread** between the user and support team  
- Only visible to the user and configured staff role(s)  
- Automatically closes inactive whispers after a configurable time  
- Replaces traditional ticket systems with a seamless, modern approach  
- Optional anonymous mode *(coming soon!)*

---

### 🎮 Leveling System
- XP gain from message activity  
- Configurable XP gain rate and cooldown  
- Level-up announcements with visual progress bars  
- Server-wide leaderboards  
- Role rewards for reaching specific levels  

---

### 👮 Moderation
- Kick, ban, timeout, purge, slowmode, snipe, and lockdown  
- Warning system with optional expiry  
- Channel/member activity logging  
- Staff permission checks and logs  

---

### 🎭 Role Management
- Auto-roles for new members  
- Interactive reaction role menus  
- Bulk role assignment and removal  
- Full permission error handling  
- Role and unbinding logs  

---

### 📝 Logging
- Logs: message edits/deletes, member joins/leaves, role/channel changes  
- Dedicated channels for mod, member, and server logs  
- Clean embeds with timestamps  
- Toggleable logging features  

---

## 🧾 Commands

### Whisper System
- `/whisper <message>` — Start a private whisper thread to staff  
- `/whisper close` — Manually close your whisper  
- `/config whisper toggle` — Enable/disable the whisper system  
- `/config whisper staff <role>` — Set staff role for whispers  
- `/config whisper timeout <minutes>` — Set auto-close timer  
- `/config whisper anonymous` *(coming soon)* — Enable anonymous whispering

---

### Leveling
- `/config xp rate <amount>` — Set XP per message (1–100)  
- `/config xp cooldown <seconds>` — Set XP cooldown  
- `/config xp toggle` — Enable or disable XP gain  

- `/config level add <level> <role>` — Add level-up role  
- `/config level remove <level>` — Remove level-up role  
- `/config level list` — View all level roles  

---

### Moderation
- `/warn <user> <reason>` — Issue a warning  
- `/warnings <user>` — View warnings  
- `/kick`, `/ban`, `/timeout` — Member actions  
- `/purge <amount>` — Delete messages  
- `/lockdown [channel] [duration]` — Temporary lockdown  
- `/slowmode <seconds> [channel]` — Enable slowmode  
- `/snipe` — View last deleted message  

---

### Role Management
- `/roles auto set <role>` — Enable auto-role  
- `/roles auto remove` — Disable auto-role  
- `/roles react bind <msg_id> <emoji> <role>` — Emoji-role binding  
- `/roles react unbind <msg_id>` — Unbind reactions  
- `/roles bulk add/remove <role> <users...>` — Bulk role actions  

---

### Info
- `/info help [command]` — Help menu  
- `/info bot` — Bot stats and latency  
- `/info server` — Server stats  
- `/info user [user]` — User profile  
- `/info role <role>` — Role details  
- `/info uptime` — Bot uptime  

---

### Developer Tools
- `/debug sync` — Sync slash commands  
- `/debug reload <cog>` — Reload cog  
- `/debug cleanup [limit]` — Clean bot messages  

---

## 🧂 Database Schema

Data is stored per-guild with unique structures for features.

### Guild Storage (`{botname}:guild:{guild_id}`)
```json
{
  "whisper_config": {
    "enabled": true,
    "staff_role": "role_id",
    "auto_close_minutes": 1440
  },
  "whispers": [
    {
      "user_id": "123456789",
      "thread_id": "123456789",
      "created_at": "ISO8601",
      "closed_at": null
    }
  ],
  "xp_settings": {
    "rate": 15,
    "cooldown": 60,
    "enabled": true
  },
  "xp_users": {
    "user_id": {
      "level": 1,
      "xp": 170,
      "last_xp": "ISO8601"
    }
  },
  "level_roles": {
    "level": "role_id"
  },
  "mod_actions": [
    {
      "action": "warn",
      "user_id": "123",
      "details": "reason",
      "timestamp": "ISO8601",
      "expires": "ISO8601 or null"
    }
  ],
  "reaction_roles": {
    "message_id": {
      "emoji": "role_id"
    }
  },
  "logs_config": {
    "mod_channel": "channel_id",
    "join_channel": "channel_id",
    "enabled": true
  }
}
```
---
## 🧹 Automation
- Whisper threads auto-close after timeout
- Mod logs trimmed to last 100 actions
- Event logs expire after 30 days
- Weekly database optimization

## 💡 Contributing

Found a bug? Want to improve the Whisper System?
Submit issues, feedback, or PRs. We’d love help pushing onWhisper forward.

📄 License
Licensed under the MIT License.
