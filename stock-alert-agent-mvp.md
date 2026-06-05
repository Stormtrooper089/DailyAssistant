# Agentic Daily Assistant MVP

## Objective

Create an agentic assistant that starts with two daily workflows:

1. Indian market alerts for NSE portfolio and wishlist stocks.
2. A day assistant that reads mail signals, suggests tasks, and prepares a daily briefing.

## Market Alert Objective

Monitor NSE stocks in two groups:

- Portfolio: stocks currently owned.
- Wishlist: stocks being watched for possible entry.

The assistant checks user-defined conditions and sends alerts when those conditions pass.

## Example Alert Conditions

Portfolio alerts:

- Alert if price rises above target sell price.
- Alert if price falls below stop-loss price.
- Alert if price drops more than 5% in a day.
- Alert if holding reaches a desired profit percentage.
- Alert if news sentiment or earnings date needs review.

Wishlist alerts:

- Alert if price falls below desired buy price.
- Alert if price crosses above a breakout level.
- Alert if volume is unusually high.
- Alert if stock is near 52-week low or high.
- Alert if valuation or technical condition becomes attractive.

## First Safe MVP

Start with price-based rules only:

1. Add stocks to Portfolio or Wishlist.
2. Store alert rules for each stock.
3. Fetch or enter the latest price.
4. Evaluate rules.
5. Show alerts in the app.
6. Later, send alerts through email, SMS, WhatsApp, Telegram, or push notifications.

## Rule Format

Each rule should have:

- Stock symbol
- Group: Portfolio or Wishlist
- Metric: current price
- Operator: above, below, changes by percentage
- Threshold
- Alert message
- Status: active, triggered, dismissed

Examples:

- `HDFCBANK price below 1520 -> Consider buying HDFCBANK`
- `RELIANCE price above 2850 -> Review profit booking`
- `TCS price below 3700 -> Protection alert`

## Automation Loop

1. Load watchlist and portfolio.
2. Fetch latest market prices.
3. Evaluate active rules.
4. Create alert records for passed conditions.
5. Notify the user.
6. Avoid duplicate notifications unless the condition resets and passes again.

## NSE Master List

The prototype includes a local seeded list of popular NSE equities for search and selection.

For a production backend, replace or sync that seed list from NSE's official "Securities available for Equity segment" CSV (`EQUITY_L.csv`) published from the NSE "Securities available for Trading" page.

Recommended backend sync:

1. Download the official NSE equity CSV on a schedule.
2. Store symbol, company name, series, ISIN, and listing metadata.
3. Use the local database for search/autocomplete.
4. Keep user portfolio holdings separate from the symbol master.

## Portfolio Tracking

Portfolio holdings should store:

- NSE symbol
- Company name
- Quantity owned
- Average buy price
- Current market price
- Invested value
- Current value
- Profit/loss amount
- Profit/loss percentage

Wishlist stocks can store quantity and average buy price as zero, while still supporting price alerts.

## Data Source Options

Possible sources for live prices:

- Broker API, if available.
- Market-data API such as a broker API, NSE-compatible feed, Yahoo Finance-compatible package, Alpha Vantage, Finnhub, Polygon, or Twelve Data.
- Manual price entry for early testing.

For the first working prototype, manual or mock prices are enough. Real notifications and live prices should be added after the rule engine is correct.

## Safety Notes

- This assistant should alert, summarize, and remind. It should not place trades unless a separate brokerage integration and explicit approval flow are built.
- Alerts are not financial advice.
- All conditions should be user-defined and editable.
- Mail automations should not send replies, create calendar events, forward messages, or share sensitive content without explicit approval.

## Day Assistant

The day assistant should eventually connect to Gmail or Outlook and perform a morning scan:

- Summarize important unread mail.
- Identify deadlines and pending replies.
- Suggest tasks from mail.
- Highlight meetings and prep work.
- Draft replies or reminders, waiting for approval before sending.
- Produce a short "what's up for today" briefing.

First prototype behavior:

- Uses local sample mail signals.
- Generates a daily briefing.
- Creates suggested tasks.
- Shows automation cards for morning mail scan, follow-up finder, and end-of-day review.
- Lets the user mark suggested tasks done.

## Next Build Step

Build a local app with:

- Portfolio and Wishlist tabs.
- Add stock form.
- Add alert condition form.
- Price update field.
- Alert inbox.
- Rule evaluation button.
- Day Assistant tab.
- Mail signal list.
- Suggested task list.
- Approval-first automation actions.
