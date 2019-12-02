# blurts-tools

Link to a bunch of different Firefox Monitor tools

## Table of Contents

1. [pdehaan/blurts-missing-logos](#1-pdehaanblurts-missing-logos)
1. [pdehaan/blurts-server-data-classes](#2-pdehaanblurts-server-data-classes)
1. [pdehaan/blurts-data-classes-stats](#3-pdehaanblurts-data-classes-stats)
1. [pdehaan/blurts-kinto](#4-pdehaanblurts-kinto)
1. [pdehaan/blurts-pageres](#5-pdehaanblurts-pageres)
1. [pdehaan/hibp-chain-api](#6-pdehaanhibp-chain-api)
1. [pdehaan/firefox-monitor-link-check.js](#7-pdehaanfirefox-monitor-link-checkjs)
1. [pontoonql.now.sh/firefox-monitor-website/80](#8-pontoonqlnowshfirefox-monitor-website80)

---

### 1. [pdehaan/blurts-missing-logos](https://github.com/pdehaan/blurts-missing-logos)

Checks for missing breach logos on the Firefox Monitor website.

```sh
npx pdehaan/blurts-missing-logos
```

### 2. [pdehaan/blurts-server-data-classes](https://github.com/pdehaan/blurts-server-data-classes)

The script will scrape the HIBP breaches and compare the DataClasses for each breach with the Firefox Monitor Website's ./locales/en/data-classes.ftl file.

```sh
npx pdehaan/blurts-server-data-classes
```

### 3. [pdehaan/blurts-data-classes-stats](https://github.com/pdehaan/blurts-data-classes-stats)

Statistics for Firefox Monitor breach data classes.

```sh
npx pdehaan/blurts-data-classes-stats
```

### 4. [pdehaan/blurts-kinto](https://github.com/pdehaan/blurts-kinto)

Check that latest HIBP breaches are in RemoteSettings/Kinto

```sh
npx pdehaan/blurts-kinto
```

### 5. [pdehaan/blurts-pageres](https://github.com/pdehaan/blurts-pageres)

Firefox Monitor screenshots using pageres.

This script will grab the latest breach list from the production monitor.firefox.com site, and then loop over each breach and take a cropped screenshot of the breach details header with the breach logo, name, type.

```sh
git clone https://github.com/pdehaan/blurts-pageres.git blurts-pageres
cd blurts-pageres
npm install
node index
# wait and wait and wait
```

### 5b. [pdehaan/blurts-logo-scraper](https://github.com/pdehaan/blurts-logo-scraper)

Scrape breach details logos using Puppeteer (but with fancy progress bar since it's a 9-10 minute script).

```sh
git clone https://github.com/pdehaan/blurts-logo-scraper.git
cd blurts-logo-scraper
npm install
npm run scrape
```

### 6. [pdehaan/hibp-chain-api](https://github.com/pdehaan/hibp-chain-api)

Chainable API for Have I Been Pwned breaches.

```js
// npm i pdehaan/hibp-chain-api -S
const HIBP = require("hibp-chain-api");

// Fetch the 10 largest breaches.
const breaches = (await new HIBP().getBreaches())
  .sort("-PwnCount")
  .breaches(10);
console.log(breaches);
```

### 7. [pdehaan/firefox-monitor-link-check.js](https://gist.github.com/pdehaan/3fb8532ebf12c1389d0ecadae734f1b9)

Link checker for external breach details links to `https://www.${breach.Domain}`. Enjoy!

See Gist at https://gist.github.com/pdehaan/3fb8532ebf12c1389d0ecadae734f1b9 (until I convert it to an `npx`able script).

### 8. [pontoonql.now.sh/firefox-monitor-website/80](https://pontoonql.now.sh/firefox-monitor-website/80)

Displays which Firefox Monitor locales are over 80%?

**NOTE:** The server might be slow to warm up on initial load, since it hibernates after a few hours of non-use.

This is also available as an API and CLI, via https://github.com/pdehaan/pontoonql.

```sh
npx pdehaan/pontoonql firefox-monitor-website 80
```

For the adventurous, there is also https://github.com/pdehaan/pontoon-l10n-lint which will compare the current 80%+ locales vs a list of production locales. Although that requires you to know the list of currently enabled locales on production (which can be found via the private OPs repo, or asking your friendly, neighborhood OPs fellow &mdash; or anybody with access to the OPs secrets repo).
