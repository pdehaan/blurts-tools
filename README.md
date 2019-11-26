# blurts-tools

Link to a bunch of different Firefox Monitor tools

## [pdehaan/blurts-missing-logos](https://github.com/pdehaan/blurts-missing-logos)

Checks for missing breach logos on the Firefox Monitor website.

```sh
npx pdehaan/blurts-missing-logos
```

## [pdehaan/blurts-server-data-classes](https://github.com/pdehaan/blurts-server-data-classes)

The script will scrape the HIBP breaches and compare the DataClasses for each breach with the Firefox Monitor Website's ./locales/en/data-classes.ftl file.

```sh
npx pdehaan/blurts-server-data-classes
```

## [pdehaan/blurts-data-classes-stats](https://github.com/pdehaan/blurts-data-classes-stats)

Statistics for Firefox Monitor breach data classes.

```sh
npx pdehaan/blurts-data-classes-stats
```

## [pdehaan/blurts-kinto](https://github.com/pdehaan/blurts-kinto)

Check that latest HIBP breaches are in RemoteSettings/Kinto

```sh
npx pdehaan/blurts-kinto
```

## [pdehaan/blurts-pageres](https://github.com/pdehaan/blurts-pageres)

Firefox Monitor screenshots using pageres.

This script will grab the latest breach list from the production monitor.firefox.com site, and then loop over each breach and take a cropped screenshot of the breach details header with the breach logo, name, type.

```sh
git clone https://github.com/pdehaan/blurts-pageres.git blurts-pageres
cd blurts-pageres
npm install
node index
# wait and wait and wait
```

## [pdehaan/hibp-chain-api](https://github.com/pdehaan/hibp-chain-api)

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
