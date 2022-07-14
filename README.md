# SocialVolume

The goal of CryptoVolume is to effectively predict the pricing of cryptocurrencies using a machine learning model. Sentiment analysis has existed for years in the form of [market sentiment](https://en.wikipedia.org/wiki/Market_sentiment#Theory_of_investor_attention), where traders' perception of the market & individual stocks is measured in terms of bullish or bearish, indicating if the market is moving upwards or downwards, respectively. Recently, many researchers have analyzed the impact of social media sentiment on the market.  While market sentiment measures traders' perspective of the market,  social media sentiment statistically measures the sentiment of users on Twitter, (and/or other sites such as Facebook, Instagram, Reddit, etc.) many of which may not even be trading in the actual market. Ideally, social media sentiment abstracts out generic news and captures the general public's view on a specific company or stock. Some examples of incidents that would lead to a strong social media sentiment would be the [United Airlines incident (2017)](https://en.wikipedia.org/wiki/United_Express_Flight_3411_incident#Cultural_impact) or [Blizzard's Hong Kong player (2019)](https://www.cbsnews.com/news/blizzard-china-statement-blizzard-president-apologizes-for-hong-kong-player-ban-we-moved-too-quickly/), where both situations were EXTREMELY controversial.

Since cryptocurrencies are a newer part of the market, many uncertainties still exist. The price trends do not seem to have a strong basis and the idea of cryptocurrencies are very controversial as well, making social media sentiment analysis an obvious choice to predict the behavior of cryptocurrencies.

## Objective
So now that we know all of these forms of sentiment-related predictions exist, what will CryptoVolume do differently? The impact of social media sentiment has been analyzed **too** frequently. While it is clearly a powerful tool, I wanted to use a lesser known metric. Instead of analyzing the social media sentiment, CryptoVolume scrapes the volume of tweets per day mentioning a specific cryptocurrency. The assumption is that a stronger volume of tweets will correspond to a greater volume in which the stock is being traded, whether it is being bought or sold. In the proof of concept, I chose to scrape and analyze Bitcoin, the most widely known cryptocurrency. After obtaining this data, the goal is to combine it with pricing factors of the respective cryptocurrency and create predictions of the price, given this data with a nueral network.

While asset-backed stocks are easier to predict given market data, these predictions cannot be made with machine learning due to a key reason. These stocks are extremely volatile towards reports and news that depend on the companies performance, which generally cannot be predicted by past data. As a result, most machine learning models will choose the previous day's pricing as the most likely value. However, cryptocurrencies differ in that they are NOT asset-backed. There is no performance reports and news is generally far more infrequent, but also potentially more severe. As a result, these predictions will be limited to short term, but also have the potential to be more accurately predicted given past data.

## Disclaimer
There are risks associated with trading, especially in the volatile crypto market. I do not recommend that any cryptocurrency should be bought, sold, or held by you. Do conduct your own due diligence and risk what you can afford to lose. All contents in this repository and beyond are solely for educational purposes.

## Scraping & Data
The greatest limitation in this project is access to the data. Twitter does not provide an exhaustive search feature or counts endpoint in their non-enterprise API. As a result, I chose to use Twint which acts as a bot, retrieving data from each webpage. The script that was created ran on AWS using cron job's task management to schedule and kill the script by the hour, preventing parallelization which would kill the instance. After roughly 140 hours, the data was scraped for the first 306 days of 2019 and recorded into a text file. The scraped data is depicted below.

<p align="center">
 <sup>Close Price vs. Tweet Count</sup>
 </p>

![Close Price vs. Tweet Count](https://i.imgur.com/O0AxsHe.png)
