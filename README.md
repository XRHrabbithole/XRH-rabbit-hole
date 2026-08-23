# XRH wallet icon pack (Xaman / XRPL Meta)

Xaman does **not** read a logo from your website by itself.
It pulls token icons from **XRPL Meta**, which reads your **xrp-ledger.toml** + issuer **Domain**.

## Files

| File | Use |
|------|-----|
| `xrh-icon-256.png` | Main wallet icon (upload next to index.html) |
| `xrh-icon-512.png` | Higher-res copy |
| `xrp-ledger.toml` | Metadata file wallets look up |

## 1. Put the icon on the live site

Upload to the same GitHub folder as `index.html`:

- `xrh-icon-256.png`
- `xrh-icon-512.png` (optional)

After deploy, this URL should open the image:

https://xrhrabbithole.github.io/XRH-rabbit-hole/xrh-icon-256.png

## 2. Host the TOML at the special path

Wallets look here (domain only, no `/XRH-rabbit-hole`):

```
https://YOURDOMAIN/.well-known/xrp-ledger.toml
```

Because your site is a GitHub **project** page, Domain `xrhrabbithole.github.io` looks for:

```
https://xrhrabbithole.github.io/.well-known/xrp-ledger.toml
```

That is **not** the same as the project folder. Easiest options:

**A. User site repo (recommended on GitHub)**
1. Create a repo named exactly `xrhrabbithole.github.io`
2. Add folder `.well-known`
3. Put `xrp-ledger.toml` inside it
4. Enable GitHub Pages on that repo

**B. Custom domain** (if you add one later)
Host `/.well-known/xrp-ledger.toml` on that domain.

## 3. Set Domain on the issuer account

In Xaman (issuer wallet):

1. Account settings → **Domain**
2. Set it to the domain only, example:
   `xrhrabbithole.github.io`
   (no `https://`, no path)
3. Sign the AccountSet

The Domain on-ledger must match the domain serving the toml file.

## 4. Wait for XRPL Meta / Xaman

- XRPL Meta must crawl the toml
- Xaman refreshes token icons about once a day
- Xaman also wants roughly Trust Level 1 + a real holder/trustline count

Check later:
https://s1.xrplmeta.org/token/XRH:r9xu7pdBEx4DdiatMqAUFodgxaPkfFU1Zw

Look for `meta.token.icon`.

## Notes

- Icon is a square PNG of your existing circular logo.
- Changing the PNG later is fine if the URL stays the same.
- First Ledger tokens sometimes already have a toml on an FL subdomain. If that exists, you can point the icon URL there too — but the Domain + toml pair must still match.
