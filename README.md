# St. Rita's Foodz — Daily Records

A small offline-first record-keeping app for the shop: sales, stock, expenses,
debts and customer contacts. It is a single HTML file with no build step and no
server — everything runs in the browser and saves to that device's storage.

Makinson Plaza, Opp St. David Agboyin Primary School, Ogbomoso, Oyo State.

## What it does

- **Sell** — record item by item, or just a total when catching up later.
  Each sale is tagged with a **Type of Sales** (Main cash, Pure water, Jinja,
  Iru Soap, Drink, POS, Transfer sales, Home purchase). POS and transfer sales can carry a charge.
- **Airtime** — card amount sold plus the cash back earned, and the platform
  it went through (Moniepoint or Opay). The sale total is card + cash back.
- **Money Out** — stock purchases with cost, supplier and proposed selling prices,
  plus running expenses. Each stock-in can carry an **expiry date**; the Home
  screen warns about anything expiring within 3 months.
- **Jinja / Drink / Pure water** sales are deducted from the purchase record
  automatically, so the purchase log shows what was bought, what has sold off
  and what is left.
- **Reports** — daily, weekly and monthly summaries with profit per item.
- **Debt list** — who is owing, for what, how much and since when; a customer
  dropdown, a total per customer, and Download / Print. The day view shows
  the debts given and paid back on that day.
- **Customer contacts** — names, phone numbers and emails.
- **Items** — prices, cost, stock counts. Tap an item's name for its full
  history: every sale and every purchase of it. The list can be downloaded or printed.

## Running it

Open `index.html` in a browser. That is all it needs.

For the installable app (offline support, home-screen icon) it has to be served
over HTTPS, because browsers block service workers on `file://`:

```
npx serve .
```

then open the `http://localhost:…` address it prints.

## Deploying

Static hosting — upload these files as they are, with no build command:

- `index.html` — the whole app
- `sw.js` — service worker (offline support)
- `manifest.webmanifest` — makes it installable
- `icon-192.png`, `icon-512.png` — app icons
- `_headers` — cache rules (Netlify and Cloudflare Pages both read this)
- `banner.png` — optional shop banner shown in the header

After changing `index.html`, bump the cache name in `sw.js`
(`srf-cache-v5` → `v6`) so installed phones pick the update up.

## Installing on a phone

Open the deployed HTTPS link, then:

- **Android / Chrome** — menu → *Install app* or *Add to Home screen*
- **iPhone** — must be **Safari** → Share → *Add to Home Screen*

## Your records live on the device

Sales are stored in the browser on each phone or computer. They are **not** on a
server and they do **not** sync between devices. Clearing the browser's site data
erases them.

Use **⤓ Backup** in the app header regularly and keep the exported file somewhere
safe. It is the only copy, and the only way to move records to another device.
