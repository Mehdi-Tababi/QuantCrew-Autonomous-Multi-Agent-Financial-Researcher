# QuantCrew-Autonomous-Multi-Agent-Financial-Researcher
A multi-agent AI system that autonomously fetches real-time market data and web sentiment to generate structured investment memos using local open-source LLMs.
## 🧠 Architecture: The Multi-Agent Pipeline

This application utilizes a sequential multi-agent workflow where specialized AI personas collaborate to synthesize a final report:

1. **The Quant (Senior Data Fetcher):** Uses the `yfinance` library via custom tool-calling to extract the last 30 days of closing prices for a target stock. It analyzes the mathematical trend (up, down, flat).
2. **The Analyst (News & Media Analyst):** Utilizes custom web-scraping tools to fetch real-time news headlines and articles, determining the current market sentiment (Bullish, Bearish, or Neutral).
3. **The CIO (Lead Portfolio Manager):** Synthesizes the quantitative data from the Quant and the qualitative sentiment from the Analyst to draft a final 3-paragraph investment memo, concluding with a definitive Buy, Hold, or Sell rating.

## ✨ Key Features

* **100% Local Inference:** Powered by Meta's Llama 3.1 running locally via Ollama. Ensures complete data privacy and zero API costs.
* **Custom Tool Calling:** Agents are equipped with Python-based tools (`fetch_stock_price`, `fetch_stock_news`) to interact with live external data sources.
* **Automated File Generation:** Dynamically saves the final investment memo to a formatted `.md` file for easy reading and record-keeping.
* **Graceful Error Handling:** Includes built-in safeguards to catch invalid ticker symbols and API failures before they crash the application.

## 🛠️ Prerequisites

Before running this project, ensure you have the following installed on your machine:
* **Python 3.10+**
* **Ollama** (for local LLM hosting)

You must also pull the Llama 3.1 model into your local Ollama instance:
```bash
ollama run llama3.1
```
📊 Example Output
When you run the script and input a ticker like apple, the AI orchestrates the research and outputs a file named apple_investment_memo.md that looks like this:
# Investment Memo: apple

Subject: Investment Memo for Apple Inc. (AAPL)

The price data from our Quant team indicates a downward trend in AAPL's stock performance over the past month, with prices declining steadily from $264.72 on March 2nd to $253.22 on March 31st. This decline is more pronounced towards the end of the period, suggesting potential selling pressure or reduced investor confidence. While such trends are not uncommon and can be market-driven, it is essential to consider sentiment analysis to form a comprehensive view.

Our Analyst team provided sentiment analysis of recent news related to Apple Inc., which showed mixed but largely bearish sentiment. Some concerns include increased competition from new entrants in the technology sector, potential supply chain disruptions due to COVID-era policies, and questions surrounding Apple's plans for its cash reserves. However, there were also mentions of positive earnings reports, strong brand loyalty, and innovative product pipeline developments.

Considering these two perspectives together, our final rating is cautious. Based on both the raw price data indicating a decline in stock performance over the viewed period and the mixed sentiment from recent news that leans more bearish than bullish, we recommend **Holding** AAPL for now. While the company maintains its positions as a technology giant with promising product lines and stable earnings records, this period seems to suggest caution before any further significant investment decisions.

**Final Recommendation:** HOLD


