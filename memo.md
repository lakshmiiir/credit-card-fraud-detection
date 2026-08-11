**Fraud Detection Model: Summary for Fraud Operations**

**What this does**

I built a model that looks at credit card transactions and flags the ones that look like fraud. It learned from almost 285,000 past transactions, including 492 known fraud cases.

**How well it works**

Out of every 10 fraud cases, this model catches about 8 of them. And when it flags something as fraud, it's right about 94% of the time, so the review team won't be chasing false alarms very often.

In testing: it caught 79 out of 98 fraud cases, and only flagged 5 normal transactions by mistake (out of almost 57,000).

**Why I picked this cutoff**

I could have set the model to catch even more fraud, up to 90%, but I tried that and it caused a big problem: only 1 out of every 25 flagged transactions would have actually been fraud. That's way too many false alarms for a review team to deal with.

I care more about missing fraud than about the occasional false alarm, since a missed fraud case actually costs money. But 90% recall wasn't worth the tradeoff, since the false alarms would have overwhelmed reviewers. So I picked a cutoff that still catches most fraud (81%) while keeping false alarms low.

**What I'd do next**

Send flagged transactions to a human for review before anything is finalized. Fraud cases in this data tended to be for slightly higher dollar amounts, so it might help to review the higher-amount flagged transactions first.