# NLP&TM Project 16: Climate Change News Analysis

## Setting up the Environment:

To run the script locally, you would need to install Python and the required libraries in a virtual environment.
1. Create a virtual environment: 
   ```commandline
   python -m venv /path/to/new/virtual/environment
   ```
2. Run the virtual environment:
   1. Linux (bash)
   ```commandline
   source /path/to/new/virtual/environment/bin/activate
   ```
   2. Windows
   ```commandline
   .\Scripts\activate.bat
   ```
3. Install the required libraries from the `requirements.txt` file:
   ```commandline
   pip install -r requirements.txt
   ```

## Running the script 
Use the following command to run the `main.py` :
   ```commandline
   python main.py
   ```

## Run the Project Tasks
Each of the implemented project tasks can be run by uncommenting their function calls in the `main.py` file. 
Most of the functions have the following format: 
```
task_function_name(start_index, end_index)
```
**Parameters:**
- `start_index`: indicates the first article document index number to run, along with all their comment documents
- `end_index`: indicates the last article document index number to run, along with all their comment documents


### Task 1: Identify a Climate Change topic
- Identify a topic in climate change which has been extensively commented on in the media, and assign it to the `keyword` variable.
```
keyword = 'carbon emissions'
```

### Task 2: Retrieve 20 search results using the keyword
- Use a News API (The Guardian API) to retrieve 20 search outcomes related to the Climate Change topic specified in Task 1
```
results = retrieve_search_results(keyword, nr_of_outcomes)
```
  - **Parameters**:
    - `keyword`: the topic phrase that will be used in the search query 
    - `nr_of_outcomes`: the maximum number of articles to retrieve (in this case, `nr_of_outcomes = 40`)
      - _**Note**: not all articles found in the **Opinion** section of **The Guardian** have comments, so we retrieve a larger number of results and check if they contain comments before saving them as text documents._

### Task 3: Check the overlapping extent (similarities) between the News Articles and their Comments
#### Task 3.1: Parse the results and save them as News Article & Comment text documents
- Extract the text from the article
- Use the article's _shortUrl_ to retrieve the top comments of the article (about 2-5 comments per article)
```
news_articles_w_comments = parse_news_articles(results)
get_comments_from_articles(news_articles_w_comments)
```
#### Task 3.2: View the Historgram & Jaccard Index of the Most Frequent Words in each document
- Pre-processing: _stopword removal, stemming, lemmatization & tokenization_
- Get the 20 most frequent terms of each document and draw a histogram
- Output the Jaccard Index between the most frequent terms found in the article and each of their comments
```
view_most_frequent_terms(1, 21)
```

### Task 5: View the Sentiment Values for each News Article & their Comments
- Get the positive & negative sentiment vector for each News Article
- Get the positive & negative sentiment vector for each Comment
- Calculate the Pearson correlation of the sentiment vector values between each News Article & their Comments
```
view_sentiments(1, 21)
```

### Task 6: Evaluate the agreement/disagreement extent for each Comment
#### View the Histogram of the negative entities found in each document, and their influence on their sentences
- Get a list of Negative Emotion Wordings from the Empath corpus
- Identify the entities that the Negative Sentiment Words are associated to (if any)
- Generate a histogram of these entities (across all the Comments of a News Article)
```
view_user_disagreement_extent(1, 21)
```
#### View the Histogram of the positive entities found in each document, and their influence on their sentences
- Get a list of Positive Emotion Wordings from the Empath corpus
- Identify the entities that the Positive Sentiment Words are associated to (if any)
- Generate a histogram of these entities (across all the Comments of a News Article)
```
view_user_agreement_extent(1, 21)
```

### Task 7: View the Histogram of the number of Agreement & Disagreement words in each document
- Generate a list of agreement words
- Generate a list of disagreement words
- Count the occurrences of all agreement-related words in all the Comment documents of each News Article
- Count the occurrences of all disagreement-related words in all the Comments documents of each News Article
- Generate a histogram
```
view_commenter_behavior(1, 21)
```