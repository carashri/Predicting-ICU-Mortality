### Predicting ICU Mortality Using Natural Language Processing

#### Goal
Using the MIMIC-III database, based on caregiver notes identify ICU patients who are at high risk of mortality within 24 hours of admission.

#### Methods Used
*Natural Language Processing
<br>
*Bag-of-Words Approach
<br>
*Data Visualization
<br>
*Machine Learning
<br>
*Predictive Modeling

#### Technologies
*Python
<br>
*Pandas
<br>
*Scikit-learn
<br>
*Matplotlib
<br>
*NLTK
<br>
*Numpy
<br>
*Jupyter Notebook
<br>
*Anaconda

#### Code
Data preparation and processing steps can be found in [Data Collection and Preparation](https://github.com/carashri/Predicting-ICU-Mortality/blob/main/Code/Data_Collection_and_Preparation-GH.ipynb).
<br>
Text pre-processing and machine learning steps can be found in [Text Pre-processing (Bag of Words) and Machine Learning](https://github.com/carashri/Predicting-ICU-Mortality/blob/main/Code/Text_Pre-processing_(Bag_of_Words)%20and%20Machine%20Learning-GH.ipynb).

#### Background
The intensive care unit (ICU) has the highest mortality rate of all the units in a hospital.  Of the approximately 4 million ICU admissions per year in the United States, the average mortality rate ranges from 8-19%, or about 500,000 deaths annually.1 ICU bed space is becoming increasingly relevant in the time of Covid-19. The ICU mortality rate of Covid-19 patients as of July 2020 was 41.6% across international studies.2 Although the mortality rate of Covid-19 appears to trending downward in the last few months11, as the pandemic begins its predicted resurgence this fall and winter, decisions regarding the proper rationing of beds and mechanical vents will become issues that many ICUs throughout the US will, more likely than not, be dealing with again as they did early in the pandemic.

<br>High in-hospital death rates lead to unnecessarily high financial costs and poor patient experiences at the end of life. The average cost of an end-of-life ICU stay is $39,3003. This costs the US $19.65 Billion per year.

#### Approach

Using the Bag-of-Words approach on caregiver notes created in the first 24 hours of admission, create a better-than-random model to predict patients at high risk of mortality.

#### The Data
This project was completed using the MIMIC-III database from MIT. MIMIC-III is a large database containing de-identified data associated with over 50,000 patients who stayed in ICUs of the Beth Israel Deaconess Medical Center between 2001 and 2012. After completing an online credentialing process, the database is accessible via: https://mimic.physionet.org/. For this reason, raw or processed datasets are not available in this repository.
Data was obtained from three datasets in MIMIC-III: ADMISSIONS, NOTEEVENTS, and ICUSTAYS.

#### Challenges
*Imbalanced dataset (positive class ~8%)
<br>
*Many steps for processing

#### Features selected
Mortality information, caregiver note text, admission date and time, time of death, number of stays in the ICU and length of stay(s) in the ICU.

#### Handling of imbalanced data
Training data samples with negative mortality (i.e., survivors) were subsampled, so that the final training dataset would be equally balanced.

![1](https://github.com/carashri/Predicting-ICU-Mortality/blob/main/Images/1%20-%20subsample%20negatives.png)

#### Text Preprocessing

Bag of Words - Steps
<br>
1. Numbers, punctuation, and irrelevant characters were removed from text.
2. A pre-made list of stop words was used to remove irrelevant words (such as “a”, “the” “and”). 
3. Most frequent words were noted. Additional stop words were added to the list (see next 2 figures).
4. A vocabulary of ‘tokens’ was built from unique words left in the caregiver notes. 
5. Each of the tokens was fed into a vectorizer, where it was converted into a feature (variable) that represented the different columns of the dataset. 

![2](https://github.com/carashri/Predicting-ICU-Mortality/blob/main/Images/2-word%20frequency.png)

#### Machine Learning

*Model Selection*
This is a classification problem, since the target variable, mortality, is categorical and binary.The ideal model would be a supervised learning model that works well with a large, sparse matrix dataset. The data was fed into four different models: logistic regression, Naive Bayes, random forest and SVM. 

![3](https://github.com/carashri/Predicting-ICU-Mortality/blob/main/Images/3-model%20comparison.png)

Logistic Regression was chosen as best performing, with AUC-ROC of 0.982 (training) and 0.787 (validation), and less overfitting compared with Random Forest.

In order to better assess the performance of the linear regression model and to optimize its parameters, some parameters were visualized:
<br>
*Sample Size*
![4](https://github.com/carashri/Predicting-ICU-Mortality/blob/main/Images/4-sample%20size.png)
<br>
*Number of Features*
![5](https://github.com/carashri/Predicting-ICU-Mortality/blob/main/Images/5-number%20of%20features.png)

<br><br>*Regularization Strength*
![6](https://github.com/carashri/Predicting-ICU-Mortality/blob/main/Images/6-regularization%20strength.png)

<br><br>*Gridsearch Cross-Validation*
Finally, GridSearch Cross-Validation was performed to help determine best parameters. GridSearchCV determined the best performance parameters to be: 'C': 0.0001, 'max_iter': 100, 'penalty': 'l2', 'solver': 'sag'.

![7](https://github.com/carashri/Predicting-ICU-Mortality/blob/main/Images/7-gridsearch.png)

##### The optimized model was used on the test data with following results:

<br><br>*Best Model - AUC/ROC (with test data)*
![7.5](https://github.com/carashri/Predicting-ICU-Mortality/blob/main/Images/7.5%20Best%20model%20AUC-ROC.png)

<br><br>*Confusion Matrix*
![8](https://github.com/carashri/Predicting-ICU-Mortality/blob/main/Images/8-confusion%20matrix.png)

<br><br>*Performance Metrics*
![9](https://github.com/carashri/Predicting-ICU-Mortality/blob/main/Images/9-performance%20metrics.png)

#### Interpretation of Results: Hospital Cost Savings

![10](https://github.com/carashri/Predicting-ICU-Mortality/blob/main/Images/10-hospital%20savings.png)

If  the machine learning model were used, an average savings of 22.5% (approximately $1.19 million) could be achieved. Additionally, 80% of the patients who are at the end of life would be flagged after 24 hours of hospital admission. If this model was applied to all community hospitals within the US, a savings of nearly $6.2 billion per year could be achieved.

#### Next steps
A reasonable next step would be to create a stacked ensemble model, which would allow for a stronger algorithm to predict mortality in ICU patients.

#### About
This project was completed in November 2020 as my second capstone for Springboard Data Science Bootcamp. My other projects can be found at https://github.com/carashri.


