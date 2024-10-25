# Mini-project Technical Report
Introduction to Data Science  
Bengs, Pulli, Strang  
28.10.2024  

### Online deliverables available at:
[Github page](https://github.com/eevib/introDataMiniProject)

[Blogpost: Sentiment analysis on news article comments](https://github.com/eevib/introDataMiniProject/blob/main/ProjectBlog.md) 

In this mini-project our group produced a pipeline to analyze user comment sentiment on Helsingin Sanomat (https://hs.fi/) news articles. Our goal was to improve understanding of commentary on online articles on a major news outlet for researchers, publishers and the general public. Mini-project material and canvas can be found on the deliverables Github-page (link above).

The pipeline collects article identifiers, fetches the articles’ comments from an open HS.fi API, preprocesses and analyzes the data. Key step in preprocessing is to anonymize the collected data to ensure GPRD compliance. The data analysis utilizes FinnSentiment -model [FinnSentiment] to assess user comment sentiment. Additionally, we analyzed distribution of user gender among the commenters.


### Data collection
HS.fi doesn’t allow scraping their website without permission. Right at the start of this project, when we had come up with our topic, we sent an email to HS.fi customer service and explained our topic and asked for permission for a small data gathering. Unfortunately to this day, we haven’t got any answer from them. We still decided to continue and kept our data gathering as small as possible as not to stress the servers or cause any other inconvenience to the newspaper.
HS.fi comment section requires users to use their real name to be allowed to comment articles from certain topics. We decided to use comments from the politics section (https://www.hs.fi/politiikka/) since this is one of the sections with only real names.
In order to collect comments from the API, we needed an adequate number of article Ids. In order to (semi-)automatically collect a large number of IDs, we used Selenium with a Chrome WebDriver to load the website. This was required as the page loads dynamically and not all IDs are visible initially. Minor amount of manual labour was used as we needed to scroll to the bottom of the page to activate loading of the entire page. This part could be easily automatized if more articles was needed but we decided against it since we only collected IDs in two batches. When the entire page was loaded, BeatifulSoup was used to scrape the site for IDs. With the acquired IDs we called the API and received comments and related metadata such as names, number of votes and time of commenting. This data was saved in JSON format for processing.

After gathering the comments, we started by removing the last names of the commenters to avoid saving personal data. We created two Pandas DataFrames from the JSON; one that contained article titles, their IDs, tags and total number of comments. The other DataFrame contained article IDs, comments, votes on the comments, creating time and first names.

### Data preprocessing
To be able to divide the commenters by sex we used the Digital and population data service agency Finnish name statistics. We combined the lists of female and male names into one list and labelled the commenters as female or male depending on which sex had more persons with that first name. The few names with a 50-50 distribution of name holders were just labelled as NaNs.

We had around 400 comments where sex couldn’t be specified, the most common reason was that the commenters had mixed up the first name and last name fields, another reason was that the name was so rare that it wasn’t included in the name list (under 5 with that name in Finland).

Overall we gathered 211 articles, where 205 had some comments. The total number of comments were 7973 and we used 7575 in our analysis. The difference is due to comments, where we didn’t manage to label the sex of the commenter. 

To start the analyse of the comments, we did some preprocessing for them. First we made all words lower case and removed stop words. Quite many comments had line break tags <br> or <br/> which we removed. We also tried to use Snowballstemmer for Finnish to stem the words in the comments.
 
### Visualisation
We did a number of plots and graphs to visalize our data. The main idea was to get an overview of the data we had. We wanted to know if we can find any patterns in the comments. We did very basic histograms on the distribution of comments per article, distribution of votes on comments and distribution of comment lengths (in characters). The distribution of votes per comment revealled that most of the comments have only a few votes, however there are some comments with a huge number of votes.  

We made a pie chart of the gender distribution of comments. We were surprised to find out that 77.69 % of the commenters were male and only 22.31 % were female. It would be very interesting to get some data on the sex of the readers. 

After we had done the sentiment analysis on the comments we made a histogram on the distribution of comment sentiments and a boxplot on distribution of votes in different sentiments. It showed that most of the comments are neutral (70 %), some are negative (25 %) and only a small fragement are positie (5 %).

We wanted to keep the visualization simple and clear. Therefore we used only basic histograms, pie chart and a boxplot. We focused on labeling the data and making the graphs as clear and informative as possible.

### Machine learning
We used FinBERT FinnSentiment model for classification of the comments into neutral, positive and negative ones. 
We tested the Finnbert Finnsentiment model and realized it worked better on less pre-processed comments, so in the end we only removed the <br> tags from our comments, before giving the comments to the model to be analyzed. For example a use of many exclamation marks (!) made the feeling stronger and the points for classification bigger. 

### Communication of the results
A blog post seemed as the most suitable forum to communicate our results for our targer group (media houses, researchers and the general public). We added the most important graphs and results to the blog post without going into too much technical details.  
Thoughts on the process, what worked and what didn’t?
To decide the topic was not that easy. We had a lot of different ideas from a very wide area of topcs. After thinking back and forth about different topics we were all happy with what we chose. Analyzing news article comments were something new that no one of us had done and we were quite sure we will learn something new. After maybe a bit slow start we got everything rolling and the project went very well. We valued face to face meetings and had one to two meetings every week throughout the course 
One challenge was working with Finnish text. There are not that many tools available and it required quite a lot of googling to find suitable tools for Finnish. 
We should have made our topic more clear from the start and we could have planned the work a bit better at the start. One reason we didn’t do this was we didn’t really know how to do the things we had planned to do and therefore the scope changed a bit during the project. 
The group work worked very well. We found it easy to work together and could utilise each others strengths. 

### Learning outcomes
No one of us had experience with string processing or working with texts, except for the weekly assignments in this course, so we learned a lot about that. We found it a good task to plan and execute a small scale data science project. Since the project scope was very wide and we could basically do anything it was a good opportunity to learn about decision making. 
It was fun and rewarding to see that the sentiment analyser worked surprisingly well. 

### Future steps
It would be very interesting to compare our results with the reader statistics of hs.fi. Do more males read hs.fi in general or the politics section or are they only more active on commenting on the articles?
It would be nice to do a website that would show recent statistics of the comments, however this would need permission from Helsingin Sanomat.



[FinnSentiment]: https://arxiv.org/pdf/2012.02613
