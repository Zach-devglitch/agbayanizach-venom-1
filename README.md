# Discord Command Bot — GitHub + Render Web Service

## Files
- `bot.py` — bot source code
- `requirements.txt` — Python dependencies
- `.python-version` — pins Python 3.12.8 for compatibility
- `render.yaml` — Render Web Service configuration
- `.gitignore` — excludes local secrets and Python cache files

## GitHub
1. Create a new GitHub repository.
2. Upload these files to the repository root (not inside an extra nested folder).
3. Never upload your Discord bot token or a `.env` file.

## Render Web Service
1. In Render, choose **New + → Web Service** and connect the GitHub repository.
2. Runtime: Python.
3. Build command: `pip install -r requirements.txt`
4. Start command: `python bot.py`
5. In **Environment**, add `DISCORD_TOKEN` with your Discord bot token as its value.
6. Deploy and inspect Logs.

If you use the `render.yaml` Blueprint instead, review the service settings and add `DISCORD_TOKEN` when prompted.

## Discord Developer Portal
Under **Bot → Privileged Gateway Intents**, enable **Message Content Intent** and **Server Members Intent** if the commands/features in this bot require them. Invite the bot with the required permissions and the `bot` and `applications.commands` scopes.

## Important notes
- The web route at `/` responds with `Bot is active!`; it does not indicate that Discord login succeeded. Confirm the logs say the bot is connected/ready.
- Render Web Services may sleep on free plans when idle depending on current plan policy; a Discord bot needs to remain connected, so check the current Render plan limitations.
- Files written to the service filesystem may not persist across deploys/restarts. Use a persistent disk or external database if you need saved settings to survive.
