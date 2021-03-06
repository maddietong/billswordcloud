## Bill's Word Cloud - Project for Code Louisville Python for Databases Spring 2018 
This simple app allows the user to select any one of William Shakespeare's plays, and then select any one act within that 
play. Once they've made their selections, the code will generate a simple word cloud showing the words most frequently used 
in that play/act combination. The question I'm answering is, simply, "how can we see the variance of frequently used words 
between plays and acts across Shakespeare's oeuvre?" This visualization could serve as a starting point for theories, 
deductions, and perhaps more questions about the way in which Shakespeare crafted his work.

## Overview
I accomplished this word cloud by first finding a dataset of Shakespeare’s complete works. I located the dataset on Kaggle, 
here: https://www.kaggle.com/kingburrito666/shakespeare-plays and also included the data as a CSV file in my repository as: 
Shakespeare_data.csv
I chose to use the plays only from this dataset (though Shakespeare’s complete works contains other pieces), and visualize 
the final product as a wordcloud. Unlike some other projects, I assume, this is an interactive, and so analysis of the data 
is conducted based on user input.

## Get Started
1. I created this project solely in Jupyter Notebook, so you will need Anaconda installed in order to run my project. 

2. You will also need to install the word cloud module. I simply ran `sudo pip install wordcloud` from the command line. 

You can also install by entering: 
`conda install -c https://conda.anaconda.org/conda-forge wordcloud`
in the Anaconda prompt. After this, start python shell, and import the wordcloud module.

You can find further instructions for installing this module here: https://github.com/amueller/word_cloud/commit/34c5828532e9d3d745b2b1b3b92717de6d19dc0f

3. Once you've downloaded the repository files, wordpress module, and Anaconda, open Juypter notebook. 

4. Open import_csv_fix.ipynb. Restart the kernel and run all.

5. Open select_and_double_check.ipynb. Restart the kernel and run all. At this point, the program will prompt you to enter a play and act. Once it's accepted the play and act combination you've chosen, the program will generate a wordcloud--simply scroll down to see. 

## Process and Project Requirement Fulfillment 
I read the Shakespeare_data.csv file into Jupyter Notebook, and created a sqlite database called “shakespeares_works.db”. 
The Python script which sets up the SQLite database is found in import_csv_fix.ipynb. As mentioned previously, I used Python 
in Jupyter notebook to take the data from Shakespeare_data.csv and create a SQLite database called shakespeares_works.db. 
At this time, I also created a new column in the database called “searchname.” This new column was created in order to 
ensure that user input for play titles could be matched precisely to play titles in the database, with no concern for 
capitalization or punctuation.

The second file that I used to create this project includes the user input piece, as well as the data visualization. 
This file is called select_and_double_check.ipynb. This is the script that asks users for input as they choose their 
play and act. 

When a user inputs a play, the database is checked to ensure that the play exists, and if not, prompts them to try again. 
Likewise, when the user inputs an act, the database is checked to ensure that the act they’ve chosen exists in their play 
choice. Once the choices are made and accepted, the script connects to the database, searches for the words contained in 
the play/act combination that’s been provided. 

After removing certain “stop words,” or words that are too common to be considered in a word cloud, the script populates 
a word cloud for the viewer to see. There were existing modern stop words that are imported into the file, and other 
Elizabethan stop words that I added (“thy, thee, etc.“)

Using the wordcloud module, which uses Matplotlib and Python Imaging Library, I was able to generate a word cloud. 
