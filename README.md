## Project Title and One-Line Summary

**Does SBP Monetary Policy Communication Tone Affect KSE-100 Returns? A FinBERT + ARDL Analysis**

This project examines whether the tone of State Bank of Pakistan monetary policy communication affects short-run KSE-100 returns using FinBERT-based sentiment scoring and an ARDL econometric framework.

## Motivation / Research Question

Central bank communication can influence investor expectations, especially when markets closely follow monetary policy signals. In Pakistan, SBP monetary policy statements and MPC minutes may contain optimistic, neutral, or cautious language that investors respond to in the stock market.

The main research question is: **Does the tone of SBP monetary policy communication have a statistically significant effect on KSE-100 returns?**

## Data Sources

The textual data consists of **SBP Monetary Policy Committee minutes/statements from 2016 to 2025**, collected from the official State Bank of Pakistan website. Around **70 monetary policy documents** were cleaned and converted into text format for sentiment scoring.

The stock market data consists of **KSE-100 daily index data**, matched to the MPC release date. If the document was released on a non-trading day, the next available trading day was used to capture the market reaction. The dependent variable is the KSE-100 log return on the matched trading date.

The interest rate control variable is the **KIBOR rate**, specifically the relevant offer rate, collected from SBP/KIBOR historical rate data. KIBOR is used to control for the monetary policy and market interest-rate environment.

## Methodology Summary

First, all SBP monetary policy documents were cleaned and processed for sentiment analysis. FinBERT, a finance-specific transformer model, was used to classify sentence-level sentiment as positive, negative, or neutral. These scores were aggregated into a document-level net tone measure.

The main tone variable was calculated as a net sentiment score, where higher values indicate a more positive or optimistic communication tone and lower values indicate a more negative or cautious tone.

After constructing the dataset, stationarity was tested using the Augmented Dickey-Fuller test. Stock returns and FinBERT tone were found to be stationary, while KIBOR rate was non-stationary in level form. Because the variables were a mix of stationary and non-stationary series, an ARDL approach was used.

The model was estimated using an **ARDL(2,1,1)** structure, with lag selection based on the Akaike Information Criterion. A bounds test was then used to check for cointegration. The unrestricted error correction model was estimated with robust standard errors to account for heteroskedasticity. A simple OLS model was also estimated as a robustness check.

## Key Findings

The results do not show a statistically significant short-run or long-run relationship between SBP communication tone and KSE-100 returns. The coefficient on tone was not statistically significant in the preferred specification.

The bounds test provided only weak or borderline evidence of cointegration. After correcting for heteroskedasticity using robust standard errors, the evidence for a stable long-run relationship became weaker.

Overall, the results suggest that FinBERT-measured SBP communication tone does not have a strong or statistically reliable effect on KSE-100 returns in this sample.

## Limitations

The study has some important limitations. First, the sample size is small, with around 64–70 observations after matching monetary policy documents with market dates. Second, the data is at meeting frequency, not regular daily or monthly frequency, which limits the strength of time-series inference.

Third, possible structural breaks were not formally tested. Pakistan’s economy experienced major shocks during the sample period, including COVID-19, inflationary pressure, exchange-rate instability, and changes in monetary policy stance. These events may affect the relationship between tone and stock returns.

Finally, FinBERT is trained on financial text generally, not specifically on Pakistani central bank communication, so some local monetary policy language may not be perfectly captured.

## How to Reproduce

1. Download SBP monetary policy documents from the official SBP website.
2. Convert all documents into `.txt` format.
3. Run the text-cleaning script to remove unnecessary formatting, page numbers, tables, and irrelevant text.
4. Run the FinBERT sentiment script to generate sentence-level sentiment scores.
5. Aggregate sentence-level scores into document-level net tone.
6. 
7. Download KSE-100 daily index data and calculate log returns.
8. Match each MPC document date to the same trading day, or the next available trading day if the market was closed.
9. Add KIBOR rates as the interest-rate control variable.
10. Run the ADF stationarity tests.
11. Estimate the ARDL model using AIC-based lag selection.
12. Run the bounds test, UECM, robust standard errors, and OLS robustness check.
13. Export the final regression tables and diagnostic results.
