# TDX in Claude Desktop: quick start for Mac

This adds TeamDynamix (TDX) tools to Claude Desktop, so you can ask Claude about tickets and other TDX records in plain language. Everything you do in TDX is done as you, under your own NetID.

## What you need

- Claude Desktop, already installed and signed in.
- Google Chrome or Microsoft Edge.
- A Cornell NetID with TDX access, and DUO on your phone.
- A Mac with Apple silicon (M1 or newer). Intel Macs are not supported. To check, choose Apple menu, About This Mac; it should say Chip: Apple M...

## Install

1. Open the Terminal app (press Command and Space, type `Terminal`, press Return).
2. Paste this line and press Return:

```
curl -fsSL https://scjcb.dev/downloads/install.sh | zsh -f
```

3. Wait while it runs. You will see short progress lines, ending with the restart steps below and the words "Then say: Sign in to TDX". If you see an error instead, copy it and send it to the person supporting you.
4. Quit Claude Desktop completely, then open it again. The installer does not do this for you, and closing the window is not enough:
   - In the menu bar choose Claude, then Quit Claude.
   - Open Claude Desktop again.
   - If Claude Desktop was not open, you can skip the quit step and just open it.

## Sign in

In a new chat, type:

```
Sign in to TDX
```

A Chrome or Edge window opens on the Cornell login page. Sign in with your NetID and approve the DUO request. The window closes by itself and Claude confirms you are signed in. You have five minutes for each attempt. If a later question says your session expired, say "Sign in to TDX" again.

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

Then quit Claude Desktop completely and open it again (menu bar, Claude, Quit Claude).

## If something goes wrong

Say:

```
Run TDX diagnostics
```

Claude writes a small text file and tells you where it is. Send that file to the person supporting you. It contains no passwords or tokens. Claude's reply gives the file's full location; on a Mac, in Finder choose Go, then Go to Folder, and paste that location.

## If Claude does not list TDX at all

1. Quit Claude Desktop completely (menu bar, Claude, Quit Claude) and open it again. Closing the window is not enough.
2. Still missing? Run the install line again in Terminal, then quit and reopen once more. This is also needed if you started using a Claude mode or organization for the first time after installing.
3. Still missing? Send the person supporting you the file `~/Library/Application Support/tdx-mcp/state/server.log`.

## Uninstall

Paste this line in Terminal and press Return, then quit and reopen Claude Desktop:

```
curl -fsSL https://scjcb.dev/downloads/install.sh | zsh -f -s -- --uninstall
```

Your saved TDX sign-in stays on your Mac unless you ask the person supporting you to remove it.
