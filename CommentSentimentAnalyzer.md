# Sentiment analyzer on news articles comments
# Sentiment analysis pipeline

Sami, Eevi, Joonatan

### What we wanted
- Improve understanding and provide valuable insights of comments made on online news articles
- researchers, publishers and the general public.

Answering questions such as:
- Are the comments as negative as we may think?
- How is interaction distributed among comments?
- What is the sex distribution of the commenters?

### Pipeline to analyze user comment sentiment

Article identifiers from scraping HS politics section -> Comments from open HS API -> EDA -> Preprocessing and enrichment -> Analysis

### Data analysis

Exploratory data analysis:
- 205 articles, 7575 comments, Hs.fi/Politics
- Small fragment of content receives majority of interaction

Preprocessing
- Anonymization
- Statistical sex inference

Analysis
- FinnSentiment BERT model to assess sentiment (trained with 27 000 Finnish sentences)
- Statistical analysis from labeled data

### Results

-	Majority of commenting being labeled with neutral sentiment, significant portion negative and a fraction positive.
-	Majority of comments by male commenters
-	Negative comments have slightly more interaction on average
-	No statistical difference in sentiment distribution between male and female commenters

![Distribution of female and male commenters](/images/piechart.png "Distribution of female and male commenters") ![Distribution of vote in different sentiment categories](/images/boxplot.png "Distribution of vote in different sentiment categories")
![A pie chart on the distribution on female and male commenters](/images/piechart.png "Distribution on female and male commenters")
![A bar chart on the distribution of sentiments.](/images/sentiment_distribution.png "Distribution on sentiments")
![Distribution of votes on comments](/images/distributionOfVotesOnComments.png "Distribution of votes on comments")
![Distribution of comment lengths](/images/distributionOfCommentLengths.png "Distribution of comment lengths")
