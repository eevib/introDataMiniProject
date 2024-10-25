# Sentiment analysis on news article comments
Introduction to data science miniproject. Team: Eevi Bengs, Joonatan Strang, Sami Pulli

## Blogpost
[Blogpost: Sentiment analysis on news article comments](https://github.com/eevib/introDataMiniProject/blob/main/ProjectBlog.md)

## Technical report
[Technical report](https://github.com/eevib/introDataMiniProject/blob/main/Group%20Assignment%20Technical%20Report.odt)

## Miniproject canvas 
[Miniproject canvas](https://docs.google.com/document/d/1RJKgGe0vVkGnCps-HEY4bKLQI1y0CzpytwS5tpvuaKY/edit#heading=h.pg57voj6n86v)

## Usage instructions
- Start by downloading a WebDriver (here: Chrome, https://googlechromelabs.github.io/chrome-for-testing/#stable) as unzip the downloaded directory
- Make sure that the correct path is set in the code 
- Install necessary dependencies (BeautifulSoup, selenium, pandas, numpy, matplotlib, transformers*, scipy)
- Now fetch_articles.ipynb can be run
- Another section of HS can also be used (e.g, culture, economy etc.). The default is politics
- In data_analysis.ipynb, make sure that paths to JSON file(s) is/are correct. If only one file is used, modify code
- Download list on Finnish first names from the internet. This list can be found on avoindata.fi. Current link is https://www.avoindata.fi/data/fi/dataset/none/resource/08c89936-a230-42e9-a9fc-288632e234f5 (checked on 24.10.2024)
- Make sure that the path to this Excel-sheet is correct in the code
- OPTIONAL: if comments are processed (default: no processing), load stopwords from https://github.com/stopwords-iso/stopwords-fi. Make sure that the path is correct in the code
- OPTIONAL: additionally install nltk for processing

*Transformers might require other dependencies 

