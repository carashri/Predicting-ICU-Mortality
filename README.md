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

####Background
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
