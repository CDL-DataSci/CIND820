# CIND820 - Big Data Analytics Project
TMU CIND820 Capstone Project - Parliament of Canada Hansard Debate Records (2006 - 2023)

This project is aims to explore what information can be gained through applying text mining and topic modeling approaches to the historical Hansard debate records from the Parliament of Canada. The identified dataset covers from April 2006 to December 2023 (39-1 Parliment to part of 44-1), which is a period of time that covers several election cycles and two Prime Ministerss. The data set includes 1972 pdf files in total and collectively represent 155,385 pages and 128,933,818 words.

The initial results of the comparative analysis between LDA and HDP models show that while HDP has greater flexibility in processing a corpus of text including not requiring defining total topics upfront, the outputs of the LDA model continue to produce individual topics that can be easily interpreted as distinct. However, the HDP model was able to identify a greater diversity of keywords that covered a higher proportion of documents that potentially would allow for a more nuanced assessment of changes in topic keywords across different timescales of either parliament sessions or calendar years. In terms of coherance values:
* For the sample size of 25, the HDP model was able to produce higher result (0.410 for LDA and 0.458 for HDP)
* For the sample size of 385, the LDA model was able to produce a higher result (0.701 for LDA and 0.315 for HDP)
* For the full dataset of 1972 documents, the LDA model was able to produce a higher result (0.628 for LDA and 0.319 for HDP)

With respect to the BERTopic model, initially processing limiations and capacity issues were encounterd due to compatability with the computer being leveraged. However, the use of a virtual machine that could leverage cloud computing to run the script proved to be a successful solution to the high computational demands of the BERTopic model. While BERTopic was able to identify 7 topics within the corpus, the ability for BERTopic to process documents without preprocessing worked out to be a disadvantage in the context of Hansard debate records that contain jargon and laguage related to protocol and parliamentary etiquette. The outcomes of the BERTopic are shared below.


## Background: Literature Review
The literature review of past research has highlighted the importance of a using a systematic approach to text mining techniques, the benefits of leveraging a combined topic model from LDA and TF-IDF, as well as considerations for evaluation of topic models and the validation of the labels for the extract topic. The literature review also helped to identify comparable alternatives to LDA that include HDP and the more recent BERTopic. While the literature review has identified possible advantages for these alternative topic models, there is a potential for these alternatives to be more computationally intensive and the performance of these different modeal will be explored in the final report. 

![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/e1bdf761-6018-4b6a-9861-0f0a63f746a4)

Original Data Source: https://www.ourcommons.ca/documentviewer/en/37-1/house/hansard-index

Sample of DataFrame created from fulldata set:
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/392c7ed8-a231-4d98-a8ea-4a27298e69f5)


## Relevant Source Code: Exploratory Analysis and Final Results
The the relevant files in this repository that have expored the LDA, HDP and BERTopic Models are referenced below. The files results are divided between "Initial Results" that assesed a representative sample of documents (s=385) as well as "Final Results" for analysis conducted on the full dataset:
* **Initial_Results_CreateSample**: documenting how two sample sizes were identified that randomly selected files from the full dataset
* **Initial_Results_HDP_LDA_Models**: Inital exploration of the algothrims for LDA and HDP topic models using a sample size of 25 files. The objectives were to test the general performance of the models in a time efficent manner.
* **Initial_Results_HDP_LDA_Models_Sample385**: The same code was run a statistically significant sameple size of 385 files out of the full 1972 pdfs from the dataset.
* **BERTopic_Model**: Initial assessment of the BERTopic model was limited due to the processing capacity and is a jupyter notebook that was run on a virtual machine. Some aspects of the script (e.g., pip install commands) have been included in the notebook due to the nature of running pyhton script on the virtual machine. 

Additionally, the source data for initial results can be found in the following folders:
* **Dataset_Sample**: 25 file sample that was leveraged by the LDA and HDP models
* **Dataset_Sample_385**: the larger sample of 385 files that was leveraged by the LDA and HDP models
* **Datasource**: the full set of documents collected from the Handsard archives.
### Summary of Findings in Initial Results:
Leveraging the outcomes from the Literature Reivew and exploratory analysis of the dataset, it was determined that the ideal number of topics for the LDA model was 7. This value will be carried forward into the analysis of the sample size of 25 and 385 files in order to compare the LDA and HDP models. Contrasting with the HDP model, when training this algorithm on the dataset (sample 25), a total of 19 topics were identified and when training on the sample of 385, a total of 39 topics were found.

Additionally, an n-folds cross validation was run against the representative sample (385 files) and the ideal number of topics for the LDA model was confirmed to be 7:

![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/8107196b-ed1d-4965-b4b8-766e5b180c50)

**Coherence Scores by Number of Topics:** 
* Number of Topics: 2, Coherence Score: 0.2777207278487633
* Number of Topics: 3, Coherence Score: 0.27948628535283787
* Number of Topics: 4, Coherence Score: 0.3497679850116785
* Number of Topics: 5, Coherence Score: 0.37398161141900993
* Number of Topics: 6, Coherence Score: 0.36098889812859786
* Number of Topics: 7, Coherence Score: 0.3949243102093841
* Number of Topics: 8, Coherence Score: 0.3793170579177607
* Number of Topics: 9, Coherence Score: 0.29408767522024126
* Number of Topics: 10, Coherence Score: 0.3189270003203882


Also improving on the literature review was updating the processing of the text mining outputs to allow for crossvalidation of a training and test set (80/20 split). The LDA model was further enhanced by updating the parameters to increase the number of passes over the corpus to 10 passes.

**Coherance values of LDA and HDA models**
The inital assessment of the model performance produced the following overal coherance values:
* LDA had an overall coherance value of 0.410 (s=25) and 0.701 (s=385) for 7 topics
* HDP had an overall coherance value of 0.458 for 19 topics (s=25) and 0.315 for 39 topics (s=385)

**Assessment of Topic Keywords**
Reviewing the outputs for each identified topic highlighted the differences between LDA and HDP being able to identify clearly distinct topics. For example, at first review of the LDA topics, it is noted that there were a least two very distinct topics for s=25 and three topicis for s=385 out of the 7 identified, which was further confirmed when isolating for representative text.

LDA Topic Keywords - Representative Text (s=25):
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/acebf3ac-7e8b-465f-8511-4cac1e5f7d2b)

LDA Topic Keywords - Representative Text (s=385)
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/ad7454d2-29e2-4aa6-a622-43de2a022905)

Comparing with the HDP model, while there were more total topics (19 & 39), there were many keywords that were common across the different topics that makes it hard for a person to interpret the differences. 

HDP Topic Keywords - Representative Text (s=25):
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/5f7ed2d1-5c94-46c2-9fea-76b0627f2c3c)

HDP Topic Keywords - Representative Text (s=385)
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/61f55e4e-3768-44f4-815d-173ae15d905d)

Further supporting the representative text table above, plotting the document wordcount against the total documents for each topic highlighted the same topic numbers for each model. For example, the two representative topics #0 and #5 in the LDA model for s=25 and topics #0, #2 and #4 are shown in the graphs below to contain the highest number of total documents.

LDA Model Outputs (s=25):
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/d50772ae-8d1d-49a7-ae9b-45f4b3bca712)

LDA Model Outputs (s=385):
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/2a967bbc-e6bb-457a-9ff9-61a84d0630a0)

HDP Model Outputs (s=25):
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/486299bf-a47f-4482-a52a-3d0aa2a94547)

HDP Model Outputs (s=385):
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/f472fc2b-7729-4d73-9606-8b65f16e51e5)



As supported by the literature review, the LDA model produced topics that were more clearly defined than that HDP model, as demonstrated by the Intertopic Distance Model Map When comparing the two maps (seen below), the results imply that the HDP model is characterized by high dimensonality, weak topic differenatation and similar topic content.

LDA Intertopic Distance Map & Top Relevant Keywords Per Topic (Sample 25)
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/49bf0cd7-e962-4569-a811-c48fbfad6286)

LDA Intertopic Distance Map & Top Relevant Keywords Per Topic (Sample 385)
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/602e8fdb-f960-4726-9c22-f2411376ba1b)

HDP Intertopic Distance Map & Top Relevant Keywords Per Topic (Sample 25)
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/4e18bf84-a103-40e6-a743-c0686942126e)

HDP Intertopic Distance Map & Top Relevant Keywords Per Topic (Sameple 385)
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/7b90bfbf-93f1-484f-a2e1-dee1a58c6435)

## Analysis Constraints:

Challenges with running the BERTopic model have typically resulted in the jyputer notebook kernel warnings that the kernel is dead and will be restarted. Error may relate to the Apple M1 processor (8 cores) of the computer being used for analyssi and compability issues with not having ability to run the script in parallel through the GPU. Otherwise, it could be limitations of the memory and processing capacity of the laptop currently being utilized.

![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/0a6d7e2d-0f9e-4bb3-a316-84f2af2c78a6)

Attempts to update and reinstall the python packages to resolve dependencies, such as transfomer package, through pip and conda have not been successful. Additionally, attempts to leverage the tensorflow package to be able to leverage the GPU in parallel to the CPU as a workaround for the Apple M1 chip have not yeilded resutls. 

Next steps inlcude further attempts to resolve the error BERTopic kernel terminating permaturely while running on current laptop. Alternatives would be to source a Windows terminal with sufficient processor and memory capacity to determine if this will resolve the obstacle. 



