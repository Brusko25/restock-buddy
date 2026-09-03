# Restock Buddy

Public Windows downloads, release history, and support for Restock Buddy.
Application source code is maintained in the private `Restock-Buddy-Code` repository.


Monitors product pages and sends a push notification to your phone when it
detects that something has come back in stock.

It does not add to cart, sign in, or buy anything. It reads the same public
stock information your browser sees when you open the page, and tells you about
it — the buying is up to you.

**[Download the latest release](https://github.com/Brusko25/Restock-Buddy-Releases/releases/latest)**

New to it? The bundled
**[Restock-Buddy-User-Guide.pdf](Restock-Buddy-User-Guide.pdf)** is a
field-by-field walkthrough written for first-time use.

## Getting started

1. Download the latest release and extract the folder anywhere you like.
2. Run **`RestockBuddy.exe`**. No Python or terminal needed.
3. On the **Notifications** tab, install the free **ntfy** app on your phone
   (Google Play or the App Store), copy the topic shown, and subscribe to it in
   the app. Turn on push alerts, save, then send a test notification.
4. On the **Products** tab, add what you want to watch.
5. On the **Monitor** tab, select **Set Up** once to load the browser helper,
   then **Start Monitoring**.

Once a restock is detected, its alert usually arrives in about a second, makes
a sound, and opens the product page when tapped. There is no account to create,
no API key, and no email setup.

## What each retailer needs

| Retailer       | What to enter               | Where to find it                             |
| -------------- | --------------------------- | -------------------------------------------- |
| Pokémon Center | full product URL            | copy it from the address bar                 |
| Target         | TCIN or full URL            | in the address: `.../-/A-88641039` — either `A-88641039` or `88641039` works |
| Walmart        | item ID or full URL         | in the address: `.../ip/123456789`           |
| Best Buy       | SKU or full URL             | in the address: `.../6418599.p`              |
| GameStop       | full product URL            | copy it from the address bar                 |
| Amazon         | full product URL            | use the product page, not a search result    |
| Other          | any HTTPS product URL       | paste the page address, then use **Test This Page** |

## The tabs

**Notifications** — set up and test phone alerts. Priority can be set to
Urgent, which lets alerts break through Do Not Disturb.

**Products** — add each product with a name, its retailer, and the URL or ID.
Saved automatically.

**Monitor** — set how often products are checked (20 seconds minimum, 60
recommended) and start or stop monitoring. Protected retailer pages are checked
through Google Chrome, Microsoft Edge, or Firefox using the included helper extension,
which is loaded once via **Set Up**. There is also a switch to keep the PC awake
while monitoring, since a sleeping machine cannot check anything. While monitoring, those pages sit together as tabs in a single browser window
that closes itself when monitoring stops. That window is left exactly as you
leave it — minimize it if you prefer it out of the way.

**Activity Log** — every stock check, alert, and error, plus **Send Diagnostic
Report** for reporting problems.

**About** — version information, release history, and a link to this repository.

## Reporting a problem

Open the **Activity Log** tab and select **Send Diagnostic Report**. A
privacy-safe ZIP is saved in the `diagnostics` folder beside the application,
selected in File Explorer, and a prefilled GitHub issue is opened. Drag the ZIP
onto the issue, review it, and submit.

Nothing is submitted until you confirm it on GitHub, and no GitHub password or
upload token is ever stored.

Reports contain the app version, Windows and runtime details, the check
interval, your alert method and priority, the selected browser and installed
helper version, retailer domains, hashed product references, the shops you have
site rules for and the kinds of check those rules use, and recent errors. They
exclude `settings.json`, your alert topic, phone numbers, email addresses,
passwords, API keys, product names, full product URLs, product IDs, the names
given to site rules, and the address of a self-hosted alert server.
`BUG_REPORT_TEMPLATE.md` has the suggested format.

## Notes and limitations

- **It will not guarantee you get the product.** High-demand restocks can sell
  out in seconds, including to purchasing bots. This buys you the fastest
  possible manual reaction time, nothing more.
- **Rate limiting.** Checking every 60 seconds per product is a sensible
  default. Much faster raises the chance a retailer temporarily blocks your IP.
- **Sites change.** Retailers alter their pages and data without warning, which
  can break a checker. If a product stops reporting correctly, that is the most
  likely cause — please open an issue.
- **The browser helper** covers Pokémon Center, Target, Walmart, Best Buy,
  GameStop, and Amazon in **Google Chrome, Microsoft Edge, and Firefox**. Its permissions
  are limited to those retailer pages and `127.0.0.1`, and only public stock
  status is passed back to the app. Firefox uses a separate helper package. Until that package is signed by
  Mozilla, Firefox removes it every time it closes, so it has to be re-added on
  each launch — usable for trying out, not yet for unattended monitoring.
- **Protected pages** are checked using your existing selected browser session,
  because some stores reject a fresh empty profile. If a store shows a protection page,
  the check stays as ERROR and can never turn into a false in-stock alert.
- **Other shops need your permission once.** The helper ships with access to
  the six retailers above and nothing else. The first time Restock Buddy opens
  a product page on another shop, a page appears asking whether the helper may
  read that shop, and your browser then shows its own confirmation. Nothing is
  read until you agree. You can allow the one shop or, if you watch many, all
  shops — allowing one at a time is the narrower choice and is recommended.

## Custom-shop monitoring

Choose **Other / Generic**, paste the address of the product page, and select
**Test This Page**.

The page opens in your browser, is read every way Restock Buddy knows how, and
each result is described in plain words along with how much weight to give it:

> **IN STOCK** · High confidence — A button reading “Add to Cart” can be clicked.
> **NO SIGNAL** — The shop publishes no product data on this page.

Choose the result that matches what you can see on the site. Restock Buddy
watches for exactly that from then on. The strongest result is offered first: a
purchase button you could actually click counts for more than published product
data, which some shops leave out of date on sold-out pages.

Results that found nothing are still listed. Knowing a shop publishes no
product data is what tells you to choose the button instead.

If none of them fit, **Advanced Rules** lets you describe the shop yourself — the
wording that appears when it is sold out, the wording on the purchase button,
or an exact element on the page.

Your settings for a shop are always preferred over anything that ships with the
app, so a shop that changes its layout can be repaired without waiting for a
release.

## Updates

The app checks for updates on launch and from the button in the header.

**v0.8.1 must be installed by hand if you are on v0.8 or earlier.** Extract the
release **over your existing folder** — your settings and tracked products live
in `settings.json`, which an install never overwrites.

Two separate reasons, depending on where you are coming from:

- **From v0.8.** The project moved to a new address, and v0.8 checks the old
  one. It does not report an error; it simply keeps telling you that you are up
  to date. Installing v0.8.1 by hand once points it at the new address, and
  automatic updates continue normally from there.
- **From v0.7 or earlier.** The application file was renamed from
  `PokeStockAlerts.exe` to `RestockBuddy.exe`, and those updaters look for the
  old name. Obsolete executables are removed for you on first launch.

In-app updating works normally from v0.8.1 onward. Versions v0.3.x and earlier
relied on a compatibility launcher that no longer ships.

Every published version, including earlier PokeStock Alerts releases, is listed in [Release history](RELEASES.md). Download the Windows ZIP from each release; GitHub's automatic Source code archives contain this documentation, not the application.

---
