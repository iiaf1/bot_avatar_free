# Bot Avatar Free

## What's Included
- `Path.png` — Frame design.
- `compositor.py` — Merges the profile picture and background within the frame.
- `bot.py` — A Discord bot featuring two commands:
- **`/av`** — Requests an image (required) and a background (optional). 
- Leaves no trace of command usage in the channel (no "User used /av" message); the initial interaction response is **ephemeral**, and the final image is sent as a standard bot message without accompanying text. 
- Adds a **Download ⬇️** button below the image. 
- **Restricted**: Works only for the bot owner or a member holding the role specified via the `/mm` command (see below). 
- **`/mm`** — Sets the role authorized to use `/av` in the current server. 
- Accessible only to the bot owner or a member with **Administrator** permissions. 
- **Fully automated saving**: Run `/mm role:<select_role>` once, and it’s done—saved to `guild_roles.json` without manual edits to `.env` or other files. You can change it anytime by re-running the command with a different role. 
- **`/by`** — Displays credits and contact info (author, license, Discord, GitHub). **Public/Unrestricted** — usable by anyone on any server.
- `guild_roles.json` — Automatically generated upon the first use of `/mm` (stores the authorized role for each server). No manual setup required.
- `reset_commands.py` — A script to be run **once** to resolve duplicate command issues. - `.env` — Contains only the token and the owner's ID.
- `requirements.txt` — Required libraries.
- `LICENSE` — MIT License (open-source and free-to-use project).

## Button Workflow (Download → Send)
1. Any member in the channel sees the **framed image** (with the frame) alongside a **Download** button.
2. They click **Download** → The same framed image appears **privately** (ephemeral—visible only to them) with a **Send** button underneath.
3. They click **Send** → The bot sends them the two **original, separate images** (the photo and the background) **without the frame** via **Direct Message (DM)**. 
- If their DMs are closed, they receive a notification instead of the images.

## Restriction: Role Required (or Owner Status) — Set automatically via `/mm`
You don't need to edit `.env` to set the role. Instead:

1. Inside the server, type:
```
/mm role:<select role from the list>
```
(Only the owner or a server admin can use this command.)
2. The bot automatically saves the role for that specific server—any member holding that
role can immediately use `/av`.
3. Want to change it? Simply run `/mm` again with a different role at any time.

⚠️ If no one has run `/mm` in the server yet, **no one except the owner** can
use `/av` (default denial; safer than accidentally leaving access open to everyone). ## Duplicate "/" Commands — Cause and Solution
This happens for two common reasons:
- You synchronized the same command at both the guild level (guild command) and the global level simultaneously → Discord displays two versions until they merge.
- The bot application has both **User Install** and **Guild Install** enabled simultaneously in the Discord Developer Portal under **Installation**.

**Solution:**
1. Ensure the bot is **still in the server** where the duplication is occurring, then run `reset_commands.py` **once**—this deletes global commands as well as any local (guild-scoped) commands registered in every server the bot is currently in:
```
python3 reset_commands.py
```
2. If the duplication persists after the previous step, check the Discord Developer Portal → your app → **Installation**, and ensure only one context is enabled (**Guild Install**). Enabling both **User Install** and **Guild Install** simultaneously causes the command to appear twice, even if there is no actual duplication in the registration itself.
3. Run `bot.py` normally afterward (it performs automatic global synchronization only, without any local registration, so the duplication won't recur for the same reason). ## Setup
1. Install the libraries:
```
pip install -r requirements.txt
```
2. Fill in the `.env` file (only these fields):
```
DISCORD_TOKEN=00000000000000000000000000000000000000000000000000000000000000000
BOT_OWNER_ID=000000000000000000

```
3. Run the bot:
```
python3 bot.py
```
4. In each server where you want to enable the bot, run `/mm` and select the role
authorized to use `/av`.

## Usage
```
/av image:<attach your image>  background:<attach background (optional)>
/mm role:<select the role>
/by   ← Public, without any restrictions
```

## 📬 Contact and Support

For inquiries, bug reports, suggestions, or to contribute to the project:

* 💬 **Discord:** `iaf0`
* 🐙 **GitHub:** [github.com/iiaf1](https://github.com/iiaf1?utm_source=chatgpt.com)

You can open an **Issue** on GitHub or contact me via Discord for support and assistance.

---

## © Copyright and Usage

**Bot Avatar Free**
Copyright © 2026 **iaf1**

All original code, files, and resources in this repository were created by and are the property of **iaf1**.

* **Author / Owner:** iaf1
* **Discord:** `iaf0`
* **GitHub:** [github.com/iiaf1](https://github.com/iiaf1?utm_source=chatgpt.com)

### 📜 License and Terms of Use

This project is provided **completely free of charge** for personal, non-commercial use.

You are permitted to:

* Use the project for free.
* Copy the source code.
* Modify and customize the code.
* Create derivative works for personal or non-commercial purposes.
* Share the project freely, provided the original copyright notice and these terms are retained.

### 🚫 Commercial Use and Resale

You may not **sell, resell, sublicense, or distribute this project as a paid product or service** (including the source code and included original resources) without the express written permission of the author.

You may not:

* Sell the project or any substantial part of its code. * Repackaging the project and offering it as a paid product.
* Charging users for access to the original project or a substantially similar modified version.
* Claiming ownership of the original work or its code.

Any commercial use requires **prior written permission from iaf1**. ### 🎨 Included Resources

The frame design **`Path.png`** is an original resource included with this project and is subject to the same usage restrictions listed above.

### ⚠️ Disclaimer

This project is provided **"as is"** and without any warranties of any kind. The author assumes no liability for any damages, losses, or issues arising from the use or modification of this project.

© 2026 **iaf1** — All rights reserved, except for the permissions expressly granted above.

