[Grailed Scraper](https://apify.com/generativa/grailed-scraper?fpr=data)

Extract listings from [Grailed.com](https://www.grailed.com) - the leading marketplace for streetwear, designer fashion, and vintage clothing.

## Features

- **Fast & Efficient** - Direct API integration, no browser required
- **Designer Filtering** - Focus on specific brands (Supreme, Palace, Bape, Off-White, etc.)
- **Size & Condition Filters** - Target specific inventory
- **Price Range** - Filter by min/max price
- **Seller Information** - Get seller ratings, transaction count, trusted status
- **Price History** - Track price drops on listings
- **Shipping Info** - Full shipping rates by region

## Use Cases

### Resellers & Flippers

- Research market prices before buying
- Find underpriced listings
- Monitor specific designers for deals

### Brand Monitoring

- Track where products are being resold
- Monitor pricing trends
- Analyze market positioning

### Market Research

- Analyze streetwear market trends
- Compare prices across designers
- Study resale market dynamics

### Data Analysis

- Build pricing models
- Create price guides
- Track inventory levels

## Input Example

```
{
  "designers": ["Supreme"],
  "categories": ["tops"],
  "sizes": ["L", "XL"],
  "priceMin": 50,
  "priceMax": 500,
  "condition": "is_gently_used",
  "maxItems": 100
}
```

## Output Data

Each listing includes comprehensive data:

```
{
  "id": "91346183",
  "url": "https://www.grailed.com/listings/91346183",
  "title": "Supreme red rum baseball jersey",
  "designer": "Supreme",
  "designers": ["Supreme"],
  "category": "tops",
  "categoryPath": "tops.jerseys",
  "department": "menswear",
  "size": "l",
  "price": 68,
  "priceDrops": [95, 85, 76, 68],
  "currency": "USD",
  "condition": "is_gently_used",
  "color": "green",
  "location": "United States",
  "images": ["https://media-assets.grailed.com/..."],
  "photoCount": 7,
  "seller": {
    "id": "832674",
    "username": "Tlam",
    "ratingAverage": 4.95,
    "ratingCount": 607,
    "totalBoughtAndSold": 1274,
    "trustedSeller": true,
    "avatarUrl": "https://..."
  },
  "shipping": {
    "us": { "amount": 9, "enabled": true },
    "ca": { "amount": 0, "enabled": false },
    "uk": { "amount": 0, "enabled": false }
  },
  "buyNow": true,
  "makeOffer": true,
  "isSold": false,
  "soldPrice": null,
  "soldAt": null,
  "createdAt": "2026-01-23T03:56:12.810Z",
  "updatedAt": "2026-01-27T03:02:23.124Z",
  "scrapedAt": "2026-01-27T03:14:57.847Z"
}
```

## Input Parameters

| Parameter | Type | Default | Description |
| --- | --- | --- | --- |
| `searchQuery` | String | - | Search term (e.g., "box logo hoodie") |
| `designers` | Array | - | Filter by designer/brand names |
| `categories` | Array | - | Filter by category (tops, bottoms, footwear, etc.) |
| `sizes` | Array | - | Filter by size (S, M, L, XL, 9, 10, etc.) |
| `priceMin` | Integer | - | Minimum price in USD |
| `priceMax` | Integer | - | Maximum price in USD |
| `condition` | String | - | Filter by condition |
| `maxItems` | Integer | 1000 | Maximum items to scrape |
| `proxyConfiguration` | Object | Apify Proxy | Proxy settings |
| `debugLog` | Boolean | false | Enable verbose logging |

### Condition Values

- `is_new` - New/Never Worn
- `is_gently_used` - Gently Used
- `is_used` - Used
- `is_very_worn` - Very Worn
- `is_not_specified` - Not Specified

## Proxy Configuration

For best results, use Apify Proxy:

```
{
  "proxyConfiguration": {
    "useApifyProxy": true
  }
}
```

## Pricing

This actor uses **pay-per-result** pricing - you only pay for what you scrape:

| Cost Component | Price |
| --- | --- |
| Per listing scraped | $0.005 |
| Minimum per run | $0.01 |

### Cost Examples

| Volume | Cost |
| --- | --- |
| 100 listings | $0.51 |
| 500 listings | $2.51 |
| 1,000 listings | $5.01 |
| 3,000 listings | $15.01 |

**3-day free trial** included for new users.

## Performance

This actor uses direct API integration (no browser) for fast, efficient scraping:

- ~40 listings per API call
- Low memory usage (~128-256MB)
- Fast execution (1000 items in ~30 seconds)

## Tips

1. **Start small** - Test with `maxItems: 50` before large runs
2. **Filter by designer** - More focused and efficient than broad searches
3. **Use price filters** - Narrow down to relevant price ranges
4. **Check priceDrops** - Identify items with recent price reductions

## Limitations

- **Active listings only** - Sold items require authentication and are not available via public API
- **Public data only** - No login required or supported
- **Rate-limited** - Respects Grailed's servers with built-in delays

## Legal Disclaimer

This actor extracts publicly available data from Grailed.com. Users are responsible for ensuring their use complies with:

- Grailed's Terms of Service
- Applicable laws and regulations
- Data protection requirements

Use for legitimate purposes such as market research, price comparison, and personal use. Do not use for harassment, spam, or unauthorized commercial purposes.

## Support

For issues or feature requests, please open an issue on the actor's page.