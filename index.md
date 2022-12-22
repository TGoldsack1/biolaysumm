---
title: 
feature_image: "https://media.istockphoto.com/id/1254001828/vector/green-simple-pastel-soft-color-for-background-green-plain-color-for-wallpaper-green-pastel.jpg?s=612x612&w=0&k=20&c=9DlnNxAnSQUhcBUmnMpL4gOVAxC7spbhdd2dOOaW6Zg="
feature_text: |
  ### Shared task on the Lay Summarization of Biomedical Research Articles
  # BioLaySumm 2023
---

### Introduction
{: #intro}

Biomedical publications contain the latest research on prominent health-related topics, ranging from common illnesses to global pandemics. This can often result in their content being of interest to a wide variety of audiences including researchers, medical professionals, journalists, and even members of the public. However, the highly technical and specialist language used within such articles typically make it difficult for non-expert audiences to understand their contents.

Abstractive summarisation models can be used to generate a concise summary of an article, capturing its salient point using words and sentences that aren’t used in original text. As such, these models have the potential to help broaden access to highly technical documents when trained to generate summaries that are more readable, containing more background information and less technical terminology.

This shared task surrounds the abstractive summarisation of biomedical articles, with an emphasis on controllability and catering to non-expert audiences. Through this task, we aim to help foster increased research interest in controllable summarisation that helps broaden access to technical texts and progress towards more usable abstractive summarisation models in the biomedical domain.


<!-- ### News
{: #news}
-  -->

### Important Dates
{: #dates}

- **First call for participation:** January 6th, 2023
- **Releasing of training and validation data:** January 6th, 2023
- **Releasing of test data:** April 6th, 2023
- **Submission deadline:** April 20th, 2023
- **Preliminary papers due date:** May 4, 2023
- **Notification of acceptance:** June 1, 2023
- **Camera-ready system papers due:** June 13, 2023
- **Workshop Date:** July 13-14, 2023


### Task Definition
{: #task}

Our shared task will consist of two subtasks, focusing on readability-controlled summarisation and lay summarisation. More details on each subtask is given below:

#### Task 1: Lay Summarization
Given an article's abstract and main text as input, the goal is for participants to train a model (or models) to generate the lay summary. Two datasets (derived from PLOS and eLife) are provided for model training and will be used for evaluation. For the final evaluation, submissions will be ranked on the average performance across both datasets.

For this task, we encourage submissions generated from either 2 seperate summarisation models (e.g., one for each dataset) or a single unified model (e.g., trained on both datasets). Participants will be required to indicate which approach was taken for each submission.

#### Task 2: Readability-controlled Summarisation

Given an article’s main text as input, the goal is for participants to train a single model to generate both the technical abstract and the lay summary. One dataset (derived from PLOS) are provided for training and will be used for evaluation. For the final evaluation, submissions will be ranked on the average perfomance across both summary types.

### Datasets
{: #data}
The data that will be used across both subtasks is derived from articles published by the Public Library of Science (PLOS) [1,2] and eLife [1]. Each datset consists of the main text of biomedical research articles, in additional the technical abstract and expert-written lay summary. As detailed in the previous section, each form of summary will have a different utility for each subtask. The lay summaries of each dataset also exhibit numerous notable differences in their characteristics - for more details, please refer to the [1].

**Note: The test sets used for both tasks will be blind, and therefore will be different to those published alongside each papers.**  

All data for each subtask will be provided for the shared task's CodaLab page.

### Evaluation Metrics
{: #eval}

Our evaluation will assess the quality of generated summaries along **3** dimensions: **(a)** Relevance (ROUGE-1,2,L and BERTScore), **(b)** Readability (Flesch-Kincaid Grade Level and Coleman-Liau index), and **(c)** Factuality (SummaC).

### Organizers
{: #us}

- Tomas Goldsack, University of Sheffield
- Zheheng Luo, University of Manchester
- Qianqian Xie, University of Manchester
- Zhihao Zhang, Beihang University
- Chenghua Lin, University of Sheffield
- Carolin Scarton, University of Sheffield
- Sophia Ananiadou, University of Manchester

### References
{: #refs}

[1] *Tomas Goldsack, Zhihao Zhang, Chenghua Lin, Carolina Scarton. Making Science Simple: Corpora for the Lay Summarisation of Scientific Literature.
arXiv preprint arXiv:2210.09932, 2022.*

[2] *Zheheng Luo, Qianqian Xie, Sophia Ananiadou. Readability Controllable Biomedical Document Summarization.
arXiv preprint arXiv:2210.04705, 2022.*