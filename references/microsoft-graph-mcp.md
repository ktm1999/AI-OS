# Microsoft Graph MCP install (personal Hotmail / Microsoft 365)

Saved-once-runnable-anytime walkthrough for wiring `@softeria/ms-365-mcp-server` to Claude Code Desktop on Mac.

**What this unlocks:** Outlook mail (Hotmail), Outlook Calendar (direct), **Microsoft To Do** (your personal task system), OneDrive personal, Teams.

**What this costs:** €0. Microsoft Graph API is free with your existing Hotmail account. Azure App Registration is free.

**What this needs:** ~25 min one-time setup. Mac. Hotmail account.

---

## Prerequisites

- macOS
- A web browser
- Terminal access (built into macOS)
- A `louisgiuliani@hotmail.com` Microsoft account

---

## Step 1. Install Node.js (5 min)

Open **Terminal** (`Cmd+Space` → type "Terminal" → Enter).

Check if Node is already installed:
```bash
node --version
```

If you see `v18.x.x` or higher, skip to Step 2.

If not, install via the official LTS installer:

1. Open https://nodejs.org in your browser.
2. Click the green **LTS** button (recommended for most users).
3. Open the downloaded `.pkg` file.
4. Follow the installer prompts (default settings are fine).
5. Reopen Terminal and verify:
   ```bash
   node --version
   ```
6. You should now see `v20.x.x` or higher.

---

## Step 2. Register an Azure app (10 min)

This is the OAuth identity the MCP server will use to read your Microsoft data. Free, your account, your control.

1. Open https://portal.azure.com in your browser.
2. Sign in with **`louisgiuliani@hotmail.com`**.
3. In the search bar at top, type **"App registrations"** and click the result.
4. Click **"+ New registration"** at the top.
5. Fill in:
   - **Name:** `Louis AIOS Microsoft 365`
   - **Supported account types:** **"Accounts in any organizational directory (Any Microsoft Entra ID tenant - Multitenant) and personal Microsoft accounts (e.g. Skype, Xbox)"**
   - **Redirect URI:** leave blank
6. Click **Register**.
7. On the next screen, copy the **"Application (client) ID"** (format: `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`). You will need this in Step 3. Paste it temporarily into a notes app or password manager.

### Enable public client flow

8. Left sidebar → **"Authentication"**.
9. Scroll down to **"Advanced settings"** → set **"Allow public client flows"** to **Yes**.
10. Click **Save** at the top.

### Grant Microsoft Graph permissions

11. Left sidebar → **"API permissions"**.
12. Click **"+ Add a permission"** → **"Microsoft Graph"** → **"Delegated permissions"**.
13. Search and check each of these (use the search box, then check the box):
    - `Mail.Read`
    - `Mail.Send`
    - `Mail.ReadWrite`
    - `Calendars.Read`
    - `Calendars.ReadWrite`
    - `Tasks.ReadWrite`
    - `Files.Read`
    - `Files.ReadWrite`
    - `User.Read`
    - `offline_access`
14. Click **"Add permissions"** at the bottom.
15. Back on the API permissions list, click **"Grant admin consent for [your account]"** at the top. Click **Yes** to confirm.

You should now see a green check next to each permission.

---

## Step 3. Add the MCP to your Claude Code config (5 min)

In Terminal:
```bash
mkdir -p ~/.claude
open -e ~/.claude/settings.json
```

TextEdit will open the file (creates it if missing). Replace the entire contents with this:

```json
{
  "mcpServers": {
    "ms365": {
      "command": "npx",
      "args": ["-y", "@softeria/ms-365-mcp-server"],
      "env": {
        "MS365_MCP_CLIENT_ID": "PASTE_YOUR_CLIENT_ID_HERE",
        "MS365_MCP_TENANT_ID": "common"
      }
    }
  }
}
```

Replace `PASTE_YOUR_CLIENT_ID_HERE` with the Application (client) ID you copied in Step 2.7. Save the file (`Cmd+S`).

If the file already had content, merge `mcpServers.ms365` into the existing JSON instead of overwriting.

---

## Step 4. Restart Claude Code (1 min)

Fully quit Claude Code Desktop:
- `Cmd+Q` (not just close window).

Reopen Claude Code.

---

## Step 5. Authenticate via device code (3 min)

In Claude Code, send any prompt that touches Microsoft 365. Example:
> "List my recent Microsoft To Do tasks."

The MCP server's first call will print a message containing:
- A URL: `https://microsoft.com/devicelogin`
- A code: typically 8 alphanumeric characters

Steps:
1. Open the URL in your browser.
2. Paste the code.
3. Sign in with `louisgiuliani@hotmail.com`.
4. Approve the permissions screen (you should see all the scopes you granted in Step 2).
5. Close the browser tab.

Back in Claude Code, the tool call should now succeed. The auth token is cached locally on this machine. You will not need to redo this until the token expires (typically 90 days, refreshed automatically via `offline_access`).

---

## Cross-device sync (later, ~15 min)

When you want this MCP available on every Mac and PC you own:

1. Create a **dotfiles repo** on GitHub (private). Add `~/.claude/settings.json` to it.
2. On each new machine: clone the repo, symlink the file into `~/.claude/settings.json`.
3. Run Step 1 (Node) and Step 5 (auth) on each new machine. The Azure registration is already shared.

The auth cache lives at `~/.cache/ms-365-mcp-server/` (or similar). Each machine maintains its own auth cache because that's per-device by design. The Azure app registration and client ID are shared.

---

## Troubleshooting

**"node: command not found" after install:**
Reopen Terminal, or run `source ~/.zshrc`.

**"Cannot find module '@softeria/ms-365-mcp-server'":**
The `npx -y` flag should fetch it on first run. If it fails, run manually: `npx -y @softeria/ms-365-mcp-server` and check for errors.

**Auth fails with "invalid_client":**
Verify the `MS365_MCP_CLIENT_ID` in `~/.claude/settings.json` matches the Application (client) ID in Azure exactly.

**Auth succeeds but tools return "unauthorized":**
Verify "Grant admin consent" was clicked in Step 2.15. Without that, scopes are requested but not granted.

**`/i_dont_remember_anything_about_my_microsoft_account`:**
You can recover the Microsoft account at https://account.live.com/ResetPassword.aspx using `louisgiuliani@hotmail.com`.

---

## Tools the MCP exposes

After auth, you can ask Claude Code things like:

- "List my Microsoft To Do tasks in the AVANTIR list."
- "What's on my Outlook calendar tomorrow?"
- "Search my Hotmail for emails from notaire@..."
- "Create a To Do task: 'Follow up with broker [name]' in the Real Estate list, due Friday."
- "Read OneDrive personal: find file [name]."
