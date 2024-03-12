# CIND820 - Big Data Analytics Project
TMU CIND820 Capstone Project - Parliament of Canada Hansard Debate Records (2006 - 2023)

This project is aims to explore what information can be gained through applying text mining and topic modeling approaches to the historical Hansard debate records from the Parliament of Canada. The identified dataset covers from 2006 to 2023 (39-1 Parliment to part of 44-1). The data set includes 1972 pdf files in total and collectively represent 155,385 pages.

The initial results of the comparative analysis between LDA and HDP models show that while HDP has greater flexibility in processing a corpus of text including not requiring defining total topics upfront, the outputs of the LDA model continue to produce topics that can be easily interpreted as distinct. However, the HDP model was able to identify a greater diversity of keywords within each topic that potentially would allow for a more nuanced assessment of changes in topic keywords across different timescales of either parliament sessions or calendar years. In terms of coherance values, the HDP model was able to produce higher results (0.383 for LDA and 0.502 for HDP). 

## Step 1: Literature Review
The literature review of past research has highlighted the importance of a using a systematic approach to text mining techniques, the benefits of leveraging a combined topic model from LDA and TF-IDF, as well as considerations for evaluation of topic models and the validation of the labels for the extract topic. The literature review also helped to identify comparable alternatives to LDA that include HDP and the more recent BERTopic. While the literature review has identified possible advantages for these alternative topic models, there is a potential for these alternatives to be more computationally intensive and the performance of these different modeal will be explored in the final report. 

Original Data Source: https://www.ourcommons.ca/documentviewer/en/37-1/house/hansard-index

## Step 2: Initial Results
The initial results expored the LDA, HDP and BERTopic Models on a sample of the full dataset. The initial results are divided between the following jupyter notebook files:
* **Initial_Results_CreateSample**: documenting how two sample sizes were identified that randomly selected files from the full dataset
* **Initial_Results_HDP_LDA_Models**: Inital exploration of the algothrims for LDA and HDP topic models using a sample size of 25 files. The objectives were to test the general performance of the models in a time efficent manner.
* **Initial_Results_HDP_LDA_Models_Sample385**: The same code was run a statistically significant sameple size of 385 files out of the full 1972 pdfs from the dataset.
* **Initial_Results_BERTopic**: Initial assessment of the BERTopic model was limited due to the processing capacity and potential combatability conflicts with running the BERTopic on an Apple M1 processor.

Additionally, the source data for initial results can be found in the following folders:
* **Dataset_Sample**: 25 file sample that was leveraged by the LDA and HDP models
* **Dataset_Sample_385**: the larger sample of files that was leveraged by the LDA and HDP models
* **Dataset_BERTopic**: the limited dataset used to run the BERTopic model

### Summary of Findings in Initial Results:
Leverating the outcomes from the Literature Reivew and exploratory analysis of the dataset, it was determined that the ideal number of topics for the LDA model was 7. This value will be carried forward into the analysis of the sample size of 25 and 385 files in order to compare the LDA and HDP models. Contrasting with the HDP model, when training this algorithm on the dataset (sample 25), a total of 19 topics were identified.

Also improving on the literature review was updating the processing of the text mining outputs to allow for crossvalidation of a training and test set (80/20 split). The LDA model was further enhanced by updating the parameters to increase the number of passes over the corpus to 10 passes.

**Coherance values of LDA and HDA models**
The inital assessment of the model performance produced the following overal coherance values:
* LDA had an overall coherance value of 0.410 for 7 topics
* HDP had an overall coherance value of 0.458 for 19 topics

**Assessment of Topic Keywords**
Reviewing the outputs for each identified topic highlighted the differences between LDA and HDP being able to identify clearly distinct topics. For example, at first review of the LDA topics, it is noted that there were a least two very distinct topics out of the 7 identified, which was further confirmed when isolating for representative text.

LDA Topic Keywords:
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/522ed12c-ca91-48ae-93e0-1261ac55e96a)

This is further underscored when narrowing the table down to keywords for three topics for the representative text
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/acebf3ac-7e8b-465f-8511-4cac1e5f7d2b)


Comparing with the HDP model, while there were more total topics (19), there were many keywords that were common across the different topics that makes it hard for a person to interpret the differences. 

HDP Topic Keywords:
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/57d0bed0-7d0f-48f0-84e5-972d5e4b1317)

HDP Representative Text narrowed down the list to keywords from 9 topics
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/5f7ed2d1-5c94-46c2-9fea-76b0627f2c3c)


Further supporting the representative text table above, plotting the document wordcount against the total documents for each topic highlighted the same topic numbers for each model. For example, the two representative topics #0 and #5 in the LDA model are shown in the graphs below to contain the highest number of total documents.

LDA Model Outputs:
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/d50772ae-8d1d-49a7-ae9b-45f4b3bca712)

HDP Model Outputs:
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/486299bf-a47f-4482-a52a-3d0aa2a94547)


As supported by the literature review, the LDA model produced topics that were more clearly defined than that HDP model, as demonstrated by the Intertopic Distance Model Map When comparing the two maps (seen below), the results imply that the HDP model is characterized by high dimensonality, weak topic differenatation and similar topic content.

LDA Intertopic Distance Map & Top Relevant Keywords Per Topic (Sample 25)
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/49bf0cd7-e962-4569-a811-c48fbfad6286)

HDP Intertopic Distance Map & Top Relevant Keywords Per Topic (Sample 25)
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/4e18bf84-a103-40e6-a743-c0686942126e)




