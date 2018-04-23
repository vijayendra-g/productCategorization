# Product Categorization

### Task

Build a model to classify the products into any one of the buckets  (i) Books (ii)  Music (iii) Videos (iv)  Rest -  A default class for products which doesn’t belong to (i),(ii) or (iii)  category. The output could be a CSV file entitled submission.csv where each row has the following format: <Id, additionalAttributes, label>

# Data Description

Given the CSV (train and test) data files:

### Id
    unique id for the record

### additionalAttributes
Product attribute related to a particular product. These are key, value pairs that can be found in tabular format as product information for most products in e-commerce websites.

    An example of additionalAttributes 

    {"ASIN": " B000JJRY9M",    "Amazon Bestsellers Rank": "  in DVD & Blu-ray (See Top 100 in DVD & Blu-ray)", 
     "Average Customer Review": " Be the first to review this item",    "Classification": "  Exempt",   
     "DVD Release Date": " 26 Feb. 2007", "Format": " AC-3, Colour, Dolby, DVD-Video, PAL",   "Language": " English",   "Number of discs": " 1",    
     "Region": " Region 2 (This DVD may not be viewable outside Europe. Read more about DVD formats.)",   
     "Run Time": " 287 minutes",   "Studio": " Hip-O Records"}
   
### label
    The class to which a product belongs. Values belong to the finite set (‘books’,’music’, ‘videos’,’rest’)


# Methods

The Jupyter Notebook productCategorization.ipynb can be used for experimentation. 

1. As a first step, the label distribution from the training samples are analysed. The training data has ~75% of products under "rest" categories and the remaining are "music", "books" and "videos".
2. In the preprocessing step, the raw product description text are run through,
                a) Lowercasing all the letters
                b) remove punctuations, special characters, stopwords
                c) remove all numerical texts
3. All the training samples are converted into TF-IDF vectors using inbuilt scikit text processing tools.
4. During training two models were experimented

                a) Using a two layer logistic regression model
                        -> Level1 -> classifier built to predict if a product belongs to either "rest" or "music, books, videos"
                        -> Level2 -> classifier built to predict if a product belongs to either "music", or "books", or "videos"
                b) Using a decision Tree regression model
5. Testing samples are converted to TF-IDF vectors based on the vocabulary built on top of training samples.
6. Both the methods are evaluated on the test data set and the results on the stored on the "submission.csv" file. The output CSV file has two new columns appended to the test data i.e, label_logReg and label_decTree as the predictions from the model a and model b, respectively.
