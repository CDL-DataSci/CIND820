# CIND820 - Big Data Analytics Project
TMU CIND820 Capstone Project - Parliament of Canada Hansard Debate Records (2006 - 2023)

This project is aims to explore what information can be gained through applying text mining and topic modeling approaches to the historical Hansard debate records from the Parliament of Canada. The identified dataset covers from 2006 to 2023 (39-1 Parliment to part of 44-1). The data set includes 1972 pdf files in total and collectively represent 155,385 pages.

## Step 1: Literature Review
The literature review of past research has highlighted the importance of a using a systematic approach to text mining techniques, the benefits of leveraging a combined topic model from LDA and TF-IDF, as well as considerations for evaluation of topic models and the validation of the labels for the extract topic. The literature review also helped to identify comparable alternatives to LDA that include HDP and the more recent BERTopic. While the literature review has identified possible advantages for these alternative topic models, there is a potential for these alternatives to be more computationally intensive and the performance of these different modeal will be explored in the final report. 

Original Data Source: https://www.ourcommons.ca/documentviewer/en/37-1/house/hansard-index

## Step 2: Initial Results
The initial results expored the LDA, HDP and BERTopic Models on a sample of the full dataset. The initial results are divided between the following jupyter notebook files:
* <u>Initial_Results_CreateSample</u>: documenting how two sample sizes were identified that randomly selected files from the full dataset
* Initial_Results_HDP_LDA_Models: Inital exploration of the algothrims for LDA and HDP topic models using a sample size of 25 files. The objectives were to test the general performance of the models in a time efficent manner.
* Initial_Results_HDP_LDA_Models_Sample385: The same code was run a statistically significant sameple size of 385 files out of the full 1972 pdfs from the dataset.
* Initial_Results_BERTopic: Initial assessment of the BERTopic model was limited due to the processing capacity and potential combatability conflicts with running the BERTopic on an Apple M1 processor.

Additionally, the source data for initial results can be found in the following folders:
* Dataset_Sample: 25 file sample that was leveraged by the LDA and HDP models
* Dataset_Sample_385: the larger sample of files that was leveraged by the LDA and HDp models
* Dataset_BERTopic: the limited dataset used to run the BERTopic model

### Summary of Findings in Initial Results:
Leverating the outcomes from the Literature Reivew and exploratory analysis of the dataset, it was determined that the ideal number of topics for the LDA model was 7. This value will be carried forward into the analysis of the sample size of 25 and 385 files in order to compare the LDA and HDP models. Contrasting with the HDP model, when training this algorithm on the dataset (sample 25), a total of 18 topics were identified.

Also improving on the literature review was updating the processing of the text mining outputs to allow for crossvalidation of a training and test set (80/20 split). The LDA model was further enhanced by updating the parameters to increase the number of passes over the corpus to 10 passes.

### Coherance values of LDA and HDA models
The inital assessment of the model performance produced the following overal coherance values:
* LDA had an overall coherance value of 0.383 for 7 topics
* HDP had an overall coherance value of 0.455 for 18 topics

The coherance values were further assesses on a topic level, generating the following tables:

LDA Coherance Values:
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/6cabf32b-8741-4a7a-8d23-ce098e742c46)

HDP Coherance Values:
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/16dca90c-a789-4522-8f5c-10a7a93acb10)


As supported by the literature review, the LDA model produced topics that were more clearly defined than that HDP model, as demonstrated by the Intertopic Distance Model Map When comparing the two maps (seen below), the results imply that the HDP model is characterized by high dimensonality, weak topic differenatation and similar topic content.

LDA Intertopic Distance Map & Top Relevant Keywords Per Topic (Sample 25)
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/f49cf930-b744-49db-825a-06f32f419fa3)

HDP Intertopic Distance Map & Top Relevant Keywords Per Topic (Sample 25)
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/39abab97-cbfc-4d4d-a438-466df37e4160)




