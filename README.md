# Ice Cream Bot

A CLI tool that finds the best local ice cream shops in any city using [Browserbase](https://www.browserbase.com/). It runs multiple web searches, fetches each shop's page, and extracts name, address, hours, and description — filtering out chains and duplicates.

## Prerequisites

- Node.js 18+
- A [Browserbase](https://www.browserbase.com/) account and API key

## Setup

```bash
git clone <repo-url>
cd ice-cream-bot
npm install
```

Set your Browserbase API key:

```bash
export BROWSERBASE_API_KEY=your_key_here
```

## Usage

```bash
npm start -- "<city name>"
```

**Examples:**

```bash
npm start -- "San Francisco, CA"
npm start -- "Austin, TX"
npm start -- "Portland, OR"
```

## Example Output

```
Searching for the best ice cream shops in San Francisco, CA...

Found 42 unique results across 4 searches. Fetching page details...

══════════════════════════════════════════════════════════════
 BEST ICE CREAM SHOPS IN SAN FRANCISCO, CA
══════════════════════════════════════════════════════════════
──────────────────────────────────────────────────────────────

  1. Bi-Rite Creamery
     Address     3692 18th St, San Francisco, CA 94110
     Hours       Mon–Thu: 11am–10pm  |  Fri–Sun: 11am–11pm
     Known for   Organic, locally sourced ice cream made in small batches...
     URL         https://biritemarket.com/creamery
```

## How It Works

1. Runs 4 search queries against the Browserbase Search API
2. Deduplicates results by URL
3. Skips media/aggregator sites (Yelp lists, Eater, Thrillist, etc.)
4. Fetches each shop's page via Browserbase and parses JSON-LD structured data, Open Graph tags, and meta descriptions
5. Filters out major chains (Baskin-Robbins, Dairy Queen, etc.)
6. Prints the top 8 results
