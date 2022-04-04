# Disney_Stock_VS_Reddit_Sentiment
A data anaylsis and visualization project of comparing Disney's stock prices to sentiment of online posts and comments from Reddit. 
This project was completed for ICS 484 (data visualization) with [Clark Whitehead](https://github.com/Clark-Whitehead).


This source code provides a detailed pipeline of gathering data from Reddit and the stock market, cleaning it, performing sentiment analysis, and graphing the 
results. The 6 major steps of this process are outlined below:

### 1. Data Gathering
This is where the data is gathered, through the help of two different APIs. The PMAW API is used to gather data from Reddit, allowing the user to either pull from a 
subreddit’s collection of posts, or comments on the posts. Yahoo’s YFinance API allows us to get stock price data for any given stock.

### 2. Data Cleaning
Once the Reddit data is pulled from the internet, it needs to be cleaned. There are a lot of posts/comments that have been deleted or removed since originally 
being posted, and some that don’t have any content. Afte these are removed, the creation date is reformatted into a YYYY-MM-DD string format.

### 3. Sentiment Analysis
After the Reddit data is cleaned, we can perform sentiment analysis on it. Google’s BERT sentiment analysis model can be downloaded and used for this step.

### 4. Data Selection for Graphing
Once the Reddit data is cleaned and passed through the sentiment analysis, we need to compare it to the stock market data. There are holes in the Reddit data 
since many posts/comments have been deleted or removed since their original upload, and there is no stock market data from weekends or holidays. Thus, we need to 
find a set of usable dates that both datasets have entries for. This step also removes all unnecessary field from the data to prepare it for graphing.

### 5. ASAP Open Source Data Smoothing
The sentiment data alone is incredibly volatile and messy, so data smoothing is needed. The 
[ASAP model](https://dawn.cs.stanford.edu/2017/08/07/asap/#:~:text=ASAP%20is%20a%20technique%20for,the%20plot%20by%20preserving%20kurtosis.) for smoothing data 
works great, and is applied to the Reddit sentiment data. The source code from this step is the entirety of the open source code fro the ASAP model.

### 6. Final Graphing
This step takes in the data from step 4 and feeds it into step 5, producing a dataset that is ready to be plotted. It returns a dataframe containing the smoothed out 
data, so it can be exported and plotted in something like Plot.Ly.

# Resulting Graphs
The process outlined above was used on both posts and comments from Reddit's [r/Disney subreddit](https://www.reddit.com/r/disney). The sentiment from these two 
datasets are graphed against Disney's stock prices, as seen below.

### Reddit Posts
<img class="ui image" src="https://robert-lemon-uhm.github.io/images/Reddit_Post_Sentiment.png">

### Reddit Comments
<img class="ui image" src="https://robert-lemon-uhm.github.io/images/Reddit_Comment_Sentiment.png">

