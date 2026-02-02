# Excel Mutual Fund Performance Comparison

An Excel dashboard that compares the performance of three mutual funds from 1998 to 2024. The goal was to see how a value fund, a growth fund, and a passive index fund each performed and whether they actually did what they said they would do.

## The Funds

Three funds were picked to represent different ways of investing in the market.

| Fund | Ticker | Strategy | Assets |
|------|--------|----------|--------|
| Macquarie Growth and Income Fund | FGINX | Large-Cap Value | $1.5B |
| Virtus Silvant Focused Growth Fund | PGWCX | Large-Cap Growth | $1.86B |
| Shelton Capital S&P 500 Index Fund | SPFIX | Passive S&P 500 |  $316.3M |

FGINX invests in large-cap stocks that pay dividends and are seen as undervalued. It uses a bottom-up approach to pick stocks with strong fundamentals. PGWCX is focused on long-term growth and typically holds around 25 to 35 high-growth companies. SPFIX just tracks the S&P 500 by holding the same stocks in the index at their market-cap weights.

## Data

- **Sources:** Wharton Research Data Services (WRDS), Fidelity Fund Screener, Ken French's Data Library
- **Returns:** Monthly data for all three funds from January 1998 to December 2024
- **Factor Data:** Monthly Fama-French 3 and 4 factor returns from Ken French's library
- **Holdings:** 2025 portfolio reports were used to look at the top 15 holdings for each fund

## Executive Summary

This project looked at whether these three funds lived up to their stated investment styles and how that played out in real performance over time. Sharpe and Treynor ratios, multi-factor alphas, and Fama-French betas were calculated over the full period from 1998 to 2013 and split into two smaller windows to check for consistency. A retirement withdrawal simulation was also run from 2014 to 2024 to see how each fund would hold up if someone was actually pulling money out.

### Key Results
- **Best Risk-Adjusted Returns (1998-2013):** FGINX with a Sharpe of 0.3142 and Treynor of 0.0535
- **Strongest Absolute Returns (Retirement Sim):** PGWCX finished just above $1M
- **Most Consistent Over Time:** SPFIX stayed steady across all periods with very little style drift

All three funds ended up matching their stated strategies pretty closely when you looked at their actual holdings.

## Performance Analysis

Over the full period, FGINX came out on top when it came to risk-adjusted returns. A big reason for that is that it held up well during both the dot-com crash and the 2008 financial crisis. SPFIX was close behind, and PGWCX lagged because growth stocks got hit hard during those downturns.

| Fund | Sharpe Ratio | Treynor Ratio | Alpha (1-Factor) | Alpha (3-Factor) | Alpha (4-Factor) |
|------|-------------|---------------|-------------------|-------------------|-------------------|
| FGINX | 0.3142 | 0.0535 | -0.0013 | -0.0058 | -0.0091 |
| PGWCX | 0.2453 | 0.0438 | -0.0120 | -0.0007 | -0.0135 |
| SPFIX | 0.3022 | 0.0507 | -0.0040 | -0.0011 | 0.0005 |

When you break it into two subperiods, the story changes a bit. PGWCX had a rough first half but came back strong in the second. SPFIX was the most stable of the three across both windows.

| Fund | Period | Sharpe Ratio | Treynor Ratio |
|------|--------|-------------|---------------|
| FGINX | 1998-2006 | 0.2385 | 0.0398 |
| FGINX | 2007-2013 | 0.3953 | 0.0693 |
| PGWCX | 1998-2006 | 0.0893 | 0.0155 |
| PGWCX | 2007-2013 | 0.4825 | 0.0878 |
| SPFIX | 1998-2006 | 0.2360 | 0.0386 |
| SPFIX | 2007-2013 | 0.3781 | 0.0657 |

## Factor Exposure Analysis

The Fama-French betas were used to check whether each fund was actually investing the way it said it was. Each fund's factor loadings were compared against its stated strategy.

FGINX had a positive HML beta and a near-zero SMB beta, which confirms it was tilted toward value stocks and stayed in large-cap territory. PGWCX had a strongly negative HML beta and a positive momentum beta, which lines up with a growth and momentum strategy. SPFIX was close to zero across all factors, which is exactly what you would expect from an index fund that just tracks the market.

The biggest change over time was in PGWCX. Its momentum beta dropped from 0.267 in the first subperiod down to 0.026 in the second. This is likely because the fund pulled back on momentum exposure after the 2008 crisis.

## Holdings Validation

The top 15 holdings from each fund's 2025 portfolio report were looked at to see if they matched up with what the factor analysis showed.

FGINX was loaded up on traditional value names like Citigroup, Wells Fargo, Exxon Mobil, and Verizon. Most of the holdings had higher book-to-market ratios and were classified as Big Value. PGWCX was dominated by mega-cap growth stocks like NVIDIA, Apple, and Microsoft. Almost all of them were classified as Big Growth with very low book-to-market ratios. SPFIX looked a lot like the current S&P 500, which is pretty growth-heavy right now because of how big tech has gotten. That is not a style choice by the fund, it is just where the market is.

All three funds checked out. Their holdings matched what the factor betas were showing.
<img width="1081" height="330" alt="image" src="https://github.com/user-attachments/assets/932ff6e3-d247-4edc-98e1-5979c928c84a" />

## Retirement Simulation

To put this into a real-world scenario, a retirement portfolio was modeled starting in January 2014. The setup was a $1M starting balance, $8,000 in monthly withdrawals after a 22% tax rate, and no additional contributions. The portfolio was tracked through December 2024.

| Allocation | Ending Balance | Volatility |
|------------|---------------|------------|
| 100% PGWCX | ~$1,000,000+ | Highest |
| 100% SPFIX | ~$700,000 | Moderate |
| 1/3 Each Fund | ~$600,000 | Moderate |
| 100% FGINX | ~$0 | Lowest |

The biggest takeaway here was FGINX. Its returns just were not enough to keep up with the monthly withdrawals, and the portfolio ran out over time. PGWCX ended the strongest but had a lot of ups and downs along the way. SPFIX and the equal-weight mix both did well, with SPFIX ending up with a higher balance.

<img width="985" height="383" alt="image" src="https://github.com/user-attachments/assets/1af4bfed-4b29-4778-af96-5e62d22eaf72" />

This simulation was looked at from the perspective of someone investing in 2013. At that point, both the dot-com crash and the 2008 crisis had already happened, so it would have made sense to lean toward stability. Putting most of the money into SPFIX and using FGINX as a buffer against big market drops was a reasonable call at the time, even though PGWCX ended up winning on raw returns.

## Limitations and Considerations

### Growth Fund Volatility
PGWCX was the most sensitive to market conditions of the three funds. Its momentum beta swung a lot between the two subperiods and its performance in 1998 to 2006 was a lot weaker than the other funds. Anyone looking at this fund should know that it can take some big hits when the market turns.

### Index Composition Shifts
SPFIX is supposed to be neutral, but its holdings shift as the market changes. Right now it is heavily tilted toward growth because of how large tech companies have become in the S&P 500. If the market rotates, the fund will shift with it.

### Withdrawal Sustainability
The retirement sim showed that fund selection matters a lot when you are pulling money out. A portfolio that was only in the value fund did not make it. A diversified approach or just going with the index fund worked a lot better for keeping up with withdrawals over time.

## Future Enhancements

With more time and data, this project could be expanded to include things like:
- Adding small-cap, international, and bond funds to the comparison
- Modeling different withdrawal rates and adjusting for inflation
- Building an allocation tool that adjusts based on how much risk someone is comfortable with
- Adding transaction costs and rebalancing into the retirement simulation

## Conclusion

The dashboard shows that value, growth, and passive strategies all have different tradeoffs when it comes to risk and return. All three funds did a good job of sticking to their stated investment styles throughout the period. The factor analysis and the holdings review backed each other up, which shows these funds are doing what they say they are doing. The retirement simulation added a practical side to it, showing that picking the right fund matters a lot for long-term sustainability. It is not just about which fund did the best on paper, it is about which fund actually works for your situation.

<img width="1401" height="597" alt="image" src="https://github.com/user-attachments/assets/31b1d9ad-ba27-41c4-8919-3176ea79b197" />
