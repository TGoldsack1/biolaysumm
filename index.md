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
- **March 6th, 2023** - More details on the evaluation protocol have been added to the [Evaluation](#eval) section.
- **April 5th, 2023** - The [evaluation](#eval) protocol has been altered slightly due to reliability issues with the FactCC metric, and the evaluation scripts have now been released for participants on GitHub.
- **April 5th, 2023** - New competition pages for each subtask have been published, and the [registration](#reg) links have been updated.
- **April 19th, 2023** - Deadline extended for the evaluation phase. The new deadline is **April 24th, 2023**.
- **April 25th, 2023** - System [paper submission](#sys) details added to the site.
- **April 27th, 2023** - Competition [results](#res) for both subtasks have been added to the site.
### Important Dates
{: #dates}

- **First call for participation:** January 9th, 2023
- **Releasing of training and validation data:** January 9th, 2023
- **Releasing of test data:** April 6th, 2023
- **System submission deadline:** ~~April 20th, 2023~~ April 24th, 2023
- **System papers due date:** May 4th, 2023
- **Notification of acceptance:** May 30th, 2023
- **Camera-ready system papers due:** June 6th, 2023
- **BioNLP Workshop Date:** July 13th or 14th, 2023

Join our [Google Group](https://groups.google.com/g/biolaysumm-shared-task) for updates and discussion on the shared task! If you have any questions, please ask in the [Google Group](https://groups.google.com/g/biolaysumm-shared-task) or [email](mailto:tgoldsack1@sheffield.ac.uk) us.

### Registration and Submission
{: #reg}

- **Task 1**: [https://codalab.lisn.upsaclay.fr/competitions/12125](https://codalab.lisn.upsaclay.fr/competitions/12125)
- **Task 2**: [https://codalab.lisn.upsaclay.fr/competitions/12127](https://codalab.lisn.upsaclay.fr/competitions/12127)

*Note - due to competition editing restrictions in CodaLab, new competitions pages have been created as of 5/05/23, the links to which are now provided above. The sumission rules have also been added to these new competition pages, please make sure to read these prior to submitting.*

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

PLOS is the larger of the two datasets, containing 24,773 instances for training and 1,376 for validation (the same for each subtask). eLife contains 4,346 instances for training and 241 for validation.

The test data for subtask 1 is composed of 142 PLOS article and 142 eLife articles. The test data for subtask 2 is composed of 142 PLOS articles (however, these are different from the used in subtask 1).

**Note: The test sets used for both subtasks are different to those published in either of the reference papers.**  

All data for both subtasks is provided via their respective CodaLab pages.

### Evaluation
{: #eval}

<!-- Our evaluation will assess the quality of generated summaries along **3** dimensions: **(a)** Relevance, **(b)** Readability, and **(c)** Factuality. More information on this coming soon. -->
For both subtasks, we will evaluate generated summaries across three aspects: Relevance, Readability, and Factuality. Each evaluation aspect will be composed of multiple automatic metrics:

- **Relevance** - ROUGE (1, 2, and L) and BERTScore
- **Readability** - Flesch-Kincaid Grade Level (FKGL) and Dale-Chall Readability Score (DCRS)
- **Factuality** - BARTScore (fine-tuned on our datasets, as has shown to be effective in recent work [3])

*Note - FactCC was previously included as a Factuality metric, but was recently removed due to reliability issues.*

More details on each how the given metrics will apply to each subtask are given below:

**Task 1: Lay Summarization** - The scores presented for each metric will be the average of those calculated independently for the generated lay summaries of PLOS and eLife. The aim is to maximize the scores for Relevance and Factuality metrics and minimize scores for Readability metrics.

**Task 2: Readability-controlled Summarization** - The scores presented for each metric will be the average of those calculated independently for the generated abstracts and lay summaries. Note that, for Readability metrics in this subtask, we use the *absolute difference between the scores of every generated summary and target summary pair*. The aim is to maximize the scores for Relevance and Factuality metrics and minimize the *absolute difference scores* calculated for Readability metrics.

We will rank submissions based on each of these evaluation aspects independently. This will be done *after the test phase has ended* by applying min-max normalization to the scores of each metric, before averaging across metrics within each evaluation aspect. An overall ranking will also be computed, which will be based on the lowest cumulative rank for each individual evaluation aspect.

A worked example of the described process for both subtasks is provided [here](https://docs.google.com/spreadsheets/d/1Eh2RAmmoUpZp5YAbzn9zPjaR-3IsLzPrW9JD1bpUXKQ/edit?usp=sharing).


**To help participants with model selection, the evaluation scripts for both subtasks (configured to run on the validation data) are now available on [GitHub](https://github.com/TGoldsack1/BioLaySumm2023-evaluation_scripts)**

### Results
{: #res}

The teams with top three ranking submissions for each subtask (overall, and for each criteria), as determined by the evaluation proceedure described in the [evaluation section](#eval), are given below:

***
**Subtask 1**

| **Criterion** | **1st**    | **2nd**       | **3rd**              |
| :---          |   :----:   |     :---:     |        :----:        |
| Relevance     | *LHS712EE* | *daixiang*    | *MDC*                |
| Readability   | *IITR*     | *APTSumm*     | *IKM_Lab*            |
| Factuality    | *Baseline* | *LHS712EE*    | *MDC*                |
| **Overall**   | *MDC*      | *Baseline*    | *V-NLP*, *daixiang*  |

***
**Subtask 2**

| **Criterion** | **1st**                                       | **2nd**     | **3rd**              |
| :---          |                     :---:                     |    :---:    |        :----:        |
| Relevance     | *NCUEE-NLP*                                   | *LHS712EE*  | *Pathology Dynamics* |
| Readability   | *Pathology Dynamics*                          | *NCUEE-NLP* | *LHS712EE*           |
| Factuality    | *Baseline*                                    | *LHS712EE*  | *Pathology Dynamics* |
| **Overall**   | *Pathology Dynamics*, *NCUEE-NLP*, *LHS712EE* | -           | -                    |

***

The full table of results for both subtasks is provided [here](https://docs.google.com/spreadsheets/d/1HKM-bOu_SG-vlwdhIbl4WJ9baSRqZWiskoH3rT77Oio/edit?usp=sharing), alongside the calculation of rankings.

### System Paper Submission
{: #sys}

All participating teams are invited to submit system papers that, pending review, will be published as part of the BioNLP Workshop proceedings.

**Submission** - To submit a system paper, please use the following link before the deadline on 04/05/2023 (23:59:59, Anywhere on Earth timezone):
[https://softconf.com/acl2023/BioNLP2023-ST/](https://softconf.com/acl2023/BioNLP2023-ST/)


**Format** - System papers should follow the ACL 2023 short paper format (i.e., 4 pages, with unlimited pages for appendices and references), as described on the call for papers where templates are also provided.
In the case that a participant has submitted to both subtasks using two distinct modelling approaches, we will allow them 1 additional page of content.

The paper titles should start with one of the following prefixes:
- "{TEAM_NAME} at BioLaySumm Task 1:" (systems submitted only to task 1)
- "{TEAM_NAME} at BioLaySumm Task 2:" (systems submitted only to task 2)
- "{TEAM_NAME} at BioLaySumm:" (systems submitted to both tasks)

followed by a desciptive title of the proposed system system. Papers should be submitted in non-anonymised format (i.e., with author names included).


**References** - We ask participants to ensure the following citations are included in their system papers:

1. *The overview paper* (use when referring to the shared task in general) - note, this is a temporary example that may be subject to change in the future
```
@inproceedings{biolaysumm-2023-overview,
    title = "Overview of the BioLaySumm 2023 Shared Task on Lay Summarization of Biomedical Research Articles",
    author = "Goldsack, Tomas and 
       Luo, Zheheng and 
       Xie, Qianqian and 
       Scarton, Carolina and
       Shardlow, Matthew and 
       Ananiadou, Sophia and 
       Lin, Chenghua",
    booktitle = "Proceedings of the 22st Workshop on Biomedical Language Processing",
    month = July,
    year = "2023",
    address = "Toronto, Canada",
    publisher = "Association for Computational Linguistics"
}
```

2. *Task datasets* (please use both of the following):
```
@inproceedings{goldsack-etal-2022-making,
    title = "Making Science Simple: Corpora for the Lay Summarisation of Scientific Literature",
    author = "Goldsack, Tomas  and
      Zhang, Zhihao  and
      Lin, Chenghua  and
      Scarton, Carolina",
    booktitle = "Proceedings of the 2022 Conference on Empirical Methods in Natural Language Processing",
    month = dec,
    year = "2022",
    address = "Abu Dhabi, United Arab Emirates",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2022.emnlp-main.724",
    pages = "10589--10604",,
}
```
```
@inproceedings{luo-etal-2022-readability,
    title = "Readability Controllable Biomedical Document Summarization",
    author = "Luo, Zheheng  and
      Xie, Qianqian  and
      Ananiadou, Sophia",
    booktitle = "Findings of the Association for Computational Linguistics: EMNLP 2022",
    month = dec,
    year = "2022",
    address = "Abu Dhabi, United Arab Emirates",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2022.findings-emnlp.343",
    pages = "4667--4680",
}
```

**Reviewer Nomination** - Similar to other shared task campaigns (e.g. SemEval), we are requiring that at least one author per paper also acts as a reviewer for our shared task papers. Please nominate the reviewer from your submission using [this form](https://docs.google.com/forms/d/e/1FAIpQLSdYbA0e4WGeftNylK3ieK0sYongdNAVRf5Jqsqe8BwVAth1TA/viewform). If you do not nominate a reviewer, the corresponding author(s) will be automatically selected.

### Organizers
{: #us}

- Chenghua Lin, Deputy Director of Research and Innovation in the Computer Science Department, University of Sheffield.
- Sophia Ananiadou, Turing Fellow, Director of the National Centre for Text Mining and Deputy Director of the Institute of Data Science and AI at the University of Manchester.
- Carolina Scarton, University of Sheffield.
- Matthew Shardlow, Manchester Metropolitan University.
- Paul Thompson, University of Manchester amd The National Centre for Text Mining.
- Qianqian Xie, National Centre for Text Mining.
- Tomas Goldsack, University of Sheffield.
- Zheheng Luo, University of Manchester.

### References
{: #refs}

[1] *Tomas Goldsack, Zhihao Zhang, Chenghua Lin, Carolina Scarton. Making Science Simple: Corpora for the Lay Summarisation of Scientific Literature.
Proceedings of the 2022 Conference on Empirical Methods in Natural Language Processing (EMNLP 2022), Abu Dhabi. [url](https://aclanthology.org/2022.emnlp-main.724/)*

[2] *Zheheng Luo, Qianqian Xie, Sophia Ananiadou. Readability Controllable Biomedical Document Summarization.
Findings of the 2022 Conference on Empirical Methods in Natural Language Processing (EMNLP 2022 Findings), Abu Dhabi. [url](https://aclanthology.org/2022.findings-emnlp.343/)*

[3] *Huan Yee Koh, Jiaxin Ju, He Zhang, Ming Liu, Shirui Pan. How Far are We from Robust Long Abstractive Summarization? Proceedings of the 2022 Conference on Empirical Methods in Natural Language Processing (EMNLP 2022), Abu Dhabi. [url](https://aclanthology.org/2022.emnlp-main.172/)*