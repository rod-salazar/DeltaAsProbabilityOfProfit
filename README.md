# DeltaAsProbabilityOfProfit

Backup from my Medium.com.

I've been playing around with options for the last few months and recently I purchased my first batch of historical CBOE options data. This is my first piece of research with the data-set.

Delta is frequently used as an approximation for the probability of an option expiring in the money (This is different from probability of profit where the underlying has to pass the strike price by the cost of the option at least). Most people understand that Delta is just an approximation for this, and there are better ways to approximate Prob-ITM but since Delta is the most frequently used it’s a good question to ask just how accurate it really is.

I wanted to see in practice how closely Delta actually tracked the true probability in the last year, specifically on the SPY.

Each trial of this experiment goes like this:

Choose a random instance in time in the last year (08/03/2015–07/29/2016).
Choose any available SPY option with 45 days of expiration or less and record it’s delta.
Look ahead to the future data and record whether this option expires in the money.
I repeat this trial 1 million times for call options and again 1 million times for put options.

Using deltas between 0 and 100, I bucketed the trials into aggregate buckets by placing deltas [0.5, 1.5) into bucket 1, [1.5, 2.5) into bucket 2, and so on. Then I proceeded to plot the average delta of each bucket against the observed probability of expiring in the money within my data-set’s time range.

Here is a plot for calls (the observation is that delta lower than it should be?):

![1_17uEXbFzCEI7bmPKmaINMw](https://user-images.githubusercontent.com/51817379/195453419-048c6029-7aed-46bb-a267-b836c36d40b4.png)


Call delta on the x-axis and actual observed probability of ITM on the Y-axis
Puts (the observation is that delta is higher than it should be?):

![1_xGiMpuizQ2P85M7cR0c4Ng](https://user-images.githubusercontent.com/51817379/195453435-0b5068a1-7e8e-42fb-aaf4-0c625db80090.png)


Put delta on the x-axis and actual observed probability of ITM on the Y-axis
Once again, this is only for options in the last year on the SPY which are within 45 days of expiration. I’m not making any conclusions on this data, except that it’s not what I expected. With any piece of code written there’s always the possibility that it’s not correct or there’s a bias in some way, so take everything with a grain of salt.

Soon, I will work on plotting out probability of profit (taking into account the option price) when holding to expiration.

Feel free to comment if you have suggestions on how to improve my experiment or have any feedback.

Raw data https://docs.google.com/spreadsheets/d/1lhEcPV11X1AMhTbXQNexxP7YHklSLZim24WJhhpADdA/edit#gid=9832090

