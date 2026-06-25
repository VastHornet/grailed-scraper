[Grailed Scraper](https://apify.com/benthepythondev/grailed-scraper?fpr=data)

# Grailed Scraper - Luxury Fashion Marketplace

Scrape luxury fashion listings from Grailed, the leading marketplace for designer and streetwear clothing.

## Features

- **Search Mode**: Search for any item by keyword
- **Designer Mode**: Browse all listings from a specific designer
- **Single Listing Mode**: Scrape detailed data from a specific listing URL
- **Deal Score**: AI-calculated score (0-100) to identify the best deals
- **Filters**: Price range, category, condition, marketplace section

## Output Data

Each listing includes:

| Field | Description |
| --- | --- |
| `listing_id` | Unique Grailed listing ID |
| `title` | Item title/description |
| `designer` | Brand/designer name (Supreme, Rick Owens, etc.) |
| `price` | Current listing price |
| `original_price` | Original/retail price if available |
| `discount_percent` | Calculated discount percentage |
| `size` | Item size |
| `condition` | Item condition (New, Gently Used, Used, etc.) |
| `category` | Category (Tops, Bottoms, Footwear, etc.) |
| `color` | Item color |
| `seller_name` | Seller username |
| `seller_rating` | Seller rating (out of 5) |
| `seller_transactions` | Number of completed sales |
| `deal_score` | AI deal score (0-100) - higher is better |
| `url` | Direct link to listing |
| `photos` | Array of photo URLs |

## Deal Score Explained

The deal score (0-100) considers:

- **Discount from original price** (+30 max)
- **Item condition** (+15 for new items)
- **Seller reputation** (+5 for top-rated sellers)
- **Seller experience** (+5 for experienced sellers)

Higher scores indicate better deals for buyers.

## Example Use Cases

1. **Resellers**: Find underpriced items to flip
2. **Fashion Enthusiasts**: Track prices on grail pieces
3. **Market Research**: Analyze pricing trends by designer
4. **Inventory Sourcing**: Source inventory for vintage shops

## Popular Designers on Grailed

- Supreme, Rick Owens, Balenciaga
- Raf Simons, Maison Margiela, Yohji Yamamoto
- Chrome Hearts, Undercover, Kapital
- Bape, Stone Island, Comme des Garcons

## Pricing

$3.00 per 1,000 results

## Support

For issues or feature requests, contact the developer.