---
title: BioLaySumm
feature_image: "https://media.istockphoto.com/id/1254001828/vector/green-simple-pastel-soft-color-for-background-green-plain-color-for-wallpaper-green-pastel.jpg?s=612x612&w=0&k=20&c=9DlnNxAnSQUhcBUmnMpL4gOVAxC7spbhdd2dOOaW6Zg="
feature_text: |
  # BioLaySumm 2023
  ##### Shared Task: Lay Summarization of Biomedical Research Articles @ BioNLP Workshop, ACL 2023
---

### Introduction
{: #intro}

Biomedical publications contain the latest research on prominent health-related topics, ranging from common illnesses to global pandemics. This can often result in their content being of interest to a wide variety of audiences including researchers, medical professionals, journalists, and even members of the public. However, the highly technical and specialist language used within such articles typically make it difficult for non-expert audiences to understand their contents.

Abstractive summarization models can be used to generate a concise summary of an article, capturing its salient point using words and sentences that aren’t used in the original text. As such, these models have the potential to help broaden access to highly technical documents when trained to generate summaries that are more readable, containing more background information and less technical terminology (i.e., a "lay summary").

This shared task surrounds the abstractive summarization of biomedical articles, with an emphasis on controllability and catering to non-expert audiences. Through this task, we aim to help foster increased research interest in controllable summarization that helps broaden access to technical texts and progress toward more usable abstractive summarization models in the biomedical domain.


### Updates
{: #news}
- March 6th, 2023 - More details on the evaluation protocol have been added to the [Evaluation Metrics](#eval) section.

### Important Dates
{: #dates}

- **First call for participation:** January 9th, 2023
- **Releasing of training and validation data:** January 9th, 2023
- **Releasing of test data:** April 6th, 2023
- **System submission deadline:** April 20th, 2023
- **System papers due date:** May 4th, 2023
- **Notification of acceptance:** May 30th, 2023
- **Camera-ready system papers due:** June 6th, 2023
- **BioNLP Workshop Date:** July 13th or 14th, 2023

Join our [Google Group](https://groups.google.com/g/biolaysumm-shared-task) for updates and discussion on the shared task! If you have any questions, please ask in the [Google Group](https://groups.google.com/g/biolaysumm-shared-task) or [email](mailto:tgoldsack1@sheffield.ac.uk) us.

### Registration and Submission
{: #reg}

- **Task 1**: [https://codalab.lisn.upsaclay.fr/competitions/9541](https://codalab.lisn.upsaclay.fr/competitions/9541)
- **Task 2**: [https://codalab.lisn.upsaclay.fr/competitions/9544](https://codalab.lisn.upsaclay.fr/competitions/9544)
### Task Definition
{: #task}

Our shared task will consist of two subtasks, focusing on readability-controlled summarization and lay summarization. More details on each subtask is given below:

#### Task 1: Lay Summarization
Given an article's abstract and main text as input, the goal is for participants to train a model (or models) to generate the lay summary. Two separate datasets (derived from biomedical journals, PLOS and eLife) are provided for model training and will be used for evaluation. For the final evaluation, submissions will be ranked on the average performance across both datasets.

For this task, submissions can be generated from either 2 separate summarization models (i.e., one trained on each dataset) or a single unified model (i.e., trained on both datasets). Participants will be required to indicate which approach was taken for each submission.

#### Task 2: Readability-controlled Summarization

Given an article’s main text as input, the goal is for participants to train a single model to generate both the technical abstract and the lay summary. One dataset (derived from PLOS) is provided for training and will be used for evaluation. For the final evaluation, submissions will be ranked on the average perfomance across both summary types.

### Datasets
{: #data}
The data that will be used across both subtasks is derived from articles published by the Public Library of Science (PLOS) [1,2] and eLife [1]. Each dataset consists of biomedical research articles, their technical abstracts, and their expert-written lay summaries. As detailed in the previous section, each form of summary will have a different utility for each subtask. The lay summaries of each dataset also exhibit numerous notable differences in their characteristics - for more details, please refer to [1].

PLOS is the larger of the two datasets, containing 24,773 instances for training and 1,376 for validation (the same for each subtask). eLife contains 4,346 instances for training and 241 for validation. More details on the test data will be provided closer to its release date (see [Important Dates](#dates)).  

**Note: The test sets used for both subtasks will be blind and therefore different to those published in either of the reference papers.**  

All data for both subtasks is provided via their respective CodaLab pages.

### Evaluation
{: #eval}

<!-- Our evaluation will assess the quality of generated summaries along **3** dimensions: **(a)** Relevance, **(b)** Readability, and **(c)** Factuality. More information on this coming soon. -->
For both subtasks, we will evaluate generated summaries across three aspects: Relevance, Readability, and Factuality. Each evaluation aspect will be composed of multiple automatic metrics. These are given below:

- **Relevance** - ROUGE (1, 2, and L) and BERTScore
- **Readability** - Flesch-Kincaid Grade Level (FKGL) and Dale-Chall Readability Score (DCRS)
- **Factuality** - FactCC and BARTScore (both fine-tuned on our datasets, as has shown to be effective in recent work [3])

More details on each how the given metrics will apply to each subtask are given below:

**Task 1: Lay Summarization** - The scores presented for each metric will be the average of those calculated independently for the generated lay summaries of PLOS and eLife. The aim is to maximize the scores for Relevance and Factuality metrics and minimize scores for Readability metrics.

**Task 2: Readability-controlled Summarization** - The scores presented for each metric will be the average of those calculated independently for the generated abstracts and lay summaries. Note that for Readability metrics, we will calculate the *absolute difference in scores* obtained for the abstracts and lay summaries of a given article. The aim is to maximize the scores for Relevance and Factuality metrics, and maximize the difference in abstract and lay summary scores for Readability metrics.

We will rank submissions based on each of these evaluation aspects independently.  
This will be done *after the test phase has ended* by applying min-max normalisation to the scores of each metric, before averaging across metrics within each evaluation aspect. During the test phase, participants will be able to view the metric scores obtained by a submission on the CodaLab leaderboard for each task.  An overall ranking will also be computed, which will be based on the lowest cumulative rank for each individual evaluation aspect.

A worked example of the described process for both subtasks is provided [here](https://docs.google.com/spreadsheets/d/1Eh2RAmmoUpZp5YAbzn9zPjaR-3IsLzPrW9JD1bpUXKQ/edit?usp=sharing).

### Organizers
{: #us}

- Chenghua Lin, Deputy Director of Research and Innovation in the Computer Science Department, University of Sheffield.
- Sophia Ananiadou, Turing Fellow, Director of the National Centre for Text Mining and Deputy Director of the Institute of Data Science and AI at the University of Manchester.
- Carolina Scarton, Computer Science Department at the University of Sheffield.
- Qianqian Xie, National Centre for Text Mining (NaCTeM).
- Tomas Goldsack, University of Sheffield.
- Zheheng Luo, the University of Manchester.
- Zhihao Zhang, Beihang University.

### References
{: #refs}

[1] *Tomas Goldsack, Zhihao Zhang, Chenghua Lin, Carolina Scarton. Making Science Simple: Corpora for the Lay Summarisation of Scientific Literature.
Proceedings of the 2022 Conference on Empirical Methods in Natural Language Processing (EMNLP 2022), Abu Dhabi. [url](https://aclanthology.org/2022.emnlp-main.724/)*

[2] *Zheheng Luo, Qianqian Xie, Sophia Ananiadou. Readability Controllable Biomedical Document Summarization.
Findings of the 2022 Conference on Empirical Methods in Natural Language Processing (EMNLP 2022 Findings), Abu Dhabi. [url](https://aclanthology.org/2022.findings-emnlp.343/)*

[3] *Huan Yee Koh, Jiaxin Ju, He Zhang, Ming Liu, Shirui Pan. How Far are We from Robust Long Abstractive Summarization? Proceedings of the 2022 Conference on Empirical Methods in Natural Language Processing (EMNLP 2022), Abu Dhabi. [url](https://aclanthology.org/2022.emnlp-main.172/)*