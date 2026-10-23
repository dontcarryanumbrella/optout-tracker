# Opt-Out Tracker

A free, private tool for getting your personal information off people-search sites. It walks you through 36 data brokers (plus 4 optional ones), most important first. It tracks what you've sent and when, applies your state's legal deadlines, and drafts request emails that cite your state's privacy law and each broker's own policy.

**Live site:** https://dontcarryanumbrella.github.io/optout-tracker/

## What it does

- **Tracker:** each site has a search link, its opt-out page, what it asks for and the response time it promises. You set a status (found, submitted, removed and so on), and the tracker tells you what's due next.
- **Request emails:** drafts written for your state's law and the broker's own privacy policy. You open them in Gmail, Outlook or your mail app, or copy them.
- **State law dashboard:** a map of which states give residents opt-out rights, which have laws on the way, and their deadlines.
- **Reminders:** one repeating calendar check-in, instead of dozens of separate reminders.
- **Resources:** privacy-friendly browsers and blockers, Global Privacy Control (with a live check of your browser), search-result removal, state data broker registries, the full broker list as a table or CSV, AI training opt-outs, junk call, mail and credit opt-outs, and safety resources.
- **A little fun:** on the Resources page, four shapes dance to an original lofi groove that's composed in code and played by your browser. Press the button under them to hear it. It fades and muffles as you scroll away, as if you're walking off.

## Privacy by design

The tracker runs entirely in your browser. There's no account, no server that receives what you type, no analytics, no ads and no cookies.

- **Your name, contact details, listing links and notes are only ever saved encrypted.** They're encrypted with AES-256-GCM, using a key derived from your passphrase with PBKDF2-SHA-256 and 600,000 rounds. The passphrase is never stored or sent anywhere.
- **Everything is stored in your browser's local storage** on your own device.
- **Fonts, map data and libraries are hosted with the site,** so loading the page contacts no other company.
- **Generated in your browser, not fetched:** the music, the CSV download, calendar files and the Global Privacy Control check all happen on your device.
- **Nothing leaves your device unless you choose to send it,** for example by opening an email draft.
- **A Content Security Policy enforces this:** the page can't load scripts, images, frames or data from any other site, or send data to one, even if a bug slipped in.

The full details are in the site's Privacy Policy (`#privacy`). Because the code is public, you can check every one of these claims yourself.

## How the code is organized

Everything that runs is in one file, with a few static assets beside it:

| Path | What it is |
|---|---|
| `index.html` | The whole site: markup, styles and scripts |
| `public/fonts/` | Self-hosted fonts, their CSS, and their license (`OFL.txt`) |
| `public/us-states.json` | US state shapes for the dashboard map |
| `public/vendor/matter.min.js` | Physics library for the Motivation page animation |
| `.github/workflows/pages.yml` | Publishes the site to GitHub Pages |

Inside `index.html`, these are the main data tables:

- **`SITES`:** every broker, with its links, what it asks for, contacts and promised response time.
- **`STATE_DATA`:** every state's privacy law status, effective date, response deadlines and official source. The map, the counts and the tracker's deadlines all read from it.
- **`lofiGroove`:** the Resources page music: chords, melody, bass and drums, written as code.

The Resources page's broker table and CSV are built from `SITES` and `LEFT_OUT`, so they always match the tracker.

## Run it locally

The published site is `index.html` with the contents of `public/` and the license files beside it. To preview that exact layout:

```bash
mkdir -p _site && cp index.html LICENSE LICENSE-DATA.md THIRD-PARTY-NOTICES.md _site/ && cp -r public/. _site/
python -m http.server 8000 --directory _site
```

Then open http://localhost:8000. The GitHub Pages workflow builds the site the same way.

## Contributing

Corrections are especially welcome: broken opt-out links, changed broker contacts, and new or amended state laws. See [CONTRIBUTING.md](CONTRIBUTING.md). To report a security or privacy problem, see [SECURITY.md](SECURITY.md). Please don't open a public issue for those.

## Licenses

- **Code, including the music:** [MIT](LICENSE).
- **Site list and opt-out instructions** (the `SITES` and `LEFT_OUT` data): adapted from [BADBOOL](https://github.com/yaelwrites/Big-Ass-Data-Broker-Opt-Out-List) by Yael Grauer and contributors, under [CC BY-NC-SA 4.0](LICENSE-DATA.md). This means no commercial use, and adaptations must keep the same license.
- **Fonts, map data and the physics library:** each keeps its own license (SIL Open Font License, ISC and MIT). The full texts are in [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md) and [`public/fonts/OFL.txt`](public/fonts/OFL.txt), and both are published with the site.

This project is general information, not legal advice.
