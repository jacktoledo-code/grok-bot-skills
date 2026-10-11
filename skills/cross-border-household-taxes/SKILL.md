---
name: Cross-border household taxes
description: >-
  Use this when a family that lives in one country but has accounts, income, or
  tax history in another (e.g. US residents with Canadian accounts) needs to
  organize docs, work with accountants in both countries, and review the return
  before filing.
---
# Cross-border household taxes

Goal: get a household's tax year from scattered documents to an accountant-approved, reviewed, filed return, with one place for every document and every answer. The assistant organizes and checks; licensed accountants prepare and file. Never give final tax advice yourself.

## How the AI agent runs it
The household talks to one assistant (e.g. a Grok Bot named for household finances). The assistant works through connectors and keeps the human in charge of anything that leaves the house.

**Connections (read-first)**
- Email: search accountant threads, find tax forms and statements, draft replies.
- Cloud drive: create folders, rename and file PDFs, keep notes, upload to the accountant's shared folder.
- Bank / aggregator links (read-only): balances and transactions for account tables and payments.
- Accountant portals and tax-authority sites (e.g. Intuit Link, IRS, CRA): the assistant opens them in its own browser; the user types passwords and 2FA codes into a secure form or takes over the screen.
- Calendar: deadlines (extension, FBAR, accountant meetings).

**Communication loop (every accountant email)**
1. Watch: on request or on a schedule, search email for new messages from each accountant.
2. Summarize: tell the user in plain words what was sent, what is asked, and any deadline or amount.
3. Gather: answer from the drive, notes, and connected accounts first; ask the user only for what only they know.
4. Draft: write the reply in the user's voice, threaded on the original, cc'ing the spouse when relevant. Show it as a draft card.
5. Send: only when the user presses Send (or explicitly says send this draft). Never auto-reply.
6. Log: record the question, answer, and date in `<Year>_Tax_Answers.md`; add any follow-up as a to-do.
7. Relay between accountants: when one accountant's result feeds the other, forward the exact figures and source, after user approval.

**Organizing loop (every new document)**
1. Find it (email attachment, portal download, user photo, Downloads folder).
2. Identify form type, person, issuer, year; check for duplicates.
3. Rename `<Year>_<FormType>_<Person>_<Issuer>.pdf` and file it in the right year/country folder; unsure items go to `_Inbox/`.
4. Update the checklist (have / requested / N/A) and the foreign-account table if it's a statement.
5. Upload to the accountant's shared folder only when the user approves that packet.

**Review loop (preparer drafts)**
Download drafts from the portal, run the Step 5 checks below, save a review note, and turn real gaps into a short question email for the user to approve.

**Cadence**
- Weekly check of accountant inboxes during tax season; daily in the last two weeks before a deadline.
- Reminder routines for extension/FBAR deadlines and unpaid invoices.
- Status updates to the user at milestones (docs complete, draft received, filed), not every step.

## 1. Set up the home (once)
- One shared cloud folder both spouses can open. Suggested layout:
  - `Taxes_<Country A>/<Year>/` and `Taxes_<Country B>/<Year>/`: source PDFs
  - `Accounts_<Country B>/`: foreign account statements (year-end and highest-balance)
  - `Notes/<Year>_Tax_Answers.md`: every accountant question and answer, plus a Filed table (date, refund/balance due, confirmation)
  - `_Inbox/`: unsorted downloads until filed

## 2. Build the document checklist
Ask for people, employers, and every account in every country, then list what's expected per person:
- Wages: W-2 / T4 (and equity or RSU slips: 1099-B, supplemental statements)
- Investment income: 1099-DIV/INT/B; NR4 / T5 / T5008 for Canadian accounts
- Retirement/pension/registered plans (RRSP, LIRA, TFSA, RESP, DCPP, 401k)
- Prior-year returns from both countries
- Residency facts that drive filing status (visa type, move dates, days in each country)
Mark each item: have / requested / N/A. Search email and drive before asking the user.

## 3. Foreign account reporting
For every non-domestic account record: owner, institution, type, country, last 4 only, open/closed, max and 12/31 value per year, currency, income received. This table feeds FBAR (FinCEN 114), Form 8938, and preparer questionnaires. Gather a year-end statement for each. Include equity-plan brokerages administered from another country; ask the preparer whether each is reportable rather than deciding yourself.

## 4. Work with the accountants
- One email thread per accountant and topic; all messages drafted for user approval.
- When one accountant's numbers feed the other's (e.g. foreign tax actually owed for a foreign tax credit), forward the exact figures and say which number to use (final tax owed, not total withheld).
- Track fees, deadlines, and authorizations (e.g. adding a representative on a tax portal) as to-dos.

## 5. Review the draft return before approving
- Filing status, dependents, and credits match the household (e.g. no dependent credits for kids without a tax ID).
- Wages and withholding match each W-2 / slip.
- Foreign tax credit uses the final foreign tax figure; carryover noted.
- Every account in the foreign-account table appears on FBAR/8938 with right owner and value, or the preparer explains why not.
- Equity compensation isn't taxed twice (adjusted cost basis).
- Refund or balance due matches the preparer's email.
Write findings to `Notes/<Year>_Return_Review.md`.

## 6. After filing
Fill the Filed table, save final returns and confirmations, and carry open items (carryovers, accounts to close, estimated payments) into next year's checklist.

## Privacy and safety rules
- Last-4 only; never store full account numbers, SINs/SSNs, or passwords in notes or chat.
- The user enters sign-ins and 2FA codes directly.
- Nothing goes to an accountant, tax authority, or bank without the user pressing Send or approving.
- The assistant never pays invoices or taxes itself unless the user explicitly asks.
