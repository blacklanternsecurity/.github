# RFC Process

An RFC is an issue that requires a consensus decision reached through compromise.

Use one when a change needs agreement before work starts. A change that only needs review is a pull request.

The owner is whoever opens it, and stays the owner until it ends.

## Where it lives

The lowest repository that contains the change.

- Only `blastdns`? It lives in `blastdns`.
- How several dependencies work together inside `bbot`? It lives in `bbot`, because the change is bbot's.
- Touching multiple repositories? The topmost parent they share.

## Participation

Anyone who can see the RFC can participate, internal or external. Visibility is the only gate, so an RFC in a private repository is staff only.

Object in the thread. Name what breaks and say what you would do instead.

## Revisions

The owner keeps a changelog, one entry per revision. Each entry says what changed, why, and who raised it, linked to their comment.

Withdrawn items stay visible with the reason. Deleting them hides the compromise that was reached.

## Ending an RFC

Two exits, and no others:

- **Quorum consensus.** Stakeholders agree.
- **Expiration.** The owner sets the window when the RFC opens, sized to what is being decided.

Either way the RFC becomes an ADR in place. Same issue, same number, same thread.

## Becoming an ADR

The owner swaps the `rfc` label for `adr`, records the decision and which exit reached it as the final changelog entry, and closes the issue.

Nothing is copied anywhere. The thread already holds the proposal, the objections, what was withdrawn and why, and the decision. Moving it to a new issue or a file breaks every link that points at it and separates the decision from the argument that produced it.

An expired RFC is still a decision. What was considered and not adopted is worth as much later as what was.

## Labeling

Every RFC carries the `rfc` label, and every ADR the `adr` label. Without them they are not findable.
