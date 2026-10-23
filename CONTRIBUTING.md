# Contributing

Thanks for helping keep the tracker accurate. Broker contacts and state laws change often, so corrections are the most useful contribution.

## Never share your own personal details

**Don't put your own name, address, phone number, email or listing links in an issue or pull request.** Everything here is public. When you report a broken opt-out page, link the broker's general opt-out page, not your own listing.

## Suggesting a correction

Open an issue and include:

- **the site or state** it's about
- **what's wrong**, and what it should say instead
- **a source:** the broker's privacy policy, its opt-out page, California's [data broker registry](https://cppa.ca.gov/data_broker_registry/), or a state's official legislature or attorney general page

Corrections without a source can't be accepted. The tracker cites these details in emails people send, so they have to be right.

You can also use the site's contact form (`#contact`) if you'd rather not use GitHub.

## Changing the data yourself

Both data tables are in `index.html`.

- **Brokers:** the `SITES` array. Each entry's fields are named in the code: `n` (name), `s` (search page), `o` (opt-out page), `e` (email), `d` (promised days), `ev` (where the email address was confirmed), `pol` (the privacy policy it came from), and so on. Follow an existing entry's shape.
- **State laws:** `STATE_DATA`. The comment above it explains every field. Set `checked` to the date you confirmed the change. For a new comprehensive law, fill in `days` and `ext` (the response deadline and extension) before its `effective` date, or the tracker can't apply it.

## Changing the code

1. Fork the repository and make a branch.
2. Preview locally (see [README](README.md#run-it-locally)) and check that nothing breaks, including with your details locked and unlocked.
3. Open a pull request that explains what changed and why.

### Privacy rules every change must follow

These are promises the Privacy Policy makes, so a pull request that breaks one won't be merged:

- **No analytics, trackers, ads or cookies.**
- **No requests to other servers when the page loads.** Host fonts, data and libraries in `public/`.
- **Personal details are only ever saved encrypted.** Never write a name, contact detail, listing link, note or email draft to storage, a backup or a URL outside the encrypted box.
- **Nothing is sent anywhere unless the user chooses to send it.**

If a change affects what the tracker stores or shares, update the Privacy Policy section of `index.html` in the same pull request.

## Review

Every pull request is reviewed by the maintainer before it's merged, and only reviewed changes on `main` are published to the live site.

## Licensing of contributions

By contributing, you agree that code changes are released under the [MIT License](LICENSE), and changes to the `SITES` and `LEFT_OUT` data under [CC BY-NC-SA 4.0](LICENSE-DATA.md).
