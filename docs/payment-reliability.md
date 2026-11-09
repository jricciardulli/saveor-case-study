# Payment and entitlement reliability

## Problem

A completed purchase and permission to use a product are related but separate states. Native receipt validation, Stripe lifecycle events, stored subscription records, enterprise relationships, and cached client UI can disagree. A valid customer can appear unpaid if the provider state has not been reconciled; stale cached access can also outlive a revoked subscription.

Specific failure modes addressed in the implementation include restored Apple receipts requiring validation, lifetime products without an expiry date, scheduled cancellations that remain paid through the period end, and provider-backed subscriptions whose local records need refreshing. These are implementation-level findings, not a claim that each caused a measured production incident.

## Decision

Use a server entitlement decision that accounts for account status, subscription lifecycle, and active enterprise access. The selected inventory matters: access associated with an inventory owner must not be confused with an invitee’s personal consumer plan.

| Layer | Responsibility |
| --- | --- |
| Native purchase integration | Register platform products and send approved transactions, including restored app receipts, for validation. |
| Provider synchronization | Refresh subscription status and paid-through dates from the relevant provider. |
| Server entitlement evaluation | Decide access using current account, consumer, and enterprise state. |
| Client navigation | Use matching cached access for responsiveness while revalidating in the background. |
| Protected actions | Await a fresh verification; distinguish unavailable verification from authoritative denial. |

Stripe lifecycle synchronization updates local subscription and account state transactionally. Scheduled cancellation preserves access through the paid period; terminal states and elapsed entitlement periods revoke it. Lifetime products require product-aware handling rather than assuming every purchase is a recurring subscription.

A reconciliation worker selects provider-backed records that are near expiry, unvalidated, or stale. It supports targeted selection as well as bounded batches. Recurring Stripe subscriptions are included; lifetime purchases do not go through recurring-subscription retrieval. Apple purchase ownership tracking prevents a restore from silently transferring the same purchase to a different account.

## Repairing existing state

The repair mechanism is provider reconciliation: select an affected record, retrieve authoritative provider state, synchronize the local record, then verify the resulting entitlement. A per-record failure is reported while other records can continue. This provides a path to repairing stale existing records as well as keeping future records current.

A completed production repair campaign, the original incident timeline, and the number of accounts restored are **not established by this repository**. Payment-event history backfills are also distinct from restoring access; neither should be presented as proof of the other.

## Tradeoffs

A fresh server check adds latency and can temporarily block a legitimate paid action during an outage. The client therefore separates browsing from protected actions: cached navigation can remain responsive, while a protected action waits for verification. A bounded timeout gives the user a retryable connectivity message rather than treating every outage as a reason to repurchase.

Reconciliation provides another recovery path when local state is stale, but its effectiveness depends on worker scheduling, provider availability, and operational monitoring. Its presence in source does not establish a production recovery-time guarantee.

## Verification

Existing tests cover active and expired subscriptions, scheduled cancellation, lifetime products, enterprise access, authoritative denial overriding cached state, inventory switching, timeout handling, and concurrent verification. API tests cover Stripe lifecycle mapping, reconciler candidate selection, lifetime exclusions, revoked-record handling, and Apple restore ownership.

These describe test coverage reviewed for this write-up, not a newly executed suite. End-to-end confirmation still requires provider sandbox purchases/restores and deployment-specific worker checks. No receipts, customer identifiers, or payment dashboards belong in the public demo.

## Outcome to demonstrate

Show a synthetic account with the intended access state. If recording a sandbox failure, show the retry message and recovery after connectivity returns. Label it as a sandbox demonstration; do not infer production reliability statistics from a successful recording.
