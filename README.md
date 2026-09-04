# Custom Welcome Book — places tiles

A monthly build that turns Foursquare's open places dataset into one small map-tile file used by the Custom Welcome Book builder to suggest nearby restaurants, cafés, groceries, parks, breweries/wineries, and museums to a host — dead businesses already removed.

**How it works.** GitHub Actions (`.github/workflows/build-tiles.yml`) runs on the 16th of each month and on demand (Actions tab → *Build places tiles* → *Run workflow*). It reads Foursquare's latest release straight from Hugging Face, keeps US places that are open and fall in our six categories, builds a PMTiles file with tippecanoe, and publishes it as the release asset **`tiles`** (`fsq-us.pmtiles` + `manifest.json`). The Cloudflare Worker range-reads that file; nothing else is deployed here.

**Data notice.** This repository's release assets contain data from **Foursquare OS Places**, © Foursquare Labs, Inc., licensed under the [Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0). Source: https://huggingface.co/datasets/foursquare/fsq-os-places · docs: https://docs.foursquare.com/data-products/docs/access-fsq-os-places. The build scripts in this repository are © Custom Welcome Book.
