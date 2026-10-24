# Onboarding patterns for products with few users

Load this when choosing how a step gets done, or when the founder asks for a specific pattern (a tour, a checklist, sample data). Each pattern says when it earns its place, when it doesn't, the smallest version worth building, and how it usually goes wrong.

Rule that sits above all of them: the pattern is only worth it if it gets the user to the aha moment sooner, on their own work. If it mainly makes the product look finished, skip it.

## Getting in

### Magic-link signup
- **Use when:** you want the fewest fields and the cheapest build. Email only, then a link.
- **Skip when:** users sign in on shared machines or locked-down work email that delays messages by minutes. Then offer a password or SSO alongside.
- **Smallest version:** one email field, one button ("Email me a sign-in link"), a screen that says which address it went to and how to resend.
- **Goes wrong:** the link lands in spam or quarantine and the user thinks the product is broken. Say "check spam or quarantine" on the waiting screen, and let them change the address.

### Google or Microsoft sign-in
- **Use when:** your customers' work email runs on one of them and they are used to clicking it. Ask two customers which they use before building both.
- **Skip when:** the buyer's firm blocks third-party sign-in, or you would only build it to look complete.
- **Goes wrong:** asking for more permission scopes than sign-in needs. Ask for calendar or drive access later, at the moment a feature needs it, with the reason on screen.

### Deferred verification
- **Use when:** almost always. Let them in, verify later.
- **Verify first only when:** the next action sends something to other people, touches money, or exposes someone else's data.
- **Goes wrong:** a hard wall three days later with no warning. Show a quiet banner from the start and block only the action that needs it.

### One routing question
- **Use when:** two kinds of user need clearly different first screens (the person who does the work versus the person who reviews it). One question, two or three answers, each changing what they see next.
- **Skip when:** the answer doesn't change the next screen. Then it is a survey; ask it on the setup call or after the aha moment.

## Setting up

### Founder-led setup call (concierge onboarding)
- **Use when:** under about 20 active accounts, the aha needs the customer's own data, or each account is worth an hour of founder time. This is the default for most B2B products at pilot stage.
- **Why it beats product changes this early:** with a handful of accounts, an hour of the founder's time per account is cheaper than a week of building, gets each customer to the aha moment for certain, and shows the founder exactly which steps to automate later. Install it for them while they watch; don't send a link and wait.
- **Smallest version:** a 30–45 minute call booked straight from signup. The founder shares their screen, loads the customer's real data from whatever they have (spreadsheet, export, a list read out loud), and gets them to the aha moment before the call ends. The customer does the last click themselves.
- **What to bring:** the customer's file sent the day before, the one workflow that produces the aha, and a notes sheet for every hesitation.
- **Stops when:** the same stall shows up in 3 calls (build the fix), or calls pass about 5 founder-hours a week (a planning line, not a law).
- **Goes wrong:** the founder demos for 40 minutes and the customer never touches it. Hand over control by minute 15.

### White-glove setup before first login
- **Use when:** the data load is long or fiddly and the customer has already said yes (a pilot, a paid start). The founder builds their account from their files; the first login opens on their own work, ready to use.
- **Smallest version:** "Your board is ready. Your 4 overdue clients are at the top." in the welcome email, with one link.
- **Goes wrong:** the customer never learns how anything got there and stalls when they add the next item. Leave one real item for them to add on the first login.

### Progressive setup
- **Use when:** setup has many settings but only one or two matter for the first result. Ask for each setting at the moment it is needed, with a sensible default.
- **Skip when:** a setting is truly required for the first result to be correct (a currency, a fiscal year end). Ask it up front, once, with a default filled in.

### Templates
- **Use when:** users start from a blank structure and most of them would build roughly the same one. Start them from the founder's own version of the job ("the close checklist I used for 4 years").
- **Skip when:** every customer's structure is genuinely different. Then load theirs on a setup call.
- **Goes wrong:** offering 12 templates. Offer one, plus "start blank".

### Paste or CSV import
- **Use when:** the aha needs a list the customer already keeps somewhere (clients, products, contacts). Paste from a spreadsheet beats a file upload; a file upload beats an integration.
- **Goes wrong:** strict column matching that rejects their real sheet. Accept messy input and let the founder clean it on the first few accounts.

### Integrations
- **Use when:** after the aha moment, once a customer asks for it by name, or once manual updates become the reason people leave.
- **Skip when:** it would sit before the aha moment. Approval flows, admin consent and sync delays turn step 2 into day 3.

## The first screens

### Empty states that teach by doing
- Every empty screen says what goes here in the customer's words, has one action that fills it, and accepts their real thing right there.
- Smallest version: a one-line explanation, one button, and an inline form for the first item. No illustration needed.
- Goes wrong: "Nothing here yet" with a button to a different page.

### Sample data
- **Use when:** real data takes days to get, and the aha is seeing how the product works (a report layout, a dashboard).
- **Skip when:** the aha depends on recognising their own work. A partner looking at a fake firm's blocked clients feels nothing.
- **Rules:** a clear "Sample" label on every sample item, one click to clear it all, and never mixed unlabelled with real data. No sample records built from a real customer's data.

### First-run checklist
- **Use when:** 3 or more required steps survive the cuts and they cannot be done in one sitting.
- **Skip when:** two steps or fewer remain. A checklist with two items is decoration.
- **Rules:** at most 5 items, each a doing action ("Add your first client"), dismissible, gone after the aha moment. The first item can be ticked only if the user really did it (signing up counts). No fake progress.

### Product tours (usually avoid)
- **Why avoid:** a tour explains the interface while the user wants to get their job done. People click through and remember little of it, and every tour step sits between them and the aha moment.
- **The one exception:** 2 or more of 5 watched users miss the same control after the empty state has been fixed. Then add one hint pointing at that control, shown once, at the moment they need it.
- **If the founder insists on a full tour:** at most 3 steps, skippable from the first one, never shown again, and tested against no tour with the same metric.

### Welcome video from the founder
- **Use when:** trust is the blocker (a new vendor asking for access to financial or customer data). A 60–90 second video, recorded by the founder, saying who they are, what happens next and what they will and won't see.
- **Skip when:** it's there to explain the interface. That job belongs to the empty states.

### Invites after the aha moment
- Ask for teammates right after the first result, with a reason in the user's terms ("Want your reviewer to see this board?"), not at signup.
- If the product only works with two people, let one person reach a solo version of the aha first, then invite.

## Finding where people stop

### Watching 5 sessions
1. Recruit people who match the target customer and have not seen the product. Pilot users who have seen a demo are primed; count them separately.
2. Give them the job, not instructions: "You've just signed up. Get last month's close onto it."
3. Ask them to think out loud. Say nothing unless they are stuck for more than about a minute; then ask "What are you looking for?"
4. Note every step where they pause, go back, ask a question or give up, with the screen and their words.
5. Afterwards, count by step. 2 or more of 5 stalling on a step: fix it next. 1 of 5: note it.

### Talking to 3 who left
- Ask within a week of them leaving, in a short personal note from the founder. Ask for 10 minutes, not a survey.
- Questions: "What were you hoping to get done when you signed up?", "Where did you stop?", "What did you do instead?", "What would have had to be true for you to keep going?"
- Their "what did you do instead" is the real competitor for onboarding. Usually it is the spreadsheet.

### Fresh-account walk
- Every two weeks the founder signs up with a new email, on a phone and on a laptop, times each step, and writes down every place they had to think. Founders stop seeing their own friction within a month.
