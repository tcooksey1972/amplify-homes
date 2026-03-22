# Amplify Homes

A real estate toolkit combining an AWS Amplify listing app with a Python-based deal-finding scraper. Built for the Indianapolis metro area.

---

## Projects

### 1. Amplify Homes Web App

A React-based home listing demo app powered by AWS Amplify.

- **Frontend:** React 17 + Amplify UI
- **Backend:** AWS AppSync (GraphQL) + DynamoDB
- **Auth:** API Key + IAM

#### Quick Start

```bash
npm install
npm start
```

See the [Amplify docs](https://docs.amplify.aws/) for backend setup (`amplify init`, `amplify push`).

---

### 2. Real Estate Comp Scraper

A Python CLI tool that finds undervalued active listings by scoring them against comparable properties in a zip code. Uses the Zillow RapidAPI to pull live listing data and applies a weighted scoring algorithm across four factors: price vs. comps, Zestimate gap, days on market, and price reductions.

**Default target:** Zip code **46220** (Broad Ripple / Meridian-Kessler, Indianapolis)

#### Quick Start

```bash
pip install -r scraper/requirements.txt
export RAPIDAPI_KEY="your-rapidapi-key"
python -m scraper.main
```

#### Example Output

```
  #1  [A]  Score: 58.3/100
  1234 N Meridian St, Indianapolis, IN 46220
  Price: $275,000   |   3bd/2ba   |   1,800 sqft
  $/sqft: $153   |   Zestimate: $315,000 (+40,000)
  Scores → comps: 22.5/40  zest: 17.8/25  DOM: 14.9/20  reduction: 3.1/15
```

See [`scraper/README.md`](scraper/README.md) for full documentation — scoring methodology, CLI options, API budget details, and troubleshooting.

---

## Repository Structure

```
amplify-homes/
├── src/                    # React app source (Amplify frontend)
├── public/                 # Static assets
├── amplify/                # AWS Amplify backend config (AppSync, DynamoDB)
├── scraper/                # Python comp scraper
│   ├── main.py             #   CLI entry point
│   ├── scoring.py          #   Comp analysis & deal scoring engine
│   ├── zillow_client.py    #   Zillow RapidAPI client
│   ├── requirements.txt    #   Python dependencies
│   └── README.md           #   Full scraper documentation
├── package.json            # Node.js dependencies
└── README.md               # This file
```

---

## License

Private repository — not for redistribution.
