# Security policy

People use this tracker to store their name, address and other personal details, so security problems matter here. Thank you for reporting them responsibly.

## Reporting a vulnerability

**Please don't open a public issue or pull request for a security problem.** Report it privately in one of these ways:

1. **GitHub:** use **Report a vulnerability** on this repository's **Security** tab.
2. **Email:** write to tom.sun@duke.edu with "Security" in the subject line.

Please include:

- what the problem is and what an attacker could do with it
- steps to reproduce it, including browser and version
- any proof of concept, using made-up personal details rather than real ones

I'll confirm I've received your report as soon as I can, keep you updated while I fix it, and credit you when the fix is published, unless you'd rather stay anonymous.

## What's in scope

Anything that could expose or damage a user's personal details, for example:

- weaknesses in the passphrase encryption, key handling or auto-lock
- personal details written to storage, backups, URLs or logs without encryption
- script injection, for example through a pasted backup, a listing link or a broker's data
- requests to third parties that the site's Privacy Policy says don't happen
- a change to the deploy workflow that would let unreviewed code reach the live site

## What's out of scope

- Problems on data broker websites or their opt-out forms. Report those to the broker.
- Problems in Gmail, Outlook or your mail app once a draft is open there.
- An attacker who already controls your device or browser. The tracker can't protect against that.

## Supported versions

Only the live site, built from the `main` branch, is supported. Fixes are released there.
