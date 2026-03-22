# Real Estate Comp Scraper

Finds undervalued active listings in a zip code by scoring them against comparable properties.

## Setup

```bash
pip install -r scraper/requirements.txt
export RAPIDAPI_KEY="your-rapidapi-key"
```

## Usage

```bash
# Default: top 15 deals in 46220
python -m scraper.main

# Custom options
python -m scraper.main --zip 46220 --top 10 --min-score 20

# Export to CSV
python -m scraper.main --csv deals.csv
```

## Scoring (0-100)

| Factor | Points | What it measures |
|---|---|---|
| Price vs comps | 40 | $/sqft compared to median of same type + bedroom count |
| Below Zestimate | 25 | Gap between list price and Zillow's automated valuation |
| Days on market | 20 | Longer DOM = more motivated seller |
| Price reduction | 15 | Seller has already cut the price |

## API Budget

Uses the `zillow-com1` API on RapidAPI. Basic tier = 50 requests/month.
A typical run uses 1-2 API calls (1 per page of results).
