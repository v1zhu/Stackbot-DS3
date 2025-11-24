# Stackbot-DS3
The main functionality of this project is in chatbot.ipynb. There are three fucntions in this file,  
all of which center around taking in a user-generated python question, and returning one or more  
answers. More information is present in the notebook to explain the specifics of each function.  
The other files mainly serve to create the necessary information for the chatbot functions.
# Local Setup
1. Download the dataset from https://www.kaggle.com/datasets/stackoverflow/pythonquestions?resource=download
2. Create a conda environment using stackbotenv.yml (follow [here](https://www.loom.com/share/0ea254b85b2745e59322b5e5a8692e91) if you haven't used conda)
3. Load in data
     1. Run all cells in data_exploration.ipynb
     2. Alternatively, download the file at https://drive.google.com/drive/u/3/folders/1_JEK_GU4MpafPtzUHgvVThDi9ivsm4kS, to skip running data_exploration.ipynb, which takes around 20-30 minutes
4. Run all cells in tf-idf.ipynb
5. Using chatbot.ipynb you can call the chatbot_reply() or other 2 functions with your question
# Methods Used  
In data_exploration.ipynb, we cleaned the data and prepared it for vectorization. First, we merged the downloaded csv files
to create question and answer pairs. For the answer column, we cleaned HTML tags to make it more readable. For the question
column, we did additional cleaning, removing newlines, multiple spaces, normalizing punctuation, and lower casing 
everything. For the title column, we did the same steps, but did not have to clean HTML tags. Then, for the title and 
question columns, we kept only alphabetic words, removed stopwords except for negations, and lemmatized all words. 
Finally, we combined the title and question columns and saved the dataframe.

In tf-idf-matrix.ipynb, we created and saved both the idf dictionary and tf-idf matrix. First, we read in the saved 
dataframe, which had some null values in the question column. These seemed to be caused by saving to a CSV. We decided just
to drop these because it was a relatively small number of columns (around 600 out of a million). Next, we created the idf 
dictionary by looping through every question, counting the number of documents every word appeared in. Then, we created a 
dictionary for every question, containing the tf_idf score for every word in the question. We then converted this to a 
SKlearn sparse matrix. Finally, we saved the sparse matrix and idf dictionary. In addition to this, we saved a dictionary
which contained every unique word and a corresponding column value for the tf-idf matrix. We did this because we 
encountered issues when loading the data back into chatbot.ipynb because dictionaries would not always maintain the same
order. However, this is probably avoidable by using another data structure.

In chatbot.ipynb we created three functions to query the dataframe based on a user input. They all work very similarly, as
each function only adds additional filter options. As such, I will only discuss the function chatbot_reply here. In this 
function, we first compute the tf-idf values for the user query, and convert it to a SKlearn sparse matrix. We then 
compute the cosine similarity between the input and every vectorized question in the dataframe. We take the max value and
return the highest rated corresponding answer, along with the similarity score and question.
# Webpage Setup



