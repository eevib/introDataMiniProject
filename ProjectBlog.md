# Sentiment analysis on news article comments

31 Oct 2024 - Sami, Eevi, Joonatan

### Understanding online discourse in Finnish

Introduction of comments sections on online news articles has introduced a new platform for discussion of current topics. This new platform is not entirely nice and tidy. Detachedness of online discussion has induced a number of negative phenomenon such as toxicity, hate speech and disinformation.

While platform owners are moderating and discouraging negative behaviour as best they can, novel tools and techiques can help bring further insight into the issue. Application of machine learning tools to estimate comment sentiment should provide new information of online news comments.

How much of online news comments are positive and negative, and how are they interacted with by the readers?

While sentiment analysis tools have existed for other languages for some time, a new Finnish language sentiment analysis model FinnSentiment was developed in 2023. We use this tool to aid us in our analysis of comments in Finnish.


### Our goal

In this project, we aimed to improve understanding and provide valuable insights of comments made on online news articles. We hoped that this would provide additional value to researchers, publishers and the general public interested in the issue.

To provide these insights, we focused on answering questions such as:
- Are the comments as negative as we may think?
- How is interaction distributed among comments?
- What is the sex distribution of the commenters?


### Data gathering

As we intended to process comments in Finnish, we selected *Helsingin Sanomat*, a prominent Finnish language news outlet, as our data source. We found the Politics-section particularly interesting for two reasons. Firstly, we expected articles there to elicit more discussion than in other topics. Secondly, comments there requred users to reveal their real name when posting. This could be used to combine and gather more information.

After gathering sufficient amount of comment data from collecting article identifiers and requesting the comments from an open HS API, we conducted preliminary data analysis.
In total, we collected 211 articles with 7973 comments, meaning around 38 comments per article on average. Our expectation of active political discussion certainly seems to hold. Additionally, it would appear that while many articles have some comments, select few receive many times more, as can be seen from the figure below.

![Distribution of articles and comments](/images/numberOfCommentsPerArticle.png "Distribution of comments per article")

### Preprocessing and analysis

With our data, we moved on to processing the data for further analysis. This had to key steps, namely **anonymisation** and **enrichment**.

We wanted to gather some information on the commenters in aggregate in addition to the comment characteristics. We used rudimentary statistical inference to assess whether a commenter was male or female. After this was done, we removed all real name information from the comments metadata, as we wanted the rest of the process to only handle anonymised data and ensure GDPR compliance.

For our analysis, we used FinnSentiment BERT model to assess sentiment. FinnSentiment was trained with 27 000 Finnish sentences with three human annotators, labeling sentences as positive, negative or neutral with certain confidence. We then used statistical analysis to draw insights from the labeled data.

Following are the core of our results. With these promising initial results, we hope to answer the key question posed and provide valuable insight for researchers, publishers and the general public.


### Results

-	Majority of commenting being labeled with neutral sentiment, significant portion negative and a fraction positive.
-	Majority of comments by male commenters
-	Negative comments have slightly more interaction on average
-	No statistical difference in sentiment distribution between male and female commenters

| ![Distribution of female and male commenters](/images/piechart.png "Distribution of female and male commenters") | ![Distribution of vote in different sentiment categories](/images/boxplot.png "Distribution of vote in different sentiment categories") |
| ------------- | ------------- |
| ![A bar chart on the distribution of sentiments.](/images/sentiment_distribution.png "Distribution on sentiments") | ![Distribution of votes on comments](/images/distributionOfVotesOnComments.png "Distribution of votes on comments") |
| ![Distribution of comment lengths](/images/distributionOfCommentLengths.png "Distribution of comment lengths") | ![Relationship between votes and comment length](/images/votesLength.png "Relationship between votes and comment length")
