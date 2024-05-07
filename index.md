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

Biomedical publications contain the latest research on prominent health-related topics, ranging from common illnesses to global pandemics. This can often result in their content being of interest to a wide variety of audiences including researchers, medical professionals, journalists, and even members of the public. However, the highly technical and specialist language used within such articles typically makes it difficult for non-expert audiences to understand their contents.

<!-- Abstractive summarization can be used to generate a concise summary of an article, capturing its salient point using words and sentences that aren’t used in the original text. As such, these models have the potential to help broaden access to highly technical documents when trained to generate summaries that are more readable, containing more background information and less technical terminology (i.e., a "lay summary"). -->

The BioLaySumm shared task surrounds the abstractive summarization of biomedical articles, with an emphasis on catering to non-expert audiences through the generation of summaries that are more readable, containing more background information and less technical terminology (i.e., a "lay summary").

This is the 2nd iteration of BioLaySumm, following the success of the [1st edition](/2023) of the task at BioNLP 2023 [1] which attracted 56 submissions across 20 different teams. In this edition, which is to be hosted by the [BioNLP workshop](https://aclweb.org/aclwiki/BioNLP_Workshop) at ACL 2024, we aim to build on last year's task by introducing a new test set, updating our evaluation protocol, and encouraging participants to explore novel approaches that will help to further advance the state-of-the-art for Lay Summarization.  Accordingly, we will not only be offering a prize of £100 to the team with the top-ranking submission, but we will also offer a second prize of £50 to the team that propose the most innovative approach (as decided upon by the task organisers).
For inspiration, we provide some ideas of promising research directions [below](#prom).

### Updates
{: #news}
- **February 23rd, 2024** - The evaluation scripts have now been released for participants on GitHub ([link](https://github.com/TGoldsack1/BioLaySumm2024-evaluation_scripts)).
- **March 25th, 2024** - A worked example of the evaluation protocol has been provided [here](https://docs.google.com/spreadsheets/d/1hQB_w16lfIGeggkCwIbdBH9jyLhDnK-R31ZWT0iCkVE/edit?usp=sharing).
- **April 25th, 2024** - Details of the system paper submission process have been added [below](#sys).
- **May 7th, 2024** - The system submission deadline has now passed and the final competition [results](#res) have been calculated and added to the site.


### Important Dates
{: #dates}

- **First call for participation:** 22nd January, 2024
- **Releasing of task data (training, validation, and test):** 22nd January, 2024
- **System submission deadline:** May 6th, 2024
- **System papers due date:** May 20th, 2024
- **Notification of acceptance:** June 17th, 2024
- **Camera-ready system papers due:** July 1st, 2024
- **BioNLP Workshop Date:** August 16th, 2024

Note that all deadlines are 23:59:59 AoE (UTC-12).

Join our [Google Group](https://groups.google.com/g/biolaysumm2024) for updates and discussion on the shared task! If you have any questions, please ask in the [Google Group](https://groups.google.com/g/biolaysumm2024) or [email](mailto:tgoldsack1@sheffield.ac.uk) us.

### Registration and Submission
{: #reg}

<!-- **CodaBench page**: [https://CodaBench.lisn.upsaclay.fr/competitions/12125](https://CodaBench.lisn.upsaclay.fr/competitions/12125) -->
**CodaBench page**: [https://www.codabench.org/competitions/1920/](https://www.codabench.org/competitions/1920/)


### Task Definition: Lay Summarization
{: #task}
 
Given an article's abstract and main text as input, the goal is for participants to train a model (or models) to generate the lay summary. Two separate datasets (derived from biomedical journals, PLOS and eLife) are provided for model training and will be used for evaluation. For the final evaluation, submissions will be ranked on the average performance across both datasets.

Note that submissions can be generated from either 2 separate summarization models (i.e., one trained on each dataset) or a single unified model (i.e., trained on both datasets). Participants will be required to indicate which approach was taken for each submission.

### Datasets
{: #data}
The data that will be used for the task is based on the PLOS and eLife datasets, published in [2]. Each dataset consists of biomedical research articles ( including their technical abstracts) and their expert-written lay summaries. The lay summaries of each dataset also exhibit numerous notable differences in their characteristics - for more details, please refer to [2].

PLOS is the larger of the two datasets, containing 24,773 instances for training and 1,376 for validation. eLife contains 4,346 instances for training and 241 for validation.

The test data is composed of 142 PLOS article and 142 eLife articles. **Note: These test splits are different to those published in [2] and used for the 1st edition of BioLaySumm [1].**  

All task data is provided via the competition CodaBench page under the "Files" tab.

### Evaluation
{: #eval}

<!-- Our evaluation will assess the quality of generated summaries along **3** dimensions: **(a)** Relevance, **(b)** Readability, and **(c)** Factuality. More information on this coming soon. -->
For both subtasks, we will evaluate generated summaries across three aspects: Relevance, Readability, and Factuality. Each evaluation aspect will be composed of multiple automatic metrics:

- **Relevance** - ROUGE (1, 2, and L) and BERTScore
- **Readability** - Flesch-Kincaid Grade Level (FKGL) and Dale-Chall Readability Score (DCRS), Coleman-Liau Index (CLI), and LENS
- **Factuality** - AlignScore, SummaC

The scores presented for each metric will be the average of those calculated independently for the generated lay summaries of PLOS and eLife. The aim is to maximize the scores for Relevance metrics, Factuality metrics, and the LENS (Readability) metric and minimize scores for all other Readability metrics.

We will rank submissions based on each of these evaluation aspects independently. This will be done *after the test phase has ended* by applying min-max normalization to the scores of each metric, before averaging across metrics within each evaluation aspect. A ranking for each evaluation aspect will be computed as well as an overall ranking, which will be based on the best average score across all three aspects.

The evaluation scripts (configured for use on the validation splot) can be found [here](https://github.com/TGoldsack1/BioLaySumm2024-evaluation_scripts).

A worked example of the described process is provided [here](https://docs.google.com/spreadsheets/d/1hQB_w16lfIGeggkCwIbdBH9jyLhDnK-R31ZWT0iCkVE/edit?usp=sharing).

### Promising Research Directions
{: #prom}

- **Retrieval-Augmented Generation (RAG)** - Recent work has shown that the incorperation of external knowledge derived from graphs can help to improve the quality of generated summaries [3]. The automatic identification and retrieval of relevant textual knowledge is likely to provide similar benefits, and we encourage participants to explore this direction.

- **Controllable Lay Summarisation** - The lay summaries of PLOS and eLife exhibit numerous notable differences in their characteristics, including their length, readability, and abstractivness [2]. We encourage participants to explore the use of controllable generation techniques to produce summaries that are tailored to the characteristics of each dataset and enable models to cater to the needs of different audiences (e.g., [6]).

- **LLMs for Data Augmentation** - In the first edition of BioLaySumm [1], we found that the use of large language models (LLMs) proved benefitial for summary generation [4], but also for data augmentation [5]. We encourage participants to explore this direction further, and to consider potential new ways to use use LLMs for both summary generation and data augmentation.


### Results
{: #res}

The teams with top three ranking submissions (overall, and for each criteria), as determined by the evaluation proceedure described in the [evaluation section](#eval), are given below:

| **Criterion** | **1st**                  | **2nd**                          | **3rd**                          |
| :---          |           :----:         |                :---:             |              :----:              |
| Relevance     | UIUC_BioNLP (*shruthan*) | *Saama Technologies* (*hwanmun*) | Ctyun AI (*mandy*)               |
| Readability   | YXZ (*yecheng*)          | NLPSucks (*aryan16*)             | jimmyapples (*etherinmatic*)     |
| Factuality    | eulerian (*eulerian123*) | MKGS(*kartiknlp*)                | sanika (*sanika*)                | 
| **Overall**   | UIUC_BioNLP (*shruthan*) | Ctyun AI (*mandy*)               | *Saama Technologies* (*hwanmun*) |

The full table of results for is provided [here](https://docs.google.com/spreadsheets/d/1BziwQ9Z7_N4V6qqkSzDFX3NEivG39ucXZGbcubG2xWQ/edit?usp=sharing), alongside the calculation of rankings.


### System Paper Submission
{: #sys}

All participating teams are invited to submit system papers that, pending review, will be published as part of the BioNLP Workshop proceedings.

**Submission** - Participants can submit a system paper at following SoftConf link (track "ST_2") anytime before the deadline on 20/05/2024 (23:59:59, Anywhere on Earth timezone):
[https://softconf.com/acl2024/BioNLP2024-ST/](https://softconf.com/acl2024/BioNLP2024-ST/)


**Format** - System papers should follow the ACL 2024 short paper format (i.e., 4 pages, with unlimited pages for appendices and references), as described on the [call for papers](https://2024.aclweb.org/calls/main_conference_papers/#paper-submission-details). The Overleaf template for this can be found [here](https://www.overleaf.com/latex/templates/association-for-computational-linguistics-acl-conference/jvxskxpnznfj).

Paper titles should adopt the format: "{TEAM_NAME} at BioLaySumm:" followed by a descriptive title of the proposed approach. Papers should be submitted in non-anonymised format (i.e., with author names included).

**References** - We ask participants to ensure the following citations are included in their system papers:

- *BioLaySumm 2024 Overview Paper* - the following citation should be used when referring to the shared task in general (note, this is a temporary example that may be subject to change in the future):
```
@inproceedings{goldsack-etal-2024-biolaysumm,
    title = "Overview of the BioLaySumm 2024 Shared Task on the Lay Summarization of Biomedical Research Articles",
    author = "Goldsack, Tomas  and
      Scarton, Carolina  and
      Shardlow, Matthew  and
      Lin, Chenghua",
    booktitle = "The 23rd Workshop on Biomedical Natural Language Processing and BioNLP Shared Tasks",
    month = aug,
    year = "2024",
    address = "Bangkok, Thailand",
    publisher = "Association for Computational Linguistics",
}
```

Participants may also want to include last year's overview paper when referring to the shared task:
```
@inproceedings{goldsack-etal-2023-biolaysumm,
    title = "Overview of the BioLaySumm 2023 Shared Task on Lay Summarization of Biomedical Research Articles",
    author = "Goldsack, Tomas  and
      Luo, Zheheng  and
      Xie, Qianqian  and
      Scarton, Carolina  and
      Shardlow, Matthew  and
      Ananiadou, Sophia  and
      Lin, Chenghua",
    booktitle = "The 22nd Workshop on Biomedical Natural Language Processing and BioNLP Shared Tasks",
    month = jul,
    year = "2023",
    address = "Toronto, Canada",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2023.bionlp-1.44",
    doi = "10.18653/v1/2023.bionlp-1.44",
    pages = "468--477",
}
```

- *Task datasets* - the following citation should be used when referring to the task datasets:
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
    pages = "10589--10604",
}
```

**Reviewer Nomination** - Similar to other shared task campaigns (e.g. SemEval), we are requiring that at least one author per paper also acts as a reviewer for our shared task papers. Please nominate the reviewer from your submission using [this form](https://forms.gle/nbwTKeaVZvVSC9MU8). If you do not nominate a reviewer, the corresponding author(s) will be automatically selected.

### Organizers
{: #us}

- Tomas Goldsack, University of Sheffield.
- Matthew Shardlow, Manchester Metropolitan University.
- Carolina Scarton, University of Sheffield.
- Chenghua Lin, University of Manchester.


### References
{: #refs}

[1] Tomas Goldsack, Zheheng Luo, Qianqian Xie, Carolina Scarton, Sophia Ananiadou, Chenghua Lin. 2023. [Overview of the BioLaySumm 2023 Shared Task on Lay Summarization of Biomedical Research Articles.](https://aclanthology.org/2023.bionlp-1.44)
In The 22nd Workshop on Biomedical Natural Language Processing and BioNLP Shared Tasks, pages 468–477, Toronto, Canada. Association for Computational Linguistics.

[2] Tomas Goldsack, Zhihao Zhang, Chenghua Lin, Carolina Scarton. 2022. [Making Science Simple: Corpora for the Lay Summarisation of Scientific Literature.](https://aclanthology.org/2022.emnlp-main.724/)
In *Proceedings of the 2022 Conference on Empirical Methods in Natural Language Processing, pages 10589–10604, Abu Dhabi, United Arab Emirates. Association for Computational Linguistics.*

[3] Tomas Goldsack, Zhihao Zhang, Chen Tang, Carolina Scarton, and Chenghua Lin. 2023. [Enhancing Biomedical Lay Summarisation with External Knowledge Graphs.](https://aclanthology.org/2023.emnlp-main.498/)
In *Proceedings of the 2023 Conference on Empirical Methods in Natural Language Processing, pages 8016–8032, Singapore. Association for Computational Linguistics.*

[4] Oisín Turbitt, Robert Bevan, and Mouhamad Aboshokor. 2023. [MDC at BioLaySumm Task 1: Evaluating GPT Models for Biomedical Lay Summarization.](https://aclanthology.org/2023.bionlp-1.65/) In *The 22nd Workshop on Biomedical Natural Language Processing and BioNLP Shared Tasks, pages 611–619, Toronto, Canada. Association for Computational Linguistics.*

[5] Mong Yuan Sim, Xiang Dai, Maciej Rybinski, and Sarvnaz Karimi. 2023. [CSIRO Data61 Team at BioLaySumm Task 1: Lay Summarisation of Biomedical Research Articles Using Generative Models.](https://aclanthology.org/2023.bionlp-1.68/) In *The 22nd Workshop on Biomedical Natural Language Processing and BioNLP Shared Tasks, pages 629–635, Toronto, Canada. Association for Computational Linguistics.*

[6] Zheheng Luo, Qianqian Xie, and Sophia Ananiadou. 2022. [Readability Controllable Biomedical Document Summarization.](https://aclanthology.org/2022.findings-emnlp.343/) In *Findings of the Association for Computational Linguistics: EMNLP 2022, pages 4667–4680, Abu Dhabi, United Arab Emirates. Association for Computational Linguistics.*