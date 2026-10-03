# Store Manager — single-file inventory, sales & loans app

A FIFO-costed inventory, sales, purchases, loan-tracking, and reporting
app for a small shop — built as one self-contained HTML file. No
install, no account, no backend, no setup. Open the file and it works.

Although it started life as a tool for a hardware store, nothing in it
is specific to hardware — a grocery store, pharmacy, electronics shop,
clothing store, or any small retail business that buys stock and
resells it can use this as-is. "Items" and "categories" are just
labels you fill in yourself.

## What it does

- **Inventory** — track items with a category, a reference selling
  price, and a low-stock threshold. Stock on hand is always computed
  from purchase history, never a number you set by hand.
- **Purchases** — record stock coming in from a supplier. Each
  purchase creates a cost "batch" at whatever price you paid.
- **Sales** — record stock going out, with the price you actually sold
  it for. Cost is pulled from the *oldest* unsold batch first (FIFO),
  so profit is always real: `(what you actually charged) − (what that
  specific unit cost you)`. A sale is blocked outright if you try to
  sell more than you have — it tells you exactly how much is left.
- **Suppliers & Loans** — keep a contact list of suppliers, and a
  running ledger of money owed to or by any supplier or customer, with
  a running balance per person.
- **Reports & Compare** — totals by day, week, month, or year, with
  filters by item, category, or supplier; a comparison view with
  charts and period-over-period percentage change, so you can see at a
  glance whether this month beat last month.
- **A password lock** on open, with a proper change-password flow and
  a direct reset if you forget it.

## Running it

There's nothing to install.

- **Locally:** download `hardware-store-manager.html` and open it in
  any modern browser (Chrome, Firefox, Edge, Safari).
- **Hosted for free, for anyone to use:** turn on GitHub Pages for this
  repo (Settings → Pages → pick the `main` branch) and GitHub will give
  you a public URL that opens the app directly in the browser —
  nothing to download.

## How your data works

Everything — every item, sale, purchase, and loan entry — is stored in
your browser's local storage, on your device, in your browser only.
There is no server and nothing is ever sent anywhere.

This also means:
- Data does **not** sync between devices or browsers. Using it on your
  phone and your laptop gives you two separate, unconnected sets of
  records.
- Clearing your browser's site data, using a private/incognito window,
  or switching browsers will lose your records. There's currently no
  built-in export/backup button — back up by copying the value of the
  `hsm_data_v1` key from your browser's developer tools if that
  matters to you.

## A Firebase-backed version also exists

There is a separate, multi-device version of this app (built with
Flutter, syncing through a Firebase backend, packaged as an Android
APK) with real-time sync across multiple phones/devices. It's not
included in this repository because it requires technical setup —
your own Firebase project, API keys, an Android signing key, and a
Flutter build toolchain — rather than being something you can just
open and use. If that's what you need, you'll have to set that
infrastructure up yourself; this repo is the zero-setup version.

## License

This project is released under the **[PolyForm Noncommercial License
1.0.0](https://polyformproject.org/licenses/noncommercial/1.0.0)**.

In plain terms:
- You can use it, for free, for any noncommercial purpose — run your
  own shop's books with it, study the code, modify it, build on it.
- You can share it and redistribute your changes.
- You **cannot sell it**, sell access to it, or use it (as-is or
  modified) as part of a paid product or service. Any commercial use
  requires a separate license from the author.

See [LICENSE](LICENSE) for the full legal text.

## Contributing

Issues and pull requests are welcome — bug fixes, new store-type
examples, translations, or UI polish are all fair game.
