     # Stackbot-DS3
     The main functionality of this project is in chatbot.ipynb. There are three fucntions in this file, all of which center around taking in a user-generated python question, and returning one or more answers. More information is present in the notebook to explain the specifics of each function. The other files mainly serve to create the necessary information for the chatbot functions.
     # Local Setup
     1. Download the dataset from https://www.kaggle.com/datasets/stackoverflow/pythonquestions?resource=download
     2. Create a conda environment using stackbotenv.yml (follow [here](https://www.loom.com/share/0ea254b85b2745e59322b5e5a8692e91) if you haven't used conda)
     3. Load in data
          1. Run all cells in data_exploration.ipynb
          2. Alternatively, download the file at https://drive.google.com/drive/u/3/folders/1_JEK_GU4MpafPtzUHgvVThDi9ivsm4kS, to skip running data_exploration.ipynb, which takes around 20-30 minutes
     4. Run all cells in tf-idf.ipynb
     5. Using chatbot.ipynb you can call the chatbot_reply() function with your question

     # Webpage Setup



