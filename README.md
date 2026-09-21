# spajong-legal

**Retired as a content host.** The legal documents for the [Spajong](https://apps.apple.com/app/spajong)
iOS app now live on the product's own domain, in the `spajong-site` repo:

| Document | Current home |
|---|---|
| Privacy Policy | <https://spajong.app/privacy> |
| Terms of Use | <https://spajong.app/terms> |
| Password reset | <https://spajong.app/reset-password> |

The two pages here are **forwarders**, not content. Edit the documents in `spajong-site`
(`public/privacy.html`, `public/terms.html`, `public/reset-password.html`) — an edit here
changes nothing anyone reads.

## Why these pages still exist

They cannot simply be deleted:

- **`index.html`** — the old privacy URL is *compiled into* Spajong builds already installed
  on testers' phones (`RootView`'s contact sheet), and it is the URL recorded in App Store
  Connect for earlier submissions. Retire it only once no build referencing it is installed
  anywhere.
- **`reset-password.html`** — Supabase now sends recovery links to `spajong.app`, but a link
  already emailed stays valid for a while. This page forwards those, **preserving the query
  string and fragment**, because that is where the recovery token is. It deliberately does
  not verify the token itself.

`reset-password.html` forwards with JavaScript rather than `<meta http-equiv="refresh">`:
a meta refresh goes to a fixed URL and would drop `?token_hash=…&type=recovery`, turning a
working reset link into an error page.

## URL

`https://shireendiana.github.io/spajong-legal/`
