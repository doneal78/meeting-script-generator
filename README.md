# Meeting Script Generator

A prep tool for running weekly client status calls and kickoff meetings without stumbling through them. You fill in what happened last week, what's happening this week, and it builds a script you can step through during the call — one phase at a time.

Live tool → https://doneal78.github.io/meeting-script-generator/

---

## The problem this solves

Going into a client call without a plan means improvising the whole thing — and that's where the "uh," "um," and "I don't have a lot to share" moments come from. This tool gives you a structure to prep before the call and a script to follow during it.

You don't have to memorize anything creative. You fill in what's actually happening, hit generate, and the script does the rest.

---

## How it works — the short version

1. Fill in your details — name, company, client, contact
2. Import last week's commitments from Copilot (see the prompt below)
3. Add this week's updates — wins, in-progress items, flags, what you need from the client
4. Generate the script and step through it during the call

---

## Step 1 — Your Details

Pretty straightforward. Your name, your company, the client name, who you're talking to, and whether it's a weekly call or a kickoff. These fill in throughout the script automatically including the column labels in Step 2.

---

## Step 2 — Last Call Review

This is where you bring in everything that was committed to in last week's meeting. The fastest way is to run the Copilot Prep Sorter prompt (full text at the bottom of this page), paste the output into the textarea, and hit **Import & route commitments**.

The tool reads the output and sorts everything automatically:
- Your company's items → left column (Your Side)
- Client's items → right column (Client Side)
- In-progress work → Step 3 In Progress section
- Background context → status notes textarea

Once it's imported, go through each item and mark it Done, In Progress, Blocked, or Pushed. That status shows up in Phase 3 of the script so you're not guessing what to say when you check in on last week.

If you don't have a Copilot output yet, you can add items manually using the + buttons.

---

## Step 3 — This Week's Updates

Five sections fill in what applies, skip what doesn't.

**Wins & completed items** anything that got wrapped up since last week. Closed Zendesk tickets, resolved issues, milestones hit. These are what you lead with in the status update.

**In progress** work that's underway. Add the item and the expected completion date. Every in-progress item needs a date "we're working on it" without a timeline doesn't hold up on a call.

**Flag items to bring up** — concerns or issues you need to raise. Add the concern and what you're doing about it. Don't leave this blank just because the news isn't great flagging something early is always better than explaining it later.

**What I need from the client** specific asks with dates. Not "whenever you can" an actual date. This feeds directly into Phase 5 of the script.

**Next call action items** commitments you're making on this call. Owner + item + date. After the call these go in your recap email and next week they come back as the "Last Call" items in Step 2. That's the whole loop.

---

## Generating the script

Hit **Generate script** and it builds a seven-phase script using everything you filled in.

Each phase has a few different types of content:

- **Green** — memorize this. These are the lines you drill before the call so they come out clean.
- **Orange** — pre-populated from your prep. Read it as-is or use it as your talking points.
- **Amber** — still needs to be filled in. Shows up when that section is empty.
- **Gray tip** — coaching for that specific phase. What to watch out for, how to avoid stumbling there.

The seven phases:
1. Opening
2. Agenda set
3. Last call review
4. Status update
5. What you need from the client
6. Next steps
7. Close

---

## The Copilot Prep Sorter Prompt

Run this in Copilot after every meeting. It works with formatted follow-up notes (the kind with Action Items and Next Steps sections) or a raw transcript it figures out which one you gave it.

Fill in your company and client name at the top, paste your content at the bottom, and run it.

---

```
YOUR COMPANY: [Enter your company name]
CLIENT: [Enter client name]

You are a meeting prep assistant. I will paste content below —
either formatted follow-up notes OR a raw meeting transcript.
Detect which it is and process accordingly.

IF FORMATTED NOTES (has sections like "Action Items" or "Next Steps"):
Read the Action Items and Next Steps sections. Sort each item
into the categories below.

IF RAW TRANSCRIPT (conversation between multiple speakers):
Read through the full conversation. Extract every commitment,
action item, and follow-up that was stated — look for phrases
like "I'll," "we'll," "I can," "let me," "going to," "I need,"
"can you," "will you." Then sort each item into the categories below.

CATEGORIES:
1. LAST CALL — [YOUR COMPANY]
   Items your company committed to. Mark: Done / In Progress / Blocked

2. LAST CALL — [CLIENT]
   Items the client committed to. Mark: Done / In Progress / Blocked

3. IN PROGRESS
   Ongoing work with an expected completion date. Use format:
   [Item] — targeting [date or TBD]

4. STATUS CONTEXT
   Background info or directional notes that help you speak
   confidently in the status update — not a checkable commitment.

5. SKIP
   Anything already covered, too vague to act on, or informational only.

RULES:
- Assign based on WHO made the commitment, not who it affects
- "I'll" / "we'll" / "let me" = the speaker made the commitment
- "Can you" / "will you" = the person being asked made the commitment
- Clean up language — concise, specific, no filler
- If a transcript: skip small talk and explanations unless they
  include a specific commitment or action
- Do NOT add details not in the content

OUTPUT FORMAT — use exactly this structure:

LAST CALL — [YOUR COMPANY]
[item] → [status]

LAST CALL — [CLIENT]
[item] → [status]

IN PROGRESS
[item] — targeting [date or TBD]

STATUS CONTEXT
[item]

SKIP
[item] — reason: [brief note]

---
CONTENT TO PROCESS:
[PASTE YOUR NOTES OR TRANSCRIPT HERE]
```

---

## What the output looks like

After running the prompt you'll get something like this copy the whole thing and paste it into the Step 2 textarea:

```
LAST CALL — Legato Security
Follow up with affected users to update OS/browser versions for Okta access → In Progress
Send Intezer and Torq API connector setup documentation → In Progress

LAST CALL — Lendistry
Complete onboarding questionnaire details for internal subnets and public-facing IPs → In Progress
Continue provisioning Okta access for remaining users → In Progress

IN PROGRESS
Engineering review of Rapid7 and CrowdStrike after full access confirmation — targeting approximately 7 days after access
Intezer and Torq integration work using provided documentation — targeting TBD

STATUS CONTEXT
Administrative onboarding is largely complete
Future meetings will focus on SIEM configuration, log ingestion, and alert tuning
Rapid7 SOAR capability confirmed and compatible with Intezer

SKIP
Shift weekly meetings toward technical discussions — reason: meeting format guidance
```

---

## The loop

This tool is designed to feed itself week over week.

- End of this call → read back the next call action items in Phase 6, confirm owners and dates
- Send the recap email with those items
- Next week → run the recap email through the Copilot prompt
- Paste the output into Step 2
- Everything lands where it belongs

The "next call action items" you lock in today become "last call" items next Friday. Nothing falls through.

---

## A few things worth knowing

- Check your Zendesk tickets before filling in Step 2 not the morning of the call, before you open the form. Knowing the real status on every item is what separates a clean update from a stumbling one.
- If a flag is resolved before the call, move it to Wins. That's a better story to lead with.
- The green memorize lines aren't there to make you sound scripted they're there so you don't have to construct sentences in real time while you're also managing the call.
- Send the recap within an hour. That's what keeps the loop working.
