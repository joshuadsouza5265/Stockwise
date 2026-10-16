# StockWise Analysis v2.0

A cyberpunk-style market research dashboard for Indian NSE/BSE and US tickers. Built with Node.js, Express 5, plain HTML/CSS/JS, Chart.js, and Yahoo Finance chart/search endpoints.

## Run on Windows
1. Install Node.js 20+ (Node 24 is fine).
2. Extract this ZIP and open the `stockpulse` folder in VS Code.
3. In the terminal run `npm install`.
4. Copy `.env.example` to `.env`. AI summaries are optional; without an `OPENAI_API_KEY`, the app uses a rules-based summary and labels uncertainty.
5. Run `npm start` and open http://localhost:3000.

## Features
- India/US market toggle; NSE defaults for bare Indian tickers, `.BO` for BSE, raw US tickers when US market is selected.
- Market overview cards (NIFTY 50, SENSEX, BANK NIFTY, NIFTY IT; or S&P 500, NASDAQ, DOW, Russell 2000).
- Stock price/history charts with 1D, 5D, 1M, 3M, 1Y ranges.
- Evidence-based Stock Detective, source-linked recent headlines and headline-only sentiment.
- RSI(14), MACD(12,26,9), SMA20 and SMA50 calculated from returned historical closes.
- Watchlist, portfolio tracker, curated stock screener, browser-open price alerts, dividend events where returned by provider, paper trading and beginner learning cards.
- Clear unavailable-data errors; no fake fallback prices.

## Data and limitations
Market data and headlines come from Yahoo Finance chart/search endpoints. This is an unofficial data integration, can be delayed, rate-limited, blocked or incomplete, and is not an exchange-certified real-time feed. Screener coverage is a curated starter universe, not all NSE/BSE/US listings. The free data feed does not consistently expose earnings dates or all fundamentals. Calendar only displays dividend events that the provider actually returns. Price alerts are checked while the app is running/open and are not guaranteed push notifications. LocalStorage data remains in this browser/device and is not synced across devices.

The Stock Detective does not claim to know the exact cause of a move. It highlights headline evidence and uncertainty. Optional AI summaries require an OpenAI API key in `.env`; never expose that key in frontend files or commit `.env` to GitHub. AI output can still be wrong and must be checked against source links.

Paper trading is a local simulation only. It does not connect to a broker or place real orders. Portfolio values are estimates using the latest returned quote and may be unavailable. This app is for research/education, not investment advice.

## API smoke tests
After starting the server, open `http://localhost:3000/api/health`. You can also try `/api/quote?symbol=TCS&market=IN` or `/api/quote?symbol=AAPL&market=US`. A provider or symbol failure should return an HTTP error with a readable message, not a fabricated price.
