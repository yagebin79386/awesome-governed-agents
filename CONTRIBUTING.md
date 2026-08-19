# Contributing

Additions and corrections are welcome. Please open a pull request that changes one thing.

## What belongs here

An entry must be **governance-relevant**: it constrains, gates, records, or rolls back what an agent
does. General agent frameworks belong here only when they ship a governance primitive that is useful
on its own — a durable interrupt point, an approval hook, a policy boundary.

## Entry format

```
- [Name](https://github.com/owner/repo) — What it does, in the project's own terms.
```

- One sentence. Describe the mechanism, not the ambition.
- Use the project's own vocabulary. No marketing adjectives, no "revolutionary", no star counts.
- Link to the source repository or the canonical project page, not to a blog post about it.
- Place it in the section whose problem it actually solves. When in doubt, say which in the PR.

## What gets rejected

- Unmaintained projects presented as current. Prior art is welcome, but label it as such.
- Entries whose governance claim is only in the README and not in the code.
- Self-promotion without a working link to the mechanism being claimed.

## Design notes

The "Design notes" section collects patterns, not products. Proposals there should name a failure
mode that recurs across several tools, and say what the pattern does about it.
