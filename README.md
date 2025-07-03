# Option-Probability-Density-Heatmap

In this post I wanted to share the code of one of my first quantitative finance projects, where I used option market data from Yahoo Finance and the Black-Scholes model to generate an option probability density heatmap.

The script begins by retrieving all available expiration dates for the selected option ticker. These expiration dates are then used in a loop to download the full option chain for each date. The resulting data is separated into two sets: one for call options and one for put options.

After the data is collected, it is being prepared by selecting relevant columns such as strike price, implied volatility and expiration date. For each option, the time to expiration (in years) is calculated and constant values are added (the current stock price and the risk-free rate).

The core of the project involves calculating the d2 term from the Black-Scholes model for each option, and then applying the probability density function (PDF) to d2 (for calls) and -d2 (for puts). This doesn’t give exact probabilities but gives a relative sense of how much probability mass is assigned to the strike price.

These values are then structured into a heatmap table, with strike prices on the y-axis and expiration dates on the x-axis. The call and put data are averaged and smoothed to handle the missing values. Finally, the combined heatmap is plotted using Seaborn, where green areas indicate higher probability mass and red areas indicate lower probability mass.
