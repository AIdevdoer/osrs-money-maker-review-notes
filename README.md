# Reviewing an OSRS Money-Making Method Before It Can Rank

This is the review checklist I use before a method is allowed into a live recommendation catalog. It is not a list of the “best” methods. It is a small provenance and maintenance protocol.

The working example is [OSRS Money Maker](https://osrsmoneymakers.com/), an independent recommender that filters methods by account settings and recalculates profit from current Grand Exchange prices.

## 1. Keep the source attached to the method

Every method record should retain the following details.

- a public source URL;
- the source revision ID when one is available;
- the date the method details were checked;
- the next review due date;
- a short note describing what was verified.

A title and a GP/hour number are not enough. Requirements, steps, action rate, inputs, outputs, risks, and the normal interaction cadence can all go stale independently.

## 2. Separate reviewed facts from live values

I treat these as two data layers.

The reviewed layer contains the method structure. It covers which skill levels are required, whether it is Members-only, whether it enters the Wilderness, the expected actions per hour, and the item quantities for one action.

The live layer contains current market prices. Inputs use the instant-buy side. Outputs use the instant-sell side after Grand Exchange tax. A missing required price removes the method from that calculation instead of becoming zero.

This separation makes failures easier to explain. A method can be correctly documented but temporarily unpriceable. It can also have complete price data while its source review is overdue.

## 3. Give a review date real consequences

`reviewDueAt` should not be decorative metadata. When a method is due for review, it moves out of the active catalog until its details are checked again. A separately blocked method is also withheld.

At the time of this note, the public health endpoint reports 104 active methods, zero due for review, and zero blocked. That is a snapshot, not a permanent claim. The point of the endpoint is to make drift visible.

```json
{
  "catalogSize": 104,
  "activeCatalogSize": 104,
  "reviewDueCount": 0,
  "blockedCount": 0,
  "catalogVerifiedAt": "2026-08-14"
}
```

## 4. Keep eligibility ahead of ranking

Before profit sorting, a method must pass the player's actual constraints.

- world access, either F2P or Members;
- Wilderness allowed or excluded;
- preferred effort level;
- loaded skill requirements;
- enough starting capital;
- complete market data;
- positive modeled profit.

Only the survivors are ranked. The product shows at most three. A short result list is allowed; the system should not weaken a gate just to fill a layout.

## 5. Expose what the model does not know

The estimate does not include Grand Exchange buy limits, slow fills, travel time, competition, mistakes, deaths, or the user's real clicking speed. Those belong in visible risk notes, not hidden fine print.

My final manual test is always a small round trip. I buy a limited batch, complete the loop, sell the output, and calculate profit from actual trades. If the method only works when every assumption is perfect, it should not be described as dependable.

## Why keep this as a checklist?

Money-making pages often age badly because the visible number updates while the method description does not. A review ledger gives both halves of the estimate a clock. It also creates a clean reason to remove a method temporarily instead of leaving questionable data in production.

OSRS and RuneScape are trademarks of Jagex. This repository is independent and is not endorsed by Jagex.
