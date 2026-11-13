# Writing knowledge-base articles with Claude

Claude can turn what you tell it, a document, an existing article or a resolved ticket into a draft knowledge-base article. You read the draft and a preview, and only when you say so does Claude create the article in TDX and send it for review.

Status: beta. Writing, importing a Word document, previewing, creating, updating, submitting and publishing have all been run for real on a Mac; drafts, pictures, the preview and a Word import have been run on Windows. Some paths have not been tried yet, so tell us what you see; "Limits to know about" at the end lists them.

## Before you start

1. Make sure you are signed in to TDX. If you are not sure, say "Sign in to TDX" (see the quick start for your computer).
2. Know where your drafts live. Each draft is a folder in your drafts folder:
   - Mac: `~/Claude/TDX KB Drafts`
   - Windows: `C:\Users\<you>\Claude\TDX KB Drafts`
3. Claude opens a draft's folder for you when it makes the draft. You can open it yourself at any time.

Nothing reaches TDX until you ask Claude to create, update, submit or publish an article. Writing, adding pictures and previewing only change files on your computer.

## Write your first article

Say each of these to Claude, one at a time.

1. "Start a knowledge-base draft called How to reset a NetID password." Claude makes the draft and opens its folder.
2. Tell Claude what the article should say, in your own words. For example: "Write it for staff. Steps: open the NetID page, choose Reset, answer the questions."
3. Read what Claude wrote. Ask for changes in plain words: "Make step 2 shorter." "Add a warning about the 24 hour lockout."
4. Add screenshots if you want them (see "Adding screenshots" below).
5. Say "Show me the preview." A page opens in your browser (see "The preview").
6. Say "Which category should this go in?" Claude lists the categories and who can see each one. Choose one and say so.
7. When you are happy, say "Create the article in TDX." Claude creates it, reads it back to check that the text and pictures arrived, and gives you a link.
8. Open the link and compare it with the preview.
9. Say "Submit it for review." The article now appears in TDX's list of articles awaiting review, where the knowledge-base publishers find it.

You can stop after any step. The draft stays in your drafts folder.

## Starting from something you already have

Say what you have and where it is. Claude tells you about anything it could not bring in. Read those notes.

### A Word document

1. Say "Make a knowledge-base draft from this Word document" and give the full path, for example `/Users/<you>/Documents/VPN guide.docx` on a Mac or `C:\Users\<you>\Documents\VPN guide.docx` on Windows.
2. The text and pictures come in, and a copy of the file is kept in the draft's `source` folder.

Some Word tables come through as raw HTML that looks odd in the draft but displays as a table in the article. Check tables in the preview.

### A Google Doc

1. In Google Docs choose File, Download, Microsoft Word (.docx).
2. Follow the Word document steps with the downloaded file.

### A PDF

1. Attach the PDF to your chat with Claude.
2. Say "Write a knowledge-base article from this PDF."

PDFs come in as text only. Pictures in the PDF are not copied. Add the screenshots you need yourself.

### An article already in TDX

1. Say "Make a draft from knowledge-base article 12345" (use the real number).
2. Claude copies the text, pictures, title, summary, tags and category into a draft and links the draft to the article, so you can update that article later. The draft keeps the article's category even when Claude cannot read the category list; it then says it could not tell who can see that category. An update never changes the category anyway.
3. If you already have a draft for that article, Claude tells you and does not make another. Say "make a second draft" only if you want a fresh copy of what is in TDX now.

### A resolved ticket

1. Say "Write a knowledge-base article from ticket 1234567" (use the real number).
2. Claude makes a draft with a Problem section from the ticket's description and a Resolution section from the technician's last public reply. The draft's folder is named `ticket-<number>` (for example `ticket-1234567`), never after the ticket's title, because a title can name a person.
3. Claude leaves out the requester's name and contact details. Claude is also asked to remove names, NetIDs, email addresses, phone numbers and device identifiers from the title and the text before it shows you the draft, but the draft folder opens straight away and its first version still has the ticket's own text. Read it before sharing it, and before you go on.
4. Private notes on the ticket are left out. Say "include the private notes" if you want them, and they are marked as private.
5. Screenshots inside a ticket are not copied. Add them yourself.
6. After the article is created, Claude offers to link the ticket to it. Say yes only if you want that. If the ticket already points at a different article, Claude asks before replacing the link.

## Adding screenshots

Do either of these.

- Drop the picture files into the draft's `images` folder, then tell Claude "I added a screenshot called login.png to the draft, put it after step 2."
- Tell Claude the full path of the file: "Add /Users/<you>/Desktop/login.png after step 2" on a Mac, or "Add C:\Users\<you>\Pictures\login.png after step 2" on Windows.

What works:

- PNG and JPEG are made smaller if they are wider than 1200 pixels. Your original is always kept, in a hidden `images\.orig` folder inside the draft.
- BMP and TIFF are turned into PNG.
- GIF and WebP are kept as they are. "Kept as it is" means Claude does not shrink them, so an animated GIF still moves, and a big one still counts fully against the size limit.
- Files over 40 MB are refused. Shrink them in an image editor first.
- Pictures of more than 50 megapixels (for example 10,000 by 5,000 pixels) are refused before they are opened, wherever they come from: a file you add or drop in, a Word document, or an article in TDX. Claude gives the size; save a smaller copy and add that.
- A file you drop into the `images` folder whose name has spaces or capital letters is renamed to a safe name, for example the default screenshot name `Screenshot 2026-11-12 at 10.15.32.png` becomes `screenshot-2026-11-12-at-10-15-32.png`. Claude tells you the new name; use that one in the article. (Markdown does not see a picture whose name has a space in it.)
- Anything else, and shortcuts or links to pictures, are refused or skipped, and Claude says so.

Phone photos may appear rotated. If one does, turn it the right way up in a photo editor and add it again. Claude never overwrites a picture you added earlier: the old one is renamed with `.superseded` in `images\.orig`.

Give each picture a short description when you can. The checks warn about pictures without one.

## The preview

Say "Show me the preview." A page opens in your browser. It is only on your computer; nobody else can see it. It updates by itself when the draft changes, as long as the tab stays open.

The page shows, from the top:

- The title, the category, and the summary.
- A bar showing how big the article is against the size limit, split into text and pictures.
- The pictures, largest first.
- Image notes: what was done to each picture (shrunk, kept as it is, converted).
- Checks. A red "blocked" check must be fixed before the article can be created. A warning is for you to read. Two blocked checks are about pictures that would not reach the article: a picture written in the text that Claude did not recognise (usually because its file name has spaces), and a picture in raw HTML (`<img src="...">`) that points at a file instead of being embedded. Ask Claude to add the picture the normal way.
- The article itself.
- If an earlier create's outcome was never confirmed, a "Create pending" line (see "If something goes wrong").

The page says "Approximate layout. The text and images are exactly what will be sent." The fonts and spacing are not the portal's. What you read here is what goes to TDX.

Claude also removes active content (scripts, forms and the like) from every article. If it removed something, the checks say what.

## When the article is over the size limit

TDX stores an article as one piece, and a very large article can fail. Claude keeps articles under 1,000,000 bytes (about 1 MB). Almost always the pictures are the cause.

If the preview says the article is over the limit, it cannot be created. Try these, in this order:

1. Say "Make the pictures smaller." Claude shrinks them again from your originals, for example to 900 pixels wide.
2. Remove pictures you do not need, or split the article into two shorter ones.

GIFs and WebP files are never shrunk, so a large one has to be replaced or removed.

## Choosing a category

Say "Which category should this go in?" Claude lists the categories with who can see each one: public, or internal. Public means TDX marks the category as open to people outside the support staff; whether a reader has to sign in to the portal first is a portal setting, so check in TDX if that matters. Some say access "may be limited to specific groups". TDX does not tell us which groups, so if the audience matters, check that category's permissions in TDX.

Claude never picks a category for you. It tells you who will be able to see the article and waits for you to confirm.

## Creating, then submitting for review

1. Say "Create the article in TDX." Claude checks the draft first and refuses if a blocked check is open. The new article belongs to you and starts as Not Submitted and not published.
2. Claude reads the article back from TDX and tells you the text and pictures matched. Open the link and look.
3. Say "Submit it for review." Its status becomes Submitted and it shows in the list of articles awaiting review.

Submitted is the normal last step for an author. If you say "publish it" and your account cannot, Claude tells you, leaves the article as it was, and you ask a publisher.

## Changing an article that is already in TDX

1. Start from the article ("Make a draft from knowledge-base article 12345") or use the draft you created it from.
2. Change the draft and check the preview.
3. Say "Update the article in TDX."

Claude may stop and ask about one of three things. It changes nothing until you agree to that thing.

- Someone else changed the article in TDX since your draft last matched it. Claude lists what changed. If you go ahead, your draft replaces their change. If you want to keep their change, copy it into your draft first. Claude says the same if it has no record of the article to compare against. If an earlier update from this draft could not be confirmed, the change it lists may be your own earlier update: Claude says so.
- The article is published, so your change is live as soon as it is saved.
- Your draft has fewer pictures than the article has now, for example because an import could not bring some in. Going ahead removes the others from the article.

An update does not change the article's category, status or published state. After saving, Claude reads the article back to check it. If you ask for an update and for a submit or publish at the same time, Claude does one and then the other, never both at once; the second may say "another action on this article is still running; try again in a moment".

## If something goes wrong

- "I could not tell whether TDX created the article." TDX gave an error or no answer, so the article may or may not exist. The draft is marked "create pending", and if you ask to create it again Claude stops and says a create was sent at a given time and never confirmed. What to do:
  1. Ask Claude to look for the article in TDX. A new article is Not Submitted and not published, so the portal's search may not show it; Claude can search the knowledge base for unpublished articles too.
  2. If it is there, Claude makes a fresh draft from it. Carry on ONLY in that new draft. Leave the old draft alone: never create from it again.
  3. If it is not there, tell Claude so, and Claude sends it again.
  4. If the draft came from a ticket, ask Claude to link the ticket to the article afterwards; that offer is lost along the way.
- "TDX accepted the article but did not return its id" and "I could not link the draft to it": the same advice. In the second case the article certainly exists, and Claude gives its link.
- "I could not tell whether TDX saved the change" (an update): look at the article in TDX. If it shows your change, it was saved. Your next update may then stop and list your own change as "changed in TDX"; Claude says it may be from an earlier update from this draft. If the article shows what you expect, agree to go ahead.
- "The article was not created." TDX clearly refused. Nothing was made, and Claude gives the reason.
- Anything else odd: say "Run TDX diagnostics". Claude writes a small text file with no passwords or tokens and tells you where it is. Send that file to the person who supports you, with the name of your draft folder.

Your drafts are plain folders. You can copy a draft folder to send it to your supporter.

## Limits to know about

- PDFs come in as text only.
- Screenshots inside a ticket are not copied.
- Some Word tables come through as raw HTML.
- Phone photos may appear rotated.
- The preview's layout is approximate.
- Not yet tried for real (as of November 2026):
  - a Claude Desktop chat (so far everything was run from the Code tab);
  - making a draft from a ticket, including TDX's real wording for the automatic entries in a ticket;
  - making a draft from an article already in TDX, including downloading its pictures;
  - linking a ticket to an article;
  - "publish it" from an account that is not allowed to publish;
  - on Windows, creating, updating, submitting or publishing an article, and pictures that a document refers to by a network path or a drive letter (tested only with Windows path rules on a Mac).

## Reference: the nine tools

You do not need these names. They are here for whoever supports you.

| Tool | What it does |
|---|---|
| `tdx_kb_categories` | Lists the categories with their ids and who can see each. Reads only. |
| `tdx_kb_draft_new` | Starts a draft from a title, a Word, Markdown or HTML file, an existing article, or a ticket. |
| `tdx_kb_draft` | Lists, reads, writes and sets the fields of a draft, shows its status, adds and shrinks images, imports a file. |
| `tdx_kb_preview` | Opens the preview page for a draft. |
| `tdx_kb_create_article` | Creates the article in TDX from a draft and reads it back. |
| `tdx_kb_update_article` | Sends a linked draft to its article, with three confirmations. |
| `tdx_kb_submit_article` | Moves an article from Not Submitted to Submitted. |
| `tdx_kb_publish_article` | Approves and publishes an article, for accounts that may. |
| `tdx_kb_link_ticket` | Links a ticket to an article. |
