# TDX in Claude Desktop: quick start for Windows

This adds TeamDynamix (TDX) tools to Claude Desktop, so you can ask Claude about tickets and other TDX records in plain language. Everything you do in TDX is done as you, under your own NetID.

## What you need

- Claude Desktop, already installed and signed in.
- Microsoft Edge or Google Chrome.
- A Cornell NetID with TDX access, and DUO on your phone.

You do not need administrator rights.

## Install

1. Open PowerShell (Start menu, type `powershell`, press Enter).
2. Paste this line and press Enter:

```
irm https://scjcb.dev/downloads/install.ps1 | iex
```

3. Wait while it runs. The installer prints what it is doing and ends by telling you to restart Claude if it is running. If it prints red text instead, copy it and send it to the person supporting you. The installer never closes Claude for you, so your open work is safe.
4. Quit Claude Desktop completely, then open it again. Closing the window is not enough, because Claude keeps running in the system tray:
   - Right-click the Claude icon in the system tray (click "Show hidden icons" if you do not see it).
   - Choose Quit.
   - Reopen Claude Desktop from the Start menu.
   - If Claude Desktop was not running, you can skip the quit steps and just open it.

## Sign in

In a new chat, type:

```
Sign in to TDX
```

An Edge or Chrome window opens on the Cornell login page. Sign in with your NetID and approve the DUO request. The window closes by itself and Claude confirms you are signed in. You have five minutes for each attempt. If a later question says your session expired, say "Sign in to TDX" again.

## Writing knowledge-base articles

Claude can also help you write knowledge-base articles: from your own words, a Word document, a PDF, an existing article or a resolved ticket. You always see a preview first, and nothing is created in TDX until you ask. The steps are in [`KB-AUTHORING.md`](./KB-AUTHORING.md).

## Three things to try

- What TDX tickets are assigned to me?
- Show me ticket 1234567.
- Which statuses can a ticket have in our TDX ticket queue?

Claude looks up the right TDX call and runs it. Use a real ticket number in place of 1234567. The first time a TDX tool runs, Claude Desktop asks for your permission; allow it.

## Updating

Updates never install on their own. When a newer version exists, the next answer from the TDX tools includes one line like "TDX MCP 0.2.1 is available". Reply:

```
update TDX
```

Then quit Claude Desktop completely and open it again (system tray, right-click the Claude icon, Quit).

## If something goes wrong

Say:

```
Run TDX diagnostics
```

Claude writes a small text file and tells you where it is. Send that file to the person supporting you. It contains no passwords or tokens. Claude's reply gives the file's full location; paste that location into the address bar of File Explorer.

## If Claude does not list TDX at all

1. Quit Claude Desktop completely (system tray, right-click the Claude icon, Quit) and open it again. Closing the window is not enough.
2. Still missing? Run the install line again in PowerShell, then quit and reopen once more. This is also needed if you started using a Claude mode or organization for the first time after installing.
3. Still missing? Send the person supporting you the file `%LOCALAPPDATA%\tdx-mcp\state\server.log`.

## Uninstall

Paste this line in PowerShell and press Enter, then quit and reopen Claude Desktop from the tray:

```
& ([scriptblock]::Create((irm https://scjcb.dev/downloads/install.ps1))) -Uninstall
```

Your saved TDX sign-in stays on your PC unless you ask the person supporting you to remove it.
