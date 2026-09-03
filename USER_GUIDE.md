# Restock Buddy - Beginner Setup Guide

This guide assumes you have never used Restock Buddy before. Follow the sections in order. You only need to complete the setup once; the program remembers your settings and products.

## Before you begin

You will need:

- An Android or iPhone with the free **ntfy** app installed (Google Play or the
  App Store). It is open source and does not require an account.
- An internet connection on both the computer and the phone.
- At least one product page or product ID to monitor.
- Google Chrome, Microsoft Edge, or Firefox, for browser-assisted retailer checks.

Restock Buddy only checks public product information and sends notifications. It does not sign in to stores, add items to a cart, or purchase anything.

## Step 1: Open Notifications

Open **`RestockBuddy.exe`**, then select **Notifications** at the top.

Restock Buddy sends alerts through **ntfy**, a free push notification service. Your
computer publishes a short message to a private channel called a *topic*, and
your phone receives it instantly. There is no account, no API key, no phone
number, and no email involved.

### Set up your phone

1. Install the free **ntfy** app from Google Play or the App Store.
2. In Restock Buddy, find the **Topic** shown on the Notifications tab and select
   **Copy Topic**.
3. Open the ntfy app, tap the **+** button, paste the topic exactly, and tap
   **Subscribe**.

Your phone is now listening. It should show "You haven't received any
notifications for this topic yet" until the first alert arrives.

### Keep your topic private

The topic name is the only thing protecting your alerts. Anyone who knows it
can read every alert you receive and send you fake ones. Restock Buddy generates a
long random topic for you so it cannot be guessed.

Do not post your topic in screenshots, videos, or bug reports. If you share it
by accident, select **Generate New Topic** and subscribe your phone to the new
one.

### Send push notifications to my phone

Turn on this switch to enable alerts. After upgrading from an older version it
starts turned off, because your phone has to subscribe to the topic first.

### Priority

Choose how insistent alerts should be:

- **Normal** - a standard notification with the default sound.
- **High** - louder, and shown at the top of the notification list. This is the
  default and suits most people.
- **Urgent** - a long vibration and pop-over notification that can break
  through Do Not Disturb. Choose this if you want restocks to wake you.

### Server

Leave this as `https://ntfy.sh` unless you run your own ntfy server. The public
service allows 250 notifications per day, far more than restock monitoring
needs.

### Save Settings

Select **Save Settings** after completing the fields. You should see a
confirmation message.

### Send Test Notification

Select **Send Test Notification** before adding products.

- If the notification arrives on your phone, the complete alert path is working.
- If nothing arrives, check that the ntfy app is subscribed to exactly the topic
  shown in Restock Buddy.
- If Restock Buddy reports an error, it names the cause, such as an unreachable
  server or the daily limit being reached.

The test message includes <https://github.com/Brusko25/restock-buddy>. Tap
the notification on your phone to confirm that links open correctly. Real
restock alerts open the product page the same way.

## Step 2: Add products

Select **Products** at the top, then use the **Add a Product** card.

### Name

Enter a short name that you will recognize in a restock notification.

Good example: `Prismatic Evolutions Booster Bundle`

Avoid a generic name such as `Pokémon cards`, especially when tracking several products.

### Retailer

Select the store that sells the product. The choice controls how Restock Buddy checks availability.

### URL / ID

What you enter depends on the selected retailer:

#### Pokémon Center

Paste the complete product-page address from the browser's address bar.

Example format:

`https://www.pokemoncenter.com/product/123-45678/example-product`

#### Target

Enter the numeric **TCIN**, not necessarily the entire URL. It is normally the number after `A-` in a Target product address.

Example URL:

`https://www.target.com/p/example/-/A-91234567`

Enter:

`91234567`

#### Walmart

Enter the numeric Walmart item ID. It is normally the long number at the end of the product address.

Example URL:

`https://www.walmart.com/ip/example-product/123456789`

Enter:

`123456789`

#### Best Buy

Paste the complete product-page address or enter the numeric SKU shown on the page. Best Buy is checked through the browser helper and does not require an API key.

Example URL:

`https://www.bestbuy.com/site/example/6571234.p`

Enter:

`6571234`

#### GameStop

Paste the complete GameStop product-page address from the browser's address bar.

Example format:

`https://www.gamestop.com/toys-games/trading-cards/products/example-product`

#### Amazon

Paste the complete Amazon.com product-page address. Use the main product page rather than a search-results or shopping-cart address.

Example format:

`https://www.amazon.com/dp/B012345678`

#### Other / Generic

Paste the complete product-page address, then use **Test This Page** below to
tell Restock Buddy how that shop shows availability.

### Watching a shop Restock Buddy does not know

Restock Buddy knows six shops by name. Any other shop works too, and setting
one up takes about a minute.

1. Open the product page in your own browser and look at it. Note what tells
   you whether the item is available — usually a button, or the words
   **Sold Out**.
2. Enter a name, choose **Other / Generic**, and paste the full address of that
   product page.
3. Select **Test This Page**. A browser window opens.
4. **The first time you do this for a shop, you will be asked for permission.**
   A page appears explaining that Restock Buddy wants to read that shop, and
   your browser then shows its own confirmation. Choose **Allow This Website**.
   Nothing is read until you agree.
5. A list appears describing what was found, with how much weight to give each
   result:

   > **IN STOCK** · High confidence — A button reading “Add to Cart” can be clicked.
   > **NO SIGNAL** — The shop publishes no product data on this page.

   Choose **Use This** beside the one that matches what you saw in step 1. The
   strongest result is offered first.
6. Select **Add Product**.

Results that found nothing are still listed. That is useful — it tells you
which of the others to trust.

**Allow This Website** grants access to that one shop. **Allow All Websites**
covers every shop at once, which saves answering this again if you watch many,
but it is the broader choice. Allowing one at a time is safer.

If none of the results fit, choose **Advanced Rules** and describe the shop yourself:
the wording shown when it is sold out, the wording on the purchase button,
in-stock wording, or an exact element on the page.

If nothing at all could be read, the page may not be a product page, or the
shop may show a human-verification page to anything automated. Opening the page
in your browser and clearing that check by hand, then trying again, usually
resolves it.

Your settings for a shop are always preferred over anything that ships with
Restock Buddy. If a shop changes its layout and stops reading correctly, run
**Test This Page** again and choose a different result.

### Add Product

Select **Add Product**. The new item will appear under **Tracked Products** and is saved automatically.

### Edit and Delete

- **Edit** scrolls to the product form, loads the tracked product, and focuses the name field. Change the fields, then select **Save Changes**.
- **Delete** permanently removes the product from the tracking list after confirmation.

## Step 3: Start monitoring

Select **Monitor** at the top.

The dashboard shows:

- **Tracked** - the number of products in your list.
- **In Stock** - the number currently known to be available.
- **Alerts Sent** - the number of alerts sent during this program session.

The **Check Interval** card controls how long the program waits between complete checks of all tracked products.

1. Enter a whole number of seconds.
2. Use `20` seconds or more. The recommended setting is `60` seconds.
3. Select **Apply Interval** to save the value.

If monitoring is already running, the new interval is saved but begins the next time you start monitoring. Select **Stop**, then **Start Monitoring**, if you want to use it immediately.

Select **Start Monitoring**. Keep the program open while it monitors.

### One-time retailer browser setup

Protected retailer pages accept an established browser session more reliably than a new empty browser profile. Restock Buddy uses the browser selected on the Monitor tab. Select **Set Up** once.

**Chrome or Edge**

1. Turn on **Developer mode** on the Extensions page.
2. Select **Load unpacked**.
3. Choose the `browser_helper` folder that Restock Buddy opened.
4. Confirm that **Restock Buddy Browser Helper** is enabled and shows version **2.3.0**. Select **Reload** after installing an updated Restock Buddy release.

**Firefox**

1. Select **This Firefox** on the left side of the `about:debugging` page.
2. Select **Load Temporary Add-on**.
3. Choose `manifest.json` inside the `browser_helper_firefox` folder that Restock Buddy opened.
4. Confirm that **Restock Buddy Browser Helper** shows version **2.3.0**.

The **Set Up** button opens the correct browser page and helper folder for the browser you selected, and copies that folder path to the clipboard.

The helper supports Pokémon Center, Target, Walmart, Best Buy, GameStop, and
Amazon in Google Chrome, Microsoft Edge, and Firefox without an extra prompt.
In v0.8.3, it also supports other HTTPS shops after you grant permission for
that shop. Firefox uses a separate temporary helper package. Until it is
signed by Mozilla, Firefox removes it every time the browser closes, so it must
be re-added after each launch. That makes Firefox suitable for trying out
rather than unattended monitoring.

After this one-time setup, **Start Monitoring** is the only routine action. Restock Buddy keeps every browser-assisted product together as a tab in one browser window. Each tab reads only its product's public availability and refreshes automatically no faster than once every 60 seconds. The shared window closes when monitoring stops. Restock Buddy does not move or resize that window, so put it wherever suits you - minimized is fine. Do not close its tabs while monitoring, and keep the computer awake.

The Monitor tab always shows the helper version installed beside the program. After stock checks respond, the indicator turns green when the browser is running the same version or red when it needs to be reloaded. If a responding browser uses a different version, or a helper too old to report one, Restock Buddy also displays a **Browser helper is out of date** warning. Stop monitoring, replace or reload the helper from the program's current folder, and confirm the expected version before testing again.

Select **Stop** when you want to pause all checks. Closing the program also stops monitoring.

## Understanding product statuses

- **NOT CHECKED** - monitoring has not checked this product yet.
- **CHECKING** - the product is being checked now.
- **IN STOCK** - the retailer reported that the product is available.
- **OUT OF STOCK** - the retailer reported that the product is unavailable.
- **ERROR** - the program could not determine availability. The store may be unavailable, blocking the request, or may have changed its website.

The **Last checked** time shows when the most recent attempt finished.

When a product changes to **IN STOCK**, the text contains `IN STOCK`, the monitored product name, and a clickable storefront link. Target, Walmart, and Best Buy IDs are converted into usable store links automatically. Pokemon Center, GameStop, Amazon, and generic products use the page address you saved.

## Activity Log

Select **Activity Log** at the top to open a large, dedicated history window. It shows each stock check, notification, error, and monitoring start or stop event. Select **Clear Log** to erase the messages currently displayed. Clearing the visible log does not remove products or change settings.

If something does not work, select **Send Diagnostic Report**. The app creates a privacy-safe ZIP in the `diagnostics` folder, copies its path, selects it in File Explorer, and opens a prefilled GitHub issue. Drag the selected ZIP onto the issue, add a short description, review everything, and select **Submit new issue**. The app never stores a GitHub password or upload token, and nothing is submitted until you confirm it on GitHub.

The report includes the app version, Windows and runtime details, your check interval, safe retailer information, anonymous product fingerprints, and recent diagnostic errors. It excludes your settings file, your alert topic, old phone and email settings, passwords, API keys, product names, full product URLs, and product IDs.

## About

Select **About** at the top to read a plain-language explanation of Restock Buddy, see the currently installed version, and review the release notes for every version.

Select **Open GitHub** to open the official Restock Buddy repository in your web browser. The About tab also includes another **Check for Updates** button.

## Updates

The version number appears beside **Check for Updates** in the header. The program also performs a quiet update check when it opens.

If a newer version is available, Restock Buddy shows the new version number and a short list of changes. Select **Yes** to download and install it. The program downloads the official GitHub release, verifies its security checksum, and tells you when it is ready.

After you select **OK**, Restock Buddy closes, installs the new files, and reopens automatically. Do not move or delete the application folder while an update is running. The compact distribution contains one application file, `RestockBuddy.exe`, this PDF guide, and the `browser_helper` and `browser_helper_firefox` folders instead of more than one thousand visible runtime files.

Your settings and products are stored in `settings.json` beside the program. The automatic installer leaves this file in place, so your existing setup is preserved. Keeping an occasional backup of `settings.json` is still recommended.

Automatic installation requires the application folder to be writable. A folder on your Desktop or in Documents normally works. If automatic installation fails, the program offers to open the manual GitHub download instead and leaves the existing program in place.

## Common problems

### The test notification does not arrive

- Confirm the ntfy app is subscribed to exactly the topic shown in Restock Buddy.
  A single wrong character means a different channel.
- Confirm **Send push notifications to my phone** is turned on and you selected
  **Save Settings**.
- Check that notifications are allowed for the ntfy app in your phone's
  settings, and that the app is not being restricted by battery optimisation.
- If Restock Buddy says the daily limit was reached, the free service allows 250
  notifications per day; it resets automatically.
- If Restock Buddy cannot reach the server, check the computer's internet
  connection and any firewall blocking outbound HTTPS.

### Alerts arrive but make no sound

- Set **Priority** to High or Urgent on the Notifications tab.
- In the ntfy app, open the topic settings and check the notification sound and
  vibration for that topic.
- Confirm Do Not Disturb is not silencing the ntfy app. Urgent priority can
  break through Do Not Disturb on Android.

### A product always shows ERROR

- Recheck the URL, TCIN, item ID, or SKU.
- Confirm that the correct retailer was selected.
- Open the product page in a browser to make sure it still exists.
- If every field is correct, the retailer may have changed its website or API and the checker may need an update.
- For a browser-assisted store, confirm that the helper is installed and enabled in the browser selected on the Monitor tab.
- Open that browser's Extensions page and confirm **Restock Buddy Browser Helper** is enabled.
- If the helper was updated, select **Reload** for it on the browser's Extensions page.
- A retailer may still return a traffic-protection page. If it does, the product remains **ERROR** and no false alert is sent.

### A generic product is inaccurate

Run **Test This Page** again and choose the result that matches what the shop
currently shows. If none fit, open **Advanced Rules** and describe the shop's
sold-out wording, purchase button, in-stock wording, or exact page element.

## Privacy and safety

The program stores its settings in `settings.json` beside the program, including the private notification topic. Keep the application folder private and share only the privacy-safe diagnostic ZIP when requesting support. Restock Buddy does not require or store an ntfy account password or API key. The private topic is removed from diagnostic reports automatically.

The browser helper has built-in access to the six supported retailers and may
read another HTTPS shop only after you approve that site's permission request.
It also uses a private `127.0.0.1` connection to Restock Buddy on the same
computer. It reads public product status only on monitoring tabs opened by
Restock Buddy and does not read browser history, saved passwords, or account information.
ZIP files do not include browser-profile data.
