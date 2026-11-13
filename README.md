# TDX tools for Claude Desktop

This adds TeamDynamix (TDX) tools to Claude Desktop for IT staff at Cornell. You ask Claude about tickets, assets and knowledge-base articles in plain language, and Claude looks up the right TDX call and runs it. Everything is done as you, under your own NetID.

This repository holds the signed release packages and the installers. It is a beta: it is not an official Cornell or TeamDynamix product, and the source code is in a separate, private repository.

## What you need

- Claude Desktop, already installed and signed in.
- Google Chrome or Microsoft Edge.
- A Cornell NetID with TDX access, and DUO.
- A Mac with Apple silicon (M1 or newer), or a Windows PC (x64). Intel Macs are not supported.

You do not need administrator rights, Node or git.

## Install

**Mac.** Open Terminal, paste this line and press Return:

```
curl -fsSL https://tdx-mcp-claude.vercel.app/downloads/install.sh | zsh -f
```

**Windows.** Open PowerShell, paste this line and press Enter:

```
irm https://tdx-mcp-claude.vercel.app/downloads/install.ps1 | iex
```

Then quit Claude Desktop completely and open it again. The installer never closes Claude for you, and closing the window is not enough:

- Mac: in the menu bar choose Claude, then Quit Claude.
- Windows: right-click the Claude icon in the system tray, then choose Quit.

## Sign in

In a new chat, type:

```
Sign in to TDX
```

A Chrome or Edge window opens on the Cornell login page. Sign in with your NetID and approve the DUO request. The window closes by itself. You have five minutes for each attempt. If a later answer says your session expired, say "Sign in to TDX" again.

## Things to try

- What TDX tickets are assigned to me?
- Show me ticket 1234567. (Use a real ticket number.)
- Which statuses can a ticket have in our TDX ticket queue?

The first time a TDX tool runs, Claude Desktop asks for your permission.

## Writing knowledge-base articles

Claude can help you write a knowledge-base article from your own words, a Word document, an existing article or a resolved ticket.

1. Say "Start a knowledge-base draft called ..." or "Make a knowledge-base draft from this Word document" and give the file's full path.
2. Ask for changes in plain words, and add screenshots if you want them.
3. Say "Show me the preview." A page opens in your browser showing the article exactly as it will be sent.
4. Say "Create the article in TDX", then "Submit it for review."

A draft is a folder on your computer, in `Claude/TDX KB Drafts` under your home folder. Nothing reaches TDX until you ask Claude to create, update, submit or publish an article.

## Updating

Updates never install on their own. When a newer version exists, the next answer from the TDX tools says so in one line. Reply:

```
update TDX
```

Then quit Claude Desktop completely and open it again. To go back to the version you had before, ask Claude to roll back the TDX tools.

## If something goes wrong

Say:

```
Run TDX diagnostics
```

Claude writes a small text file and tells you where it is. Send that file to the person who gave you this link. It contains no passwords or tokens.

If Claude does not list the TDX tools at all:

1. Quit Claude Desktop completely and open it again.
2. Still missing? Run the install line again, then quit and reopen once more. This is also needed if you started using a different Claude mode or organization after installing.
3. Still missing? Send the log file: `~/Library/Application Support/tdx-mcp/state/server.log` on a Mac, `%LOCALAPPDATA%\tdx-mcp\state\server.log` on Windows.

## Uninstall

Mac:

```
curl -fsSL https://tdx-mcp-claude.vercel.app/downloads/install.sh | zsh -f -s -- --uninstall
```

Windows:

```
& ([scriptblock]::Create((irm https://tdx-mcp-claude.vercel.app/downloads/install.ps1))) -Uninstall
```

Then quit and reopen Claude Desktop. Your saved TDX sign-in stays on your computer unless you ask for it to be removed.

## What is in a release

Each [release](https://github.com/merpuya/tdx-mcp-releases/releases) holds these files. You do not need to download any of them by hand; the install lines above and the built-in updater do it.

| File | What it is |
|------|------------|
| `install.sh` | The Mac installer |
| `install.ps1` | The Windows installer |
| `tdx-mcp-<version>-darwin-arm64.tar.gz` | The full package for Apple-silicon Macs, with its own copy of Node |
| `tdx-mcp-<version>-win-x64.zip` | The full package for Windows, with its own copy of Node |
| `tdx-mcp-<version>-payload.zip` | The tools alone, used by the built-in updater |
| `latest.json` | The release manifest: the version, and the size and SHA-256 checksum of each package |
| `latest.json.sig`, `latest.json.sig.der` | The signature of the manifest, in two encodings |

## How downloads are checked

- `latest.json` is signed with an ECDSA P-256 key. The matching public key is built into the installers and into every installed copy.
- The installer and the updater check that signature first, then check each package against the size and checksum in the manifest. A file that fails either check is never unpacked or run, and nothing on your computer is changed.
- The install line itself is protected by HTTPS only. Everything it downloads after that is checked as above.

## What it changes on your computer

- The tools are installed for your user account only: `~/Library/Application Support/tdx-mcp` on a Mac, `%LOCALAPPDATA%\tdx-mcp` on Windows.
- One `tdx-mcp` entry is added to Claude Desktop's configuration file. Uninstalling removes it.
- Your TDX sign-in is saved on your own computer. No password or token appears in the chat.
