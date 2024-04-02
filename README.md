# CIND820 - Big Data Analytics Project
**TMU CIND820 Capstone Project - Parliament of Canada Hansard Debate Records (2006 - 2023)**

This project is aims to explore what information can be gained through applying text mining and topic modeling approaches to the historical Hansard debate records from the Parliament of Canada. The identified dataset covers from April 2006 to December 2023 (39-1 Parliment to part of 44-1), which is a period of time that covers several election cycles and two Prime Ministerss. The data set includes 1972 pdf files in total and collectively represent 155,385 pages and 128,933,818 words.

The initial results of the comparative analysis between LDA and HDP models show that while HDP has greater flexibility in processing a corpus of text including not requiring defining total topics upfront, the outputs of the LDA model continue to produce individual topics that can be easily interpreted as distinct. However, the HDP model was able to identify a greater diversity of keywords that covered a higher proportion of documents that potentially would allow for a more nuanced assessment of changes in topic keywords across different timescales of either parliament sessions or calendar years. In terms of coherance values:
* For the sample size of 25, the HDP model was able to produce higher result (0.410 for LDA and 0.458 for HDP)
* For the sample size of 385, the LDA model was able to produce a higher result (0.701 for LDA and 0.315 for HDP)
* For the full dataset of 1972 documents, the LDA model was able to produce a higher result (0.628 for LDA and 0.319 for HDP)

With respect to the BERTopic model, initially processing limiations and capacity issues were encounterd due to compatability with the computer being leveraged. However, the use of a virtual machine that could leverage cloud computing to run the script proved to be a successful solution to the high computational demands of the BERTopic model. While BERTopic was able to identify 7 topics within the corpus, the ability for BERTopic to process documents without preprocessing worked out to be a disadvantage in the context of Hansard debate records that contain jargon and laguage related to protocol and parliamentary etiquette. The outcomes of the BERTopic are shared below.


## Background: Literature Review
The literature review of past research has highlighted the importance of a using a systematic approach to text mining techniques, the benefits of leveraging a combined topic model from LDA and TF-IDF, as well as considerations for evaluation of topic models and the validation of the labels for the extract topic. The literature review also helped to identify comparable alternatives to LDA that include HDP and the more recent BERTopic. While the literature review has identified possible advantages for these alternative topic models, there is a potential for these alternatives to be more computationally intensive and the performance of these different modeal will be explored in the final report. 

Copies of research articles that are refenced in the final paper can be found in **/Reports/Literature_Review_Articles/**

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
  
### Preprocessing - Determining Total Topics for LDA Model:
Leveraging the outcomes from the Literature Reivew and exploratory analysis of the dataset, it was determined that the ideal number of topics for the LDA model was 7. This value was carried forward into the analysis of representative same (s=385) and the full dataset (s=1972). 
The total number of topics to use in the LDA was determined through an assessement of coherance across a range of topic numbers (2-10 and 2-40).

![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/8107196b-ed1d-4965-b4b8-766e5b180c50)
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/84c39148-99ba-4aff-9d33-30a0dc137621)


## Model Performance - Coherence Values

**Coherance values of LDA**
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/1eb0fa47-54b3-47d2-810b-b60ee7354fd6)
<img width="468" alt="image" src="https://github.com/CDL-DataSci/CIND820/assets/160800059/2fdf8eea-0366-4efb-9798-6f7e6dc2c7b3">

**Coherance values of HDP model**
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/fd6c0725-a964-40f3-bfe3-307fb46bfff2)
<img width="738" alt="image" src="https://github.com/CDL-DataSci/CIND820/assets/160800059/066b36a9-0bd1-49b8-b070-17e7a931492c">

The inital assessment of the model performance produced the following overal coherance values:
* LDA had an overall coherance value of 0.410 (s=25) and 0.701 (s=385) for 7 topics
* HDP had an overall coherance value of 0.458 for 19 topics (s=25) and 0.315 for 39 topics (s=385)

**Assessment of Topic Keywords**
Reviewing the outputs for each identified topic highlighted the differences between LDA and HDP being able to identify clearly distinct topics. For example, at first review of the LDA topics, it is noted that there were a least three distinct topics out of 7 for s=385, which was further confirmed when isolating for representative text.

LDA Topic Keywords - Representative Text (s=385)
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/ad7454d2-29e2-4aa6-a622-43de2a022905)

Comparing with the HDP model, while there were more total topics, there were many keywords that were common across the different topics that makes it hard for a person to interpret the differences between each individual topic. However, collectively the identified keywords were found across a higher percentage of total documents in the dataset. 

HDP Topic Keywords - Representative Text (s=385)
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/61f55e4e-3768-44f4-815d-173ae15d905d)

Further supporting the representative text table above, plotting the document wordcount against the total documents for each topic highlighted the same topic numbers for each model. For example, the two representative topics #0 and #5 in the LDA model for s=25 and topics #0, #2 and #4 are shown in the graphs below to contain the highest number of total documents.

**LDA Model Outputs (s=385):**
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/2a967bbc-e6bb-457a-9ff9-61a84d0630a0)

**HDP Model Outputs (s=385):**
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/f472fc2b-7729-4d73-9606-8b65f16e51e5)

Further assessment of the LDA model which produced topics that were more clearly defined than that HDP model, as demonstrated by the Intertopic Distance Model Map When comparing the two maps (seen below). The results imply that the HDP model is characterized by high dimensonality, weak topic differenatation and similar topic content.

LDA Intertopic Distance Map & Top Relevant Keywords Per Topic (Sample 385)
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/602e8fdb-f960-4726-9c22-f2411376ba1b)

HDP Intertopic Distance Map & Top Relevant Keywords Per Topic (Sameple 385)
![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/7b90bfbf-93f1-484f-a2e1-dee1a58c6435)

**BERTopic Model Outputs (s=385)**
The BERTopic model was trained on the dataset without preprocessing and leveraged many of the default parameters. However, due to the nature of the Hansard debate records, the identified topics were dominated by the protocol jargon and parliamentary etiquette terms that were removed during the preprocessing stage for the LDA and HDP models. Further evaluation of the BERTopic Model may require some degree of preprocessing prior to running the model.

<img width="635" alt="image" src="https://github.com/CDL-DataSci/CIND820/assets/160800059/c0d5a757-f85a-4f0d-8629-4970562473fb">
<img width="468" alt="image" src="https://github.com/CDL-DataSci/CIND820/assets/160800059/8161be02-32cc-4819-9fb4-aaa1eea6d701">

## Analysis Constraints & Limitations:

The computing and processing resources required to model the Hansard debate records proved challenging, especially when running the BERTopic model. In order to complete the training of the BERTopic, a virtual machine was leveraged inorder to access higher processing capacity (CPUs, RAM and GPU resources). 

Even with access to the virtual machine, the long processing times required to preprocess text, train the models and conduct analysis of coherenace values limited the extent of analysis conducted. Considerations for future research to incorporate bigrams and trigrams into the corpus of text to train the LDA and HDP models is just one example of additional steps that can be taken to improve model performance. 

![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/39fce3a5-6084-4071-9d97-7ed8bff134e4)

![image](https://github.com/CDL-DataSci/CIND820/assets/160800059/3d80388d-6968-4030-a3a3-5afa07e5138a)
