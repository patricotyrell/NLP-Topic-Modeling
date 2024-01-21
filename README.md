# Topic Modeling of COVID-19 Research
<img width="614" alt="Screenshot 2024-01-20 215647" src="https://github.com/patricotyrell/NLP-Topic-Modeling/assets/59300889/96708498-cb5c-49db-a321-693acf353bd6">

## Introduction
The COVID-19 pandemic has generated an immense volume of scholarly articles, presenting a challenge for researchers and policymakers to stay abreast of evolving trends. This project will apply Natural Language Processing (NLP) techniques for topic modeling and trend analysis to extract valuable insights from the COVID-19 Open Research Dataset (CORD-19). The purpose of the project was to use NLP to clearly define and interpret topics derived from scientific literature.

## 1. Data
The project utilized the COVID-19 Open Research Dataset (CORD-19) published on Kaggle. This was prepared by the White House and a coalition of leading research groups. The CORD-19 is a resource of over 1,000,000 scholarly articles, including over 400,000 with full text, about COVID-19, SARS-CoV-2, and related coronaviruses. See the link to the data source below:

* [CORD-19 Dataset](https://www.kaggle.com/code/divyapatel4/cord-19-dataset-cleaner/notebook#Finding-The-Number-Of-Best-Topics-As-Parameter)

## 2. Data Wrangling
[Full Data Wrangling Report](https://github.com/patricotyrell/NLP-Topic-Modeling/blob/410363b4b668a4ea6bc0c905990b147b516463e6/Topic%20Modeling%20Data%20Wrangling.ipynb)

Here are some of the high-level steps taken to prepare the CORD-19 dataset for analysis:

**1. Merging Metadata and JSON Files:**
>Metadata from CSV files was merged with the content of JSON files and a random sample of 10,000 papers was chosen from the merged dataset.

**2. Exclusion of Invalid and Missing Papers:**
>Papers with invalid formats and those lacking metadata or having empty body text were excluded from the sample. The resulting dataset comprised 8,656 papers.

**3. Language Identification and Filtering:**
>A language column was created to identify the language of each paper and of the 8,656 papers, 8,465 were identified as being in English, while non-English papers were dropped.

**4. Text Cleaning:**
>Both abstract and body text underwent a comprehensive cleaning process, including the removal of special characters, numbers, and punctuation using regular expressions; conversion of text to lowercase; tokenization of text into words, removal of stop words using NLTK's stop words; application of stemming using the Porter Stemmer.

## 3.Exploratory Data Analysis

[Full EDA Report](https://github.com/patricotyrell/NLP-Topic-Modeling/blob/410363b4b668a4ea6bc0c905990b147b516463e6/Topic%20Modeling%20EDA.ipynb)

In the abstracts, trigrams such as ('sar', 'cov', 'infect') and ('coronaviru', 'diseas', '2019') shed light on the virology and temporal context of the SARS-CoV virus. Notably, ('sever', 'acut', 'respiratori') and ('acut', 'respiratori', 'syndrom') highlight the severity and acute respiratory conditions associated with the virus. These findings, in the abstracts, serve as a snapshot, capturing key aspects of COVID-19 research and providing a high-level understanding of the priorities.

<img width="459" alt="Picture1" src="https://github.com/patricotyrell/NLP-Topic-Modeling/assets/59300889/cc7b12b9-03dc-49a1-8a44-1909156bcc6d">

The word clouds reveal terms such as "patient", "sar", "cov", and "model" were prominent throughout the papers.

<img width="468" alt="Picture 3" src="https://github.com/patricotyrell/NLP-Topic-Modeling/assets/59300889/09a9bccb-47b4-4b98-a1f6-ac2fc69a2461">


## 4. Preprocessing
[Preprocessing Report](https://github.com/patricotyrell/NLP-Topic-Modeling/blob/410363b4b668a4ea6bc0c905990b147b516463e6/NLP%20Topic%20Modeling%20-%20Preprocessing.ipynb)

The preprocessing pipeline for the abstracts and body texts involved several steps to prepare them for topic modeling. 
The cleaned and processed abstracts and body texts were transformed into a numerical representation called a Document-Term Matrix (DTM) using CountVectorizer. 
This matrix captures the frequency of each word in each document, providing a foundation for quantitative analysis and topic modeling of the research content. The final files were exported to be used for modeling.


## 5. Modeling & Evaluation
[Modeling Report](https://github.com/chicofanito/Capstone-2/blob/076e87994a52d55b0afb9871d50bf36c89e0c72c/data/Capstone%202%20-%20Substance%20Use%20Treatment%20-%20Modeling.ipynb)

In this research project, I utilized two topic modeling algorithms, Latent Dirichlet Allocation (LDA) and Non-Negative Matrix Factorization (NMF) techniques to extract and interpret topics from the extensive scientific literature on COVID-19.

The initial exploration considered both LDA and NMF as potential topic modeling algorithms. The decision to proceed with LDA was based on its inherent interpretability and higher coherence scores observed during preliminary analyses (Figure 3). Additionally, NMF's coherence scores were consistently lower, suggesting less semantically meaningful topics.

<img width="404" alt="Picture 4" src="https://github.com/patricotyrell/NLP-Topic-Modeling/assets/59300889/53740596-508e-4a50-9ab4-56b4cb579549">

## 6. Hyperparameter Tuning LDA Model

To optimize the performance of the LDA model, hyperparameter tuning was employed, aiming to enhance coherence and topic distinctiveness. Despite minimal differences in coherence scores before and after hyperparameter tuning, LDA was deemed more suitable for its ability to generate topics that align with the study's objectives and maintain consistency in theme representation. 

## 7. Topics Discovered

I determined that 5 topics were optical for the LDA model based on coherence and perplexity scores. The topics were as follows:

**Topic 1: General COVID-19 and Model-related**

*Keywords: covid, model, method, data, study, base, result, time, patient, perform*

**Topic 2: Pandemic and Social Impact**

*Keywords: covid, study, pandemic, result, social, health, student, effect, model, care*

**Topic 3: Patient and Disease Characteristics**

*Keywords: patient, covid, cov, sar, study, infect, disease, severe, risk, hospital*

**Topic 4: Vaccination and Health Research**

*Keywords: vaccine, health, study, covid, effect, research, pandemic, infect, result, cov*

**Topic 5: Cellular and Protein Aspects**

*Keywords: cell, sar, patient, study, infect, disease, protein, cov, effect, covid*

<img width="468" alt="Picture 5" src="https://github.com/patricotyrell/NLP-Topic-Modeling/assets/59300889/de5a862e-32cf-49ed-8361-8272f2a094a3">

## 8. Summary of Findings

The topics generated through Latent Dirichlet Allocation (LDA) modeling of the scientific literature on COVID-19 offer insight into the extensive body of work produced during the pandemic. These identified topics span a diverse range of themes, including general discussions on COVID-19, the societal impact of the pandemic, patient and disease characteristics, vaccination efforts, and cellular aspects of the virus. The consistency in themes across models, both before and after hyperparameter tuning, underscores the robustness of the topic identification process. These topics provide a structured representation in line with the study's goal of clearly defining and interpreting themes from the literature.
The following general conclusions and implications emerged from the findings:
>A. Diverse Research Themes: The identified topics encompass a wide array of research themes related to COVID-19, reflecting the diversity within the scientific literature on the subject.

>B. Consistency in Themes: Despite subtle changes after hyperparameter tuning, the overall themes and keywords within topics remain consistent, indicating the robustness of the identified topics.

>C. Interpretable Topics: The topics are interpretable and align with the broader context of COVID-19 research, providing valuable insights for researchers and practitioners into different aspects of the pandemic.

>D. Relevance to Study Goals: Aligned with the study's goal, the identified topics offer a structured representation of key themes in the literature, enhancing understanding of the research landscape.

>E. Implications for Further Analysis: The topics serve as a foundation for in-depth analysis, including exploration of subtopics, trends over time, and correlations between topics. Researchers can prioritize areas for further investigation based on the prevalence and significance of specific themes.

>F. Communication and Decision-Making: Insights from the topics are valuable for communicating key findings to diverse audiences, including policymakers, healthcare professionals, and the general public. Understanding prevalent themes is crucial for informed decision-making during the ongoing pandemic and future ones.

>G. Validation and Expert Input: While LDA models provide automated topic identification, validation by domain experts is essential. Collaboration with subject matter experts ensures that identified topics align with the latest developments and nuances in COVID-19 research.

## 9. Future Directions

1.	**Temporal Evolution of Research Themes**:
   
* Investigate the temporal evolution of topics within the COVID-19 literature. Analyze how research themes have shifted over time, identifying emerging topics and tracking the prevalence of key themes during different phases of the pandemic. This longitudinal analysis could provide insights into the dynamic nature of scientific discourse and evolving priorities in COVID-19 research.
  
3.	**Cross-Disciplinary Collaboration Analysis**:
   
* Explore the potential for cross-disciplinary collaboration in COVID-19 research by examining the co-occurrence of topics across different domains. Identify interdisciplinary intersections and assess the extent to which research themes from fields such as medicine, public health, social sciences, and technology converge. This could inform strategies for fostering collaboration and knowledge integration across diverse scientific communities.
  
5.	**Sentiment Analysis of Research Themes**:

* Conduct sentiment analysis on the identified topics to gauge the emotional tone and sentiment prevalent in COVID-19 literature. Analyzing sentiments associated with specific themes could provide insights into the emotional context of research findings. Understanding the emotional undertones may contribute to a more nuanced understanding of how scientific discourse reflects the challenges, concerns, or optimism within the research community.


## 10. Recommendations

1.	**Enhanced Validation with Expert Input**:
   
* Collaborate with domain experts, including researchers, clinicians, and public health professionals, to validate and refine the identified topics. Expert input can offer additional context, ensuring that the topics align with the latest developments, emerging trends, and nuances in COVID-19 research. This validation process enhances the reliability and accuracy of the identified topics.

3.	**Integration of External Data Sources**:
   
* Integrate external data sources, such as citation networks, funding information, or global health data, to enrich the context around identified topics. Linking topics to citation patterns or funding sources can provide a broader understanding of the impact and influence of specific research themes. This integrated approach contributes to a more comprehensive analysis of the research landscape.

3.	**Interactive Visualization for Knowledge Exploration**:
  
* Develop interactive visualization tools to facilitate knowledge exploration for researchers, policymakers, and the general public. Create user-friendly interfaces that allow stakeholders to navigate and explore the identified topics, enabling a deeper understanding of the interconnectedness of themes. Visualization tools can enhance the accessibility of complex research insights and promote data-driven decision-making.



