# Project-EWP-GARCH-Model
Modeling and Forecasting Equally Weighted Portfolio Volatility: A GARCH(1,1) Approach

In this project, we analyze the daily log-returns of the equally weighted portfolio using the csv file provided portfolio and model its conditional volatility using a GARCH(1,1) framework, extended to include a jump component. Our goal is to capture volatility clustering and persistence typical of financial time series.

A standard GARCH(1,1) model assumes: 𝑟𝑡=𝜇+√ℎ𝑡𝜀𝑡,𝜀𝑡~𝑁(0,1)
With conditional variance : ℎ𝑡=𝜔+𝛼⁡𝑟𝑡−12+𝛽⁡ℎ𝑡−1
Where 𝜔,𝛼,𝛽>0 and 𝛼+𝛽<1 to ensure stationary and mean reversion.

Volatility Forecasting : Once the parameters are estimated, the conditional variance can be forecasted as follows:
For the first forecast step: ℎ𝑇+1=𝜔+𝛼⁡𝑟𝑇2+𝛽ℎ𝑇
For subsequent steps (assuming 𝐸[𝑟𝑡2]=ℎ𝑡): ℎ𝑇+𝑘=𝜔+(𝛼+𝛽)ℎ𝑇+𝑘−1,𝑘≥2.
The forecasted volatility is then obtained by taking the square root: 𝜎𝑇+𝑘=√ℎ𝑇+𝑘.

Results & Financial Interpretation
Conditional Volatility & Clustering The model captures the conditional volatility √ℎ𝑡 which is dynamically driven by past squared returns and previous variance. Our results clearly show volatility clustering, meaning that large shocks tend to be followed by periods of high volatility. The out-of-sample forecast over a 30-day horizon reveals an upward trend in conditional volatility. This increase indicates that recent large movements in returns have elevated the risk level, and this heightened volatility is expected to increase for at least 30 days before gradually reverting to its long-run average, given by:
𝐿𝑜𝑛𝑔−𝑅𝑢𝑛⁡𝑉𝑎𝑟𝑖𝑎𝑛𝑐𝑒=𝜔/(1−(𝛼+𝛽)).
