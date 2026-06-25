[Grailed Scraper](https://apify.com/lulzasaur/grailed-scraper?fpr=data)

# Grailed Scraper

Apify Actor for scraping Grailed.com designer fashion marketplace listings. Uses the Grailed Algolia search API for fast, reliable data extraction without browser rendering.

## Features

- Search Grailed listings by keyword (designer names, item types, styles)
- Filter by price range, department (menswear/womenswear), and condition
- Two modes: quick search results or full detail scraping via listing API
- Extracts designer names, prices, sizes, conditions, photos, and seller info
- Paginates through Algolia API results (up to 1000 listings per query)
- Detail mode fetches complete listing data including full descriptions and all photos

## Input

| Field | Type | Default | Description |
| --- | --- | --- | --- |
| `searchQueries` | string[] | `["jordan 1"]` | Search terms to scrape |
| `maxListings` | integer | `100` | Max listings per query (0 = max available, up to 1000) |
| `scrapeDetails` | boolean | `false` | Fetch full details from listing API |
| `minPrice` | integer | - | Minimum price filter |
| `maxPrice` | integer | - | Maximum price filter |
| `department` | string | `""` | `menswear`, `womenswear`, or empty for all |
| `condition` | string | `""` | `is_new`, `is_gently_used`, `is_used`, `is_very_worn`, or empty for all |
| `proxyConfiguration` | object | `{}` | Proxy settings (optional) |

### Example Input

```
{
    "searchQueries": ["rick owens ramones", "supreme box logo"],
    "maxListings": 50,
    "scrapeDetails": true,
    "minPrice": 100,
    "maxPrice": 500,
    "department": "menswear"
}
```

## Output

### Search-only mode (`scrapeDetails: false`)

```
{
    "listingId": 12345678,
    "title": "Rick Owens Ramones Low",
    "price": 350,
    "designer": "Rick Owens",
    "designerNames": ["Rick Owens"],
    "department": "menswear",
    "category": "footwear",
    "subcategory": "low-top-sneakers",
    "size": "43",
    "condition": "Gently Used",
    "imageUrl": "https://process.fs.grailed.com/...",
    "sold": false,
    "sellerUsername": "fashionseller",
    "url": "https://www.grailed.com/listings/12345678",
    "searchQuery": "rick owens ramones",
    "scrapedAt": "2026-03-17T12:00:00.000Z"
}
```

### Detail mode (`scrapeDetails: true`)

Includes all search fields plus:

```
{
    "description": "Rick Owens Ramones low-top sneakers in black...",
    "photos": [
        "https://process.fs.grailed.com/photo1.jpg",
        "https://process.fs.grailed.com/photo2.jpg"
    ],
    "photoCount": 5,
    "sellerLocation": "New York, NY",
    "sellerRating": 4.9,
    "sellerListingCount": 42,
    "createdAt": "2026-03-10T08:30:00.000Z",
    "updatedAt": "2026-03-15T14:20:00.000Z"
}
```

## How It Works

1. Queries the Grailed Algolia search API directly (no browser needed)
2. Builds Algolia POST requests with search terms, numeric filters, and facet filters
3. Paginates through results (100 per page, up to 10 pages = 1000 max per query)
4. Optionally fetches individual listing detail API for richer data
5. Uses CheerioCrawler for detail page requests (handles retries, proxies, concurrency)

## Technical Details

Grailed uses Algolia for its search infrastructure with publicly accessible API keys. This scraper calls the Algolia API directly for search, which is significantly faster and more reliable than scraping HTML. For detail pages, it uses the Grailed listing API endpoint.

## Quick Start

```
$apify run --purge
```

## Deploy to Apify

```
apify login
apify push
```

## Related Scrapers

More marketplace scrapers and data tools by [lulzasaur](https://apify.com/lulzasaur):

- [AbeBooks Scraper](https://apify.com/lulzasaur/abebooks-scraper) — Rare and used books
- [Bonanza Scraper](https://apify.com/lulzasaur/bonanza-scraper) — Online marketplace listings
- [Contractor License Verifier](https://apify.com/lulzasaur/contractor-license-scraper) — Multi-state license verification
- [Craigslist Scraper](https://apify.com/lulzasaur/craigslist-scraper) — Classifieds and for-sale posts
- [Goodreads Scraper](https://apify.com/lulzasaur/goodreads-scraper) — Book ratings and reviews
- [Houzz Scraper](https://apify.com/lulzasaur/houzz-scraper) — Home improvement professionals
- [IMDb Scraper](https://apify.com/lulzasaur/imdb-scraper) — Movie and TV show data
- [Nurse License Verifier](https://apify.com/lulzasaur/nurse-license-scraper) — State nursing board verification
- [OfferUp Scraper](https://apify.com/lulzasaur/offerup-scraper) — Local marketplace listings
- [Poshmark Scraper](https://apify.com/lulzasaur/poshmark-scraper) — Fashion resale marketplace
- [PSA Population Report](https://apify.com/lulzasaur/psa-pop-scraper) — Card grading data
- [Redfin Scraper](https://apify.com/lulzasaur/redfin-scraper) — Real estate listings and prices
- [Reverb Scraper](https://apify.com/lulzasaur/reverb-scraper) — Music gear marketplace
- [StubHub Scraper](https://apify.com/lulzasaur/stubhub-scraper) — Event ticket prices
- [Swappa Scraper](https://apify.com/lulzasaur/swappa-scraper) — Used electronics marketplace
- [TCGPlayer Scraper](https://apify.com/lulzasaur/tcgplayer-scraper) — Trading card prices
- [ThriftBooks Scraper](https://apify.com/lulzasaur/thriftbooks-scraper) — Used book prices
- [Thumbtack Scraper](https://apify.com/lulzasaur/thumbtack-scraper) — Local service professionals