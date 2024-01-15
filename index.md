---
title: BioLaySumm
# feature_image: "https://media.istockphoto.com/id/1254001828/vector/green-simple-pastel-soft-color-for-background-green-plain-color-for-wallpaper-green-pastel.jpg?s=612x612&w=0&k=20&c=9DlnNxAnSQUhcBUmnMpL4gOVAxC7spbhdd2dOOaW6Zg="
# feature_image: "https://i.postimg.cc/tTtgwdYq/DALL-E-2024-01-10-12-32-19-Extend-the-background-of-the-image4.jpg"
# feature_image: "https://i.postimg.cc/bwHwVHMm/image1.webp"
feature_image: "https://i.postimg.cc/mD23gyKD/DALL-E-2024-01-10-12-32-19-Extend-the-background-of-the-image3.jpg"
feature_text: |
  # BioLaySumm 2024
  ##### Shared Task: Lay Summarization of Biomedical Research Articles @ BioNLP Workshop, ACL 2024
---


### Introduction
{: #intro}

Biomedical publications contain the latest research on prominent health-related topics, ranging from common illnesses to global pandemics. This can often result in their content being of interest to a wide variety of audiences including researchers, medical professionals, journalists, and even members of the public. However, the highly technical and specialist language used within such articles typically make it difficult for non-expert audiences to understand their contents.

<!-- Abstractive summarization can be used to generate a concise summary of an article, capturing its salient point using words and sentences that aren’t used in the original text. As such, these models have the potential to help broaden access to highly technical documents when trained to generate summaries that are more readable, containing more background information and less technical terminology (i.e., a "lay summary"). -->

The BioLaySumm shared task surrounds the abstractive summarization of biomedical articles, with an emphasis on catering to non-expert audiences through the generation of summaries that are more readable, containing more background information less technical terminology (i.e., a "lay summary").

This is the 2nd iteration of BioLaySumm, following the success of the [1st edition](/2023) of the task at BioNLP 2023 [1] which attracted 56 submission accross 20 different teams. In this edition, we aim to build on last year's task by introducing a new test set, updating our evaluation protocol, and encouraging participants to explore novel approaches that will help to further advance the state-of-the-art for Lay Summarization. For inspiration, we provide some indeas of promising research directions [below](#prom).

<!-- ### Updates
{: #news}
- **March 6th, 2023** - More details on the evaluation protocol have been added to the [Evaluation](#eval) section.
- **April 5th, 2023** - The [evaluation](#eval) protocol has been altered slightly due to reliability issues with the FactCC metric, and the evaluation scripts have now been released for participants on GitHub.
- **April 5th, 2023** - New competition pages for each subtask have been published, and the [registration](#reg) links have been updated.
- **April 19th, 2023** - Deadline extended for the evaluation phase. The new deadline is **April 24th, 2023**.
- **April 25th, 2023** - System [paper submission](#sys) details added to the site.
- **April 27th, 2023** - Competition [results](#res) for both subtasks have been added to the site. -->

### Important Dates
{: #dates}

- **First call for participation:** January, 2024
- **Releasing of training and validation data:** January, 2024
- **System submission deadline:** May 6th, 2024
- **System papers due date:** May 20th, 2024
- **Notification of acceptance:** June 20th, 2024
- **Camera-ready system papers due:** July 11th, 2024 (23:59:59 AoE)
- **BioNLP Workshop Date:** August 15th-16th, 2024

Join our [Google Group](https://groups.google.com/g/biolaysumm2024) for updates and discussion on the shared task! If you have any questions, please ask in the [Google Group](https://groups.google.com/g/biolaysumm2024) or [email](mailto:tgoldsack1@sheffield.ac.uk) us.

### Registration and Submission
{: #reg}

<!-- **CodaLab page**: [https://codalab.lisn.upsaclay.fr/competitions/12125](https://codalab.lisn.upsaclay.fr/competitions/12125) -->
**CodaLab page**: *coming soon!*


### Task Definition: Lay Summarization
{: #task}
 
Given an article's abstract and main text as input, the goal is for participants to train a model (or models) to generate the lay summary. Two separate datasets (derived from biomedical journals, PLOS and eLife) are provided for model training and will be used for evaluation. For the final evaluation, submissions will be ranked on the average performance across both datasets.

Note that submissions can be generated from either 2 separate summarization models (i.e., one trained on each dataset) or a single unified model (i.e., trained on both datasets). Participants will be required to indicate which approach was taken for each submission.

### Datasets
{: #data}
The data that will be used for the task is based on the PLOS and eLife datasets, published in [2]. Each dataset consists of biomedical research articles ( including their technical abstracts) and their expert-written lay summaries. The lay summaries of each dataset also exhibit numerous notable differences in their characteristics - for more details, please refer to [2].

PLOS is the larger of the two datasets, containing 24,773 instances for training and 1,376 for validation. eLife contains 4,346 instances for training and 241 for validation. These splits are identical to those used in [2].

The test data is composed of 142 PLOS article and 142 eLife articles. **Note: These test splits are different to those published in [2] and used for the 1st edition of BioLaySumm [1].**  

All data is provided via the competition CodaLab page.

### Evaluation
{: #eval}

<!-- Our evaluation will assess the quality of generated summaries along **3** dimensions: **(a)** Relevance, **(b)** Readability, and **(c)** Factuality. More information on this coming soon. -->
For both subtasks, we will evaluate generated summaries across three aspects: Relevance, Readability, and Factuality. Each evaluation aspect will be composed of multiple automatic metrics:

- **Relevance** - ROUGE (1, 2, and L) and BERTScore
- **Readability** - Flesch-Kincaid Grade Level (FKGL) and Dale-Chall Readability Score (DCRS), Coleman-Liau Index (CLI), and LENS
- **Factuality** - AlignScore, SummaC

The scores presented for each metric will be the average of those calculated independently for the generated lay summaries of PLOS and eLife. The aim is to maximize the scores for Relevance metrics, Factuality metrics, and the LENS (Readability) metric and minimize scores for all other Readability metrics.

We will rank submissions based on each of these evaluation aspects independently. This will be done *after the test phase has ended* by applying min-max normalization to the scores of each metric, before averaging across metrics within each evaluation aspect. A ranking for each evaluation aspect will be computed as well as an overall ranking, which will be based on the best average score across all three aspects.

In the near future, we will update this section to provide a link to a worked example of the described ranking process.

### Promising Research Directions
{: #prom}

- **Retrieval-Augmented Generation (RAG)** - Recent work has shown that the incorperation of external knowledge derived from graphs can help to improve the quality of generated summaries [3]. The automatic identification and retrieval of relevant textual knowledge is likely to provide similar benefits, and we encourage participants to explore this direction.

- **Controllable Lay Summarisation** - The lay summaries of PLOS and eLife exhibit numerous notable differences in their characteristics, including their length, readability, and abstractivness [2]. We encourage participants to explore the use of controllable generation techniques to produce summaries that are tailored to the characteristics of each dataset and enable models to cater to the needs of different audiences.

- **LLMs for Data Augmentation** - In the first edition of BioLaySumm [1], we found that the use of large language models (LLMs) proved benefitial for summary generation [4], but also for data augmentation [5]. We encourage participants to explore this direction further, and to consider potential new ways to use use LLMs for both summary generation and data augmentation.


<!-- for both subtasks is provided [here](https://docs.google.com/spreadsheets/d/1Eh2RAmmoUpZp5YAbzn9zPjaR-3IsLzPrW9JD1bpUXKQ/edit?usp=sharing). -->

<!-- **To help participants with model selection, the evaluation scripts for both subtasks (configured to run on the validation data) are now available on [GitHub](https://github.com/TGoldsack1/BioLaySumm2023-evaluation_scripts)** -->

<!-- ### Results
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

The full table of results for both subtasks is provided [here](https://docs.google.com/spreadsheets/d/1HKM-bOu_SG-vlwdhIbl4WJ9baSRqZWiskoH3rT77Oio/edit?usp=sharing), alongside the calculation of rankings. -->
<!-- 
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

followed by a desciptive title of the proposed system system. Papers should be submitted in non-anonymised format (i.e., with author names included). -->


<!-- **References** - We ask participants to ensure the following citations are included in their system papers:

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
``` -->

<!-- **Reviewer Nomination** - Similar to other shared task campaigns (e.g. SemEval), we are requiring that at least one author per paper also acts as a reviewer for our shared task papers. Please nominate the reviewer from your submission using [this form](https://forms.gle/9KjqeoGrn9ZnU7gY7). If you do not nominate a reviewer, the corresponding author(s) will be automatically selected. -->

### Organizers
{: #us}

- Tomas Goldsack, University of Sheffield.
- Matthew Shardlow, Manchester Metropolitan University.
- Carolina Scarton, University of Sheffield.
- Sophia Ananiadou, Turing Fellow, Director of the National Centre for Text Mining and Deputy Director of the Institute of Data Science and AI at the University of Manchester.
- Chenghua Lin, Deputy Director of Research and Innovation in the Computer Science Department, University of Sheffield.


### References
{: #refs}

[1] Tomas Goldsack, Zheheng Luo, Qianqian Xie, Carolina Scarton, Chenghua Lin. 2023. [Overview of the BioLaySumm 2023 Shared Task on Lay Summarization of Biomedical Research Articles.]((https://aclanthology.org/2023.bionlp-1.44))
In The 22nd Workshop on Biomedical Natural Language Processing and BioNLP Shared Tasks, pages 468–477, Toronto, Canada. Association for Computational Linguistics.

[2] Tomas Goldsack, Zhihao Zhang, Chenghua Lin, Carolina Scarton. 2022. [Making Science Simple: Corpora for the Lay Summarisation of Scientific Literature.](https://aclanthology.org/2022.emnlp-main.724/)
In *Proceedings of the 2022 Conference on Empirical Methods in Natural Language Processing, pages 10589–10604, Abu Dhabi, United Arab Emirates. Association for Computational Linguistics.*

[3] Tomas Goldsack, Zhihao Zhang, Chen Tang, Carolina Scarton, and Chenghua Lin. 2023. [Enhancing Biomedical Lay Summarisation with External Knowledge Graphs.](https://aclanthology.org/2023.emnlp-main.498/)
In *Proceedings of the 2023 Conference on Empirical Methods in Natural Language Processing, pages 8016–8032, Singapore. Association for Computational Linguistics.*

[4] Oisín Turbitt, Robert Bevan, and Mouhamad Aboshokor. 2023. [MDC at BioLaySumm Task 1: Evaluating GPT Models for Biomedical Lay Summarization.](https://aclanthology.org/2023.bionlp-1.65/) In *The 22nd Workshop on Biomedical Natural Language Processing and BioNLP Shared Tasks, pages 611–619, Toronto, Canada. Association for Computational Linguistics.*

[5] Mong Yuan Sim, Xiang Dai, Maciej Rybinski, and Sarvnaz Karimi. 2023. [CSIRO Data61 Team at BioLaySumm Task 1: Lay Summarisation of Biomedical Research Articles Using Generative Models.](https://aclanthology.org/2023.bionlp-1.68/) In *The 22nd Workshop on Biomedical Natural Language Processing and BioNLP Shared Tasks, pages 629–635, Toronto, Canada. Association for Computational Linguistics.*