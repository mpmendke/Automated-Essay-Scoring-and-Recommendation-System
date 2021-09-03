#########################
Code Running Instructions
#########################

The code files uploaded on moodle and github (https://github.com/mpmendke/Automated-Essay-Scoring-and-Recommendation-System) includes the following:
•	Formatting of CLC-FCE dataset, based on work done by Gwenaelle Cunha Sergio (2019).
•	Formatting of text scripts for discourse cohesion features, based on work done by Emily Pitler and Ani Nenkova (2009).
•	86 distinct Feature Extraction for training and test data, based on work done by Sowmya Vajjala (2016) and additional readability features.
•	Implementation of eight ML regression models for AES systems.
•	Identifying top 10 best feature predictors.
•	Performance of Ridge regression model for each feature group.
•	Implementation of six Clustering algorithms for Recommendation systems.

#########################
Data formatting
#########################

The CLC-FCE dataset is available in XML format which needs to be formatted to CSV. Run the below steps to format the dataset:
•	Unzip ‘FCECorpusXML-master.zip’
•	‘FCECorpusHandler.py’ is the main python code that contains methods to download the dataset and converts them from xml to txt.
•	Run ‘main_xml_to_txt.py’ which will generate the ‘data’ folder with the original CLC-FCE dataset and its converted txt format.
•	Next Run the ‘txt_to_csv.py’ file which will generate two csvs: ‘training_data.csv’ and ‘test_data.csv’ with 1141 records and 97 records respectively.

#########################
Feature Extraction
#########################

Once the essays are extracted in csv format and separated in training and test dataset, run the ‘Feature_Extraction_For_Trainingdata.ipynb’ and ‘Feature_Extraction_For_Testdata.ipynb’ to extract 86 linguistic features using feature engineering. To extract discourse cohesion features, follow the below steps:
•	Unzip ‘addDiscourse.tar.gz’ which contains the implementation of identifying explicit discourse connectives by Emily Pitler and Ani Nenkova (2009).
•	For code to work we would need syntactic parse trees as input.
•	Unzip ‘DiscourseFeaturesData.zip’.
•	Then run ‘Discourse_Cohesion_feature_preprocessing.ipynb’ to generate parsed trees. (P.S. ‘DiscourseFeaturesData.zip’ folder already contains input txt files with parsed syntactic trees).
•	Now run addDiscourse.pl (Perl) file specifying the input and output locations. (Please follow Readme.txt of the ‘addDiscourse.tar.gz’ zip folder).
•	Once the txt files are tagged (P.S. ‘DiscourseFeaturesData.zip’ folder already contains output txt files with tagged cohesion features.) you can run the last code block of ‘Feature_Extraction_For_Trainingdata.ipynb’ and ‘Feature_Extraction_For_Testdata.ipynb’ to extract these discourse cohesion features by specifying the directory location to ‘path’ variable.
The final data files will look like ‘training_features - Copy.csv’ and ‘test_features - Copy.csv’ with 86 extracted features mapped to corresponding docIds.

####################################### 
Automated Essay Scoring (AES) system
#######################################

Once the datasets are formatted and processed, we can now start the training of our ML regression models to develop AES systems.
•	Run the ‘ML_Models_Overall_Performance.ipynb’ file to compare eight ML regression models used in this project.
•	Run the ‘ML_Models_Top10_features.ipynb’ file to observe the best 10 predictors out of 86 features using the Mutual Information Feature Selection method and the performance of the Ridge Regression model when trained on these features.
•	Run the‘ Ridge_Regression_Feature_Group.ipynb’ file to observe the best predictor feature group by comparing the performance of the Ridge regression model trained on each feature group individually.

#########################
Recommendation system
#########################

As providing feedback is an important aspect of the AES system, we have developed a recommendation system using a clustering algorithm.
•	Run the ‘Essay_Clustering_And_Recommendation.ipynb’ file to compare the performance of six different clustering algorithms.
•	Then a memory-based collaborative filtering recommendation approach is developed using the K-Means clustering algorithm to make five recommendations based on which cluster does the essay falls into.
