# Meeting Script Generator

A prep tool for security services weekly status calls and kickoff meetings. Fill in your details, import last week's commitments from Copilot, add this week's updates, and generate a structured script you can step through one phase at a time during the call.

**Live tool:** https://doneal78.github.io/meeting-script-generator/

---

## What It Does

The tool solves one specific problem: going into a client call unprepared and stumbling through updates. Instead of improvising, you prep your content beforehand and the tool generates a phase-by-phase script with memorized lines, pre-populated updates from your prep, and coaching tips for each section.

It has two modes — **prep** (before the call) and **script** (during the call). Prep is where you fill things in. The script is what you step through one phase at a time when you're live.

---

## Full Workflow

### Before the call — three steps

**Step 1 — Your Details**

Fill in your name, your company, the client name, primary contact, and meeting type. These populate throughout the script automatically. The client and company names also label the commitment columns in Step 2.

**Step 2 — Last Call Review**

This is where you import what was committed to in last week's meeting. The fastest way to do this is with the Copilot Prep Sorter prompt (see below). Paste the full Copilot output and hit **Import & route commitments** — the tool reads the output and routes each item to the correct column automatically.

- Items from your company's section → **Your Side** column
- Items from the client's section → **Client Side** column
- IN PROGRESS items → the In Progress section in Step 3
- STATUS CONTEXT items → the status notes textarea in Step 3

Once items are imported, review them and mark each one:
- **✓ Done** — completed since last call
- **⏳ In progress** — still underway
- **✗ Blocked** — something is preventing it
- **→ Pushed** — delayed to a future call

**Step 3 — This Week's Updates**

Five sections to fill in manually. These directly populate Phases 3–6 of the generated script.

| Section | What goes here | Goes into |
|---------|---------------|-----------|
| Wins & completed items | Completed Zendesk tickets or resolved tasks the client should know about | Phase 4 — Status update |
| In progress | Active work items with expected completion dates | Phase 4 — Status update |
| Flag items to bring up | Concerns or issues — include what you're doing about it | Phase 4 — Status update |
| What I need from the client | Specific asks with due dates | Phase 5 — Needs from client |
| Next call action items | Commitments you're making ON THIS CALL — owner + item + date. After the call these go in your recap email and become next week's "Last Call" items | Phase 6 — Next steps |

**Generate your script**

Hit **Generate script**. The tool builds a 7-phase script:

1. Opening
2. Agenda set
3. Last call review
4. Status update
5. What I need from the client
6. Next steps
7. Close

Each phase shows:
- **Green** — memorize this line word for word
- **Orange** — pre-populated from your prep, ready to deliver
- **Amber** — fill this in manually (shown when the section is empty)
- **Gray** — coaching tip for that phase

### During the call

The script is one long view you can scroll through, or use your browser's print/PDF function to save it before the call.

---

## The Copilot Prep Sorter Prompt

Use this prompt in Copilot after every meeting. It accepts either **formatted follow-up notes** (with Action Items and Next Steps sections) or a **raw meeting transcript**. It figures out which one it's looking at and processes accordingly.

Copy the full prompt below, fill in your company and client name at the top, paste your notes or transcript at the bottom, and run it.

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
   Background info, directional notes, or context that helps
   you speak confidently in the status update but isn't a
   checkable commitment.

5. SKIP
   Anything already covered, too vague to act on, or informational only.

RULES:
- Assign based on WHO made the commitment, not who it affects
- "I'll" / "we'll" / "let me" = whoever is speaking made the commitment
- "Can you" / "will you" = the person being asked made the commitment
- Clean up language — concise, specific, no filler
- If a transcript: ignore small talk, pleasantries, and explanations
  unless they contain a specific commitment or action
- Do NOT add details not in the content

OUTPUT FORMAT — use exactly:

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

## What the Prompt Output Looks Like

After running the prompt, Copilot returns something like this:

```
LAST CALL — Legato Security
Follow up with affected users to update OS/browser versions for Okta access → In Progress
Send Intezer and Torq API connector setup documentation → In Progress

LAST CALL — Lendistry
Complete onboarding questionnaire details for internal subnets and public-facing IPs → In Progress
Continue provisioning Okta access for remaining users → In Progress

IN PROGRESS
Engineering review of Rapid7 and CrowdStrike after full access confirmation — targeting approximately 7 days after access completion
Intezer and Torq integration work using provided documentation — targeting TBD

STATUS CONTEXT
Administrative onboarding is largely complete
Future meetings will focus on SIEM configuration, log ingestion, and alert tuning
Rapid7 SOAR capability is confirmed and compatible with Intezer

SKIP
Shift weekly meetings toward technical discussions — reason: meeting format guidance
```

Copy the full output, paste it into the Step 2 textarea in the tool, and hit **Import & route commitments**.

---

## The Closed Loop

The tool is designed so each call feeds directly into the next one.

1. End of call — you read back the **Next Call Action Items** (Phase 6) and confirm owners and dates
2. Send your recap email with those items as action items
3. Next week — run the recap email through the Copilot prompt
4. Paste the Copilot output into the tool
5. Everything lands in the right place automatically

The "Last Call" items this week become the starting point for next week's call prep.

---

## Tips

**Before every call**
- Fill in Step 2 and Step 3 before opening the call
- Check your Zendesk tickets for the latest status on every open item — "I believe I sent it" is not a status
- Know the dates on every in-progress item before you dial in

**During the call**
- Step through the script one phase at a time
- Green lines are memorized — read them directly if you need to
- Orange sections are pre-populated from your prep — they're ready to deliver
- The coaching tip in each phase is there to keep you from stumbling in that specific moment

**After the call**
- Send the recap email within an hour
- Include every action item from Phase 6 with the owner and date
- That email is what feeds the Copilot prompt for next week's prep
