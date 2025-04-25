---
title: BioLaySumm
# feature_image: "https://media.istockphoto.com/id/1254001828/vector/green-simple-pastel-soft-color-for-background-green-plain-color-for-wallpaper-green-pastel.jpg?s=612x612&w=0&k=20&c=9DlnNxAnSQUhcBUmnMpL4gOVAxC7spbhdd2dOOaW6Zg="
# feature_image: "https://i.postimg.cc/tTtgwdYq/DALL-E-2025-01-10-12-32-19-Extend-the-background-of-the-image4.jpg"
# feature_image: "https://i.postimg.cc/bwHwVHMm/image1.webp"
feature_image: "https://i.postimg.cc/mD23gyKD/DALL-E-2025-01-10-12-32-19-Extend-the-background-of-the-image3.jpg"
feature_text: |
  # BioLaySumm 2025
  ##### Shared Task: Lay Summarization of Biomedical Research Articles and Radiology Reports @ BioNLP Workshop, ACL 2025
---

### Introduction
{: #intro}

Biomedical publications contain the latest research on prominent health-related topics, ranging from common illnesses to global pandemics. This can often result in their content being of interest to a wide variety of audiences including researchers, medical professionals, journalists, and even members of the public. However, the highly technical and specialist language used within such articles typically makes it difficult for non-expert audiences to understand their contents.

<!-- Abstractive summarization can be used to generate a concise summary of an article, capturing its salient point using words and sentences that aren’t used in the original text. As such, these models have the potential to help broaden access to highly technical documents when trained to generate summaries that are more readable, containing more background information and less technical terminology (i.e., a "lay summary"). -->

The BioLaySumm shared task surrounds the abstractive summarization of biomedical articles, with an emphasis on catering to non-expert audiences through the generation of summaries that are more readable, containing more background information and less technical terminology (i.e., a "lay summary").

This is the 3nd iteration of BioLaySumm, following the success of the [2nd edition](/2024) of the task at BioNLP 2024 [1] which attracted **200 plus** submissions across **53** different teams and the [1st edition](/2023) of the task at BioNLP 2023 [2] which attracted 56 submissions across 20 different teams. In this edition, which is to be hosted by the [BioNLP workshop](https://aclweb.org/aclwiki/BioNLP_Workshop) at ACL 2025, we aim to build on last year's task by introducing a new task: radiology report generation with layman’s terms, extending the shared task to a new domain and multi-modality. Additionally, we update our evaluation protocol, and encourage participants to explore unified approaches to tackle both the text-only task and the multi-modal task, which help further advance the state-of-the-art for Lay Summarization.


<!-- ### Updates
{: #news}
- **February 23rd, 2025** - The evaluation scripts have now been released for participants on GitHub ([link](https://github.com/TGoldsack1/BioLaySumm2025-evaluation_scripts)).
- **March 25th, 2025** - A worked example of the evaluation protocol has been provided [here](https://docs.google.com/spreadsheets/d/1hQB_w16lfIGeggkCwIbdBH9jyLhDnK-R31ZWT0iCkVE/edit?usp=sharing).
- **April 25th, 2025** - Details of the system paper submission process have been added [below](#sys).
- **May 7th, 2025** - The system submission deadline has now passed and the final competition [results](#res) have been calculated and added to the site.
- **May 13th, 2025** - The test set reference data has been made publically available via [this repository](https://github.com/TGoldsack1/Corpora_for_Lay_Summarisation). -->


### Important Dates
{: #dates}

- **First call for participation:**  February 21st, 2025
- **Releasing of task data (training, validation, and test):** February 21st, 2025
- **System submission deadline:** May 15th, 2025
- **System papers due date:** May 22th, 2025
- **Notification of acceptance:** May 26th, 2025
- **Camera-ready system papers due:** May 30th, 2025
- **BioNLP Workshop Date:** July 31 - August 1, 2025

Note that all deadlines are 23:59:59 AoE (UTC-12).

Join our Google Group -- [Biolaysumm2025](https://groups.google.com/g/laysumm) for updates and discussion on the shared task! 
<!-- If you have any questions, please ask in the [Google Group](https://groups.google.com/g/biolaysumm2025) or [email](mailto:tgoldsack1@sheffield.ac.uk) us. -->

### Registration and Submission
{: #reg} 

**CodaBench page**: [https://www.codabench.org/competitions/7351](https://www.codabench.org/competitions/7351) 
<!-- **CodaBench page**: [https://www.codabench.org/competitions/1920/](https://www.codabench.org/competitions/1920/) -->


### Task Definition
{: #task}

**Task 1: Lay Summarization**


**Subtask 1.1: Plain Lay Summarization**

Given an article's abstract and main text as input, the goal is for participants to train a model (or models) to generate the lay summary. Two separate datasets (derived from biomedical journals, PLOS and eLife) are provided for model training and will be used for evaluation. For the final evaluation, submissions will be ranked on the average performance across both datasets.

Note that submissions can be generated from either 2 separate summarization models (i.e., one trained on each dataset) or a single unified model (i.e., trained on both datasets). Participants will be required to indicate which approach was taken for each submission.

**Subtask 1.2: Lay Summarisation with External Knowledge**

Due to differences in the intended audience, the source article may not always contain all the information required by a lay audience (e.g., background information needed for understanding the topic, concept definitions, etc.). This knowledge gap can be filled through the introduction of relevant external information.

This substask is the constrained version of Task 1.1, and follows an identical setup, except that participants will be required to make use of external knowledge in some capacity. For example, participants could perform manual data augmentation or Retrieval-Augmented Generation (RAG). 
Participants will be required to indicate which approach was taken(i.e., online or offline) for each submission.

**Task 2: Radiology Report Generation with Layman’s Terms**

**Subtask 2.1: Radiology Report Translation**

The goal of this subtask is to build models to translate professional reports to layman’s terms. This has validated advantages that will bring real-world impacts, e.g., improving patient understanding. This will also allow participants that have no intention to participate in our multi-modal setting to contribute to the field of Radiology Report Generation(RRG).

Participants would be asked to submit summaries generated by the trained model. Also, we will be able to provide professional report-layman’s terms pairs from datasets(two settings: Open-i, PadChest, BIMCV-COVID19, with or without MIMIC-CXR).


**Subtask 2.2: Multi-modal Radiology Report Translation**

The participants are expected to train an end-to-end image-to-text model, e.g., an MLLM, to facilitate this task. 

Two settings are provided, three datasets training and four datasets training. Submissions under these two settings will be evaluated differently, although we would encourage participants to gain access to MIMIC-CXR dataset to push the boundary of the performance. 

<!-- We further allow and encourage participants to train on the concatenation of Task 1 and task 2 datasets to achieve better results in Subtask 2.2, since this is possible with MLLMs which can take in image-only, text-only inputs, or both. We believe training on both can provide good transferability of knowledge across both setups. -->

**Note: We're excited to have you join us! You can choose to take on one subtask or multiple — it's entirely up to you!**

### Datasets
{: #data}

**For Task 1: Lay Summarisation**

The data that will be used for this task is based on the [PLOS](https://journals.plos.org/plosone/s/data-availability) and [eLife](https://elifesciences.org/), published in [3]. Each dataset consists of biomedical research articles (including their technical abstracts) and their expert-written lay summaries. The lay summaries of each dataset also exhibit numerous notable differences in their characteristics - for more details, please refer to [3].

PLOS is the larger of the two datasets, containing 24,773 instances for training and 1,376 for validation. eLife contains 4,346 instances for training and 241 for validation. The datasets can be downloaded in [BioLaySumm2025-PLOS](https://huggingface.co/datasets/BioLaySumm/BioLaySumm2025-PLOS) and [BioLaySumm2025-eLife](https://huggingface.co/datasets/BioLaySumm/BioLaySumm2025-eLife).

<!-- The test data is composed of 142 PLOS article and 142 eLife articles. **Note: These test splits are different to those published in [3] and used for the 1st edition of BioLaySumm [2].** -->


**For Task 2: Radiology Report Generation with Layman’s Terms**

Four layman’s terms datasets ([PadChest](https://bimcv.cipf.es/bimcv-projects/padchest/), [BIMCV-COVID19](https://bimcv.cipf.es/bimcv-projects/bimcv-covid19/)([its github](https://github.com/BIMCV-CSUSP/BIMCV-COVID-19)), [Open-i](https://openi.nlm.nih.gov/faq#collection) and [MIMIC-CXR](https://physionet.org/content/mimic-cxr-jpg/2.1.0/)）will be provided for model training and used for evaluation. We will mainly base on non-MIMIC’s images because participants can easily access. We allow the use of MIMIC-CXR data to provide better results, and submissions that are trained on three datasets and four datasets will be evaluated separately. The dataset can be downloaded in [BioLaySumm2025-LaymanRRG-opensource-track](https://huggingface.co/datasets/BioLaySumm/BioLaySumm2025-LaymanRRG-opensource-track) and [BioLaySumm2025-LaymanRRG-closesource-track](https://huggingface.co/datasets/BioLaySumm/LaymanRRG-closesource-track).



<!-- All task data is provided via the competition CodaBench page under the "Files" tab. -->

<!-- #### Test set reference data
Now that the competition has concluded, we have made the test data (including reference lay summaries) publically available to enable further research on the task of Lay Summarization. It can be accessed via [this repository](https://github.com/TGoldsack1/Corpora_for_Lay_Summarisation). -->

### Evaluation
{: #eval}

<!-- Our evaluation will assess the quality of generated summaries along **3** dimensions: **(a)** Relevance, **(b)** Readability, and **(c)** Factuality. More information on this coming soon. -->
An automatic evaluation will be conducted automatically upon submission of test set predictions using CodaLab.  After the test phase is complete, we will perform a manual system ranking process that involves normalising and averaging metric scores.

**Automatic Metrics**

**Automatic Metrics**

evaluation aspect will be composed of one or more automatic metrics:

- **Relevance** - ROUGE (1, 2, and L), BLEU, METEOR, BERTScore
- **Readability** - Flesch-Kincaid Grade Level (FKGL) and Dale-Chall Readability Score (DCRS), Coleman-Liau Index (CLI), and LENS
- **Factuality** - AlignScore, SummaC

For Task 2, we will evaluate generated summaries across three aspects: Relevance,  Readability, Clinical. Each evaluation aspect will be composed of one or more automatic metrics:

- **Relevance** - ROUGE (1, 2, and L), BLEU, METEOR, BERTScore, semantics scores
- **Readability** - Flesch-Kincaid Grade Level (FKGL) and Dale-Chall Readability Score (DCRS), Coleman-Liau Index (CLI)
- **Clinical metrics** - CheXbert-F1, RadGraph-F1


<!-- The scores presented for each metric will be the average of those calculated independently for every subtask. The aim is to maximize the scores for Relevance metrics, Factuality metrics, Clinical metrics, LLMs-based metrics and the LENS (Readability) metric and minimize scores for all other Readability metrics. -->

**System Ranking**

We will rank submissions based on each of these evaluation aspects independently. This will be done *after the test phase has ended* by applying min-max normalization to the scores of each metric, before averaging across metrics within each evaluation aspect. A ranking for each evaluation aspect will be computed as well as an overall ranking, which will be based on the best average score across all related aspects.

<!-- The evaluation scripts (configured for use on the validation splot) can be found [here](https://github.com/TGoldsack1/BioLaySumm2025-evaluation_scripts). -->

<!-- A worked example of the described process is provided [here](https://docs.google.com/spreadsheets/d/1hQB_w16lfIGeggkCwIbdBH9jyLhDnK-R31ZWT0iCkVE/edit?usp=sharing). -->

**Baseline**

For text-only tasks(Task 1 and Subtask 2.1), llama3 8B/Qwen2.5 7B will be used as the primary baseline. 

For multimodal task(Subtask 2.2), we will use finetuned LlaVA as the finetuned baseline, and a stronger model (e.g, Qwen-VL 72B) as the off-the-shelf baseline.


### Promising Research Directions
{: #prom}

- **Retrieval-Augmented Generation (RAG)** - Recent work has shown that the incorperation of external knowledge derived from graphs can help to improve the quality of generated summaries [4]. The automatic identification and retrieval of relevant textual knowledge is likely to provide similar benefits, and we encourage participants to explore this direction.

- **Controllable Lay Summarisation** - The lay summaries of PLOS and eLife exhibit numerous notable differences in their characteristics, including their length, readability, and abstractivness [3]. We encourage participants to explore the use of controllable generation techniques to produce summaries that are tailored to the characteristics of each dataset and enable models to cater to the needs of different audiences (e.g., [7]).

- **LLMs for Data Augmentation** - In the first edition of BioLaySumm [2], we found that the use of large language models (LLMs) proved benefitial for summary generation [5], but also for data augmentation [6]. We encourage participants to explore this direction further, and to consider potential new ways to use use LLMs for both summary generation and data augmentation.


<!-- ### Results
{: #res}

The teams with top three ranking submissions (overall, and for each evaluation aspect), as determined by the evaluation proceedure described in the [evaluation section](#eval), are given below:

***

| **Aspect**    | **1st**                  | **2nd**                          | **3rd**                          |
| :---          |           :----:         |                :---:             |              :----:              |
| Relevance     | UIUC_BioNLP (*shruthan*) | *Saama Technologies* (*hwanmun*) | Ctyun AI (*mandy*)               |
| Readability   | YXZ (*yecheng*)          | NLPSucks (*aryan16*)             | jimmyapples (*etherinmatic*)     |
| Factuality    | eulerian (*eulerian123*) | MKGS(*kartiknlp*)                | sanika (*sanika*)                | 
| **Overall**   | UIUC_BioNLP (*shruthan*) | Ctyun AI (*mandy*)               | *Saama Technologies* (*hwanmun*) |

***


The full table of results is provided [here](https://docs.google.com/spreadsheets/d/1BziwQ9Z7_N4V6qqkSzDFX3NEivG39ucXZGbcubG2xWQ/edit?usp=sharing), alongside the calculation of rankings. -->


### System Paper Submission
{: #sys}

All participating teams are invited to submit system papers that, pending review, will be published as part of the BioNLP Workshop proceedings.

**Submission** - Participants can submit a system paper at following SoftConf link (track "ST_2") anytime before the deadline on 20/05/2025 (23:59:59, Anywhere on Earth timezone):
[https://softconf.com/acl2025/BioNLP2025-ST/](https://softconf.com/acl2025/BioNLP2025-ST/)


**Format** - System papers should follow the ACL 2025 short paper format (i.e., 4 pages, with unlimited pages for appendices and references), as described on the [call for papers](https://2025.aclweb.org/calls/main_conference_papers/#paper-submission-details). The Overleaf template for this can be found [here](https://www.overleaf.com/latex/templates/association-for-computational-linguistics-acl-conference/jvxskxpnznfj).

Paper titles should adopt the format: "{TEAM_NAME} at BioLaySumm:" followed by a descriptive title of the proposed approach. Papers should be submitted in non-anonymised format (i.e., with author names included).

**References** - We ask participants to ensure the following citations are included in their system papers:

- *BioLaySumm 2025 Overview Paper* - the following citation should be used when referring to the shared task in general (note, this is a temporary example that may be subject to change in the future):
```
@inproceedings{goldsack-etal-2025-biolaysumm,
    title = "Overview of the BioLaySumm 2025 Shared Task on the Lay Summarization of Biomedical Research Articles",
    author = "Goldsack, Tomas and Lin, Chenghua",
    booktitle = "The 24rd Workshop on Biomedical Natural Language Processing and BioNLP Shared Tasks",
    month = aug,
    year = "2025",
    address = "Vienna, Austria",
    publisher = "Association for Computational Linguistics",
}
```

Participants may also want to include last two years' overview paper when referring to the shared task:

```
@inproceedings{goldsack-etal-2024-overview,
    title = "Overview of the {B}io{L}ay{S}umm 2024 Shared Task on the Lay Summarization of Biomedical Research Articles",
    author = "Goldsack, Tomas  and
      Scarton, Carolina  and
      Shardlow, Matthew  and
      Lin, Chenghua",
    editor = "Demner-Fushman, Dina  and
      Ananiadou, Sophia  and
      Miwa, Makoto  and
      Roberts, Kirk  and
      Tsujii, Junichi",
    booktitle = "Proceedings of the 23rd Workshop on Biomedical Natural Language Processing",
    month = aug,
    year = "2024",
    address = "Bangkok, Thailand",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2024.bionlp-1.10/",
    doi = "10.18653/v1/2024.bionlp-1.10",
    pages = "122--131",
}
```

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
@article{zhao2024x,
  title={X-ray Made Simple: Radiology Report Generation and Evaluation with Layman's Terms},
  author={Zhao, Kun and Xiao, Chenghao and Tang, Chen and Yang, Bohao and Ye, Kai and Moubayed, Noura Al and Zhan, Liang and Lin, Chenghua},
  journal={arXiv preprint arXiv:2406.17911},
  year={2024}
}
```

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

- Kun Zhao, University of Pittsburgh
- Prof. Liang Zhan, University of Pittsburgh
- Chenghao Xiao, University of Durham
- Prof. Noura Al Moubayed, University of Durham
- Kejing Yin, Hong Kong Baptist University
- Sixing Yan, Hong Kong Baptist University
- Zijian Lei, Hong Kong Baptist University
- Prof. William CHEUNG, Hong Kong Baptist University
- Dr. Qianqian Xie, Yale University
- Zheheng Luo, University of Manchester
- Prof. Sophia Ananiadou, University of Manchester
- Tomas Goldsack, University of Sheffield
- Siwei Wu, University of Manchester
- Xiao Wang, University of Manchester
- Prof. Chenghua Lin, University of Manchester



### References
{: #refs}

[1] Tomas Goldsack, Carolina Scarton, Matthew Shardlow, and Chenghua Lin. 2024. [Overview of the BioLaySumm 2024 Shared Task on the Lay Summarization of Biomedical Research Articles.](https://aclanthology.org/2024.bionlp-1.10/) In *Proceedings of the 23rd Workshop on Biomedical Natural Language Processing, pages 122–131, Bangkok, Thailand. Association for Computational Linguistics.*

[2] Tomas Goldsack, Zheheng Luo, Qianqian Xie, Carolina Scarton, Sophia Ananiadou, Chenghua Lin. 2023. [Overview of the BioLaySumm 2023 Shared Task on Lay Summarization of Biomedical Research Articles.](https://aclanthology.org/2023.bionlp-1.44)
In The 22nd Workshop on Biomedical Natural Language Processing and BioNLP Shared Tasks, pages 468–477, Toronto, Canada. Association for Computational Linguistics.

[3] Tomas Goldsack, Zhihao Zhang, Chenghua Lin, Carolina Scarton. 2022. [Making Science Simple: Corpora for the Lay Summarisation of Scientific Literature.](https://aclanthology.org/2022.emnlp-main.724/)
In *Proceedings of the 2022 Conference on Empirical Methods in Natural Language Processing, pages 10589–10604, Abu Dhabi, United Arab Emirates. Association for Computational Linguistics.*

[4] Tomas Goldsack, Zhihao Zhang, Chen Tang, Carolina Scarton, and Chenghua Lin. 2023. [Enhancing Biomedical Lay Summarisation with External Knowledge Graphs.](https://aclanthology.org/2023.emnlp-main.498/)
In *Proceedings of the 2023 Conference on Empirical Methods in Natural Language Processing, pages 8016–8032, Singapore. Association for Computational Linguistics.*

[5] Oisín Turbitt, Robert Bevan, and Mouhamad Aboshokor. 2023. [MDC at BioLaySumm Task 1: Evaluating GPT Models for Biomedical Lay Summarization.](https://aclanthology.org/2023.bionlp-1.65/) In *The 22nd Workshop on Biomedical Natural Language Processing and BioNLP Shared Tasks, pages 611–619, Toronto, Canada. Association for Computational Linguistics.*

[6] Mong Yuan Sim, Xiang Dai, Maciej Rybinski, and Sarvnaz Karimi. 2023. [CSIRO Data61 Team at BioLaySumm Task 1: Lay Summarisation of Biomedical Research Articles Using Generative Models.](https://aclanthology.org/2023.bionlp-1.68/) In *The 22nd Workshop on Biomedical Natural Language Processing and BioNLP Shared Tasks, pages 629–635, Toronto, Canada. Association for Computational Linguistics.*

[7] Zheheng Luo, Qianqian Xie, and Sophia Ananiadou. 2022. [Readability Controllable Biomedical Document Summarization.](https://aclanthology.org/2022.findings-emnlp.343/) In *Findings of the Association for Computational Linguistics: EMNLP 2022, pages 4667–4680, Abu Dhabi, United Arab Emirates. Association for Computational Linguistics.*

[8]Zheheng Luo, Qianqian Xie, Sophia Ananiadou, [Factual consistency evaluation of summarization in the Era of large language models.](https://www.sciencedirect.com/science/article/pii/S0957417424013228) Expert Systems with Applications,Volume 254, 2024, 124456,https://doi.org/10.1016/j.eswa.2024.124456.
 
[9]Jennifer A. Bishop, Sophia Ananiadou, and Qianqian Xie. 2024. [LongDocFACTScore: Evaluating the Factuality of Long Document Abstractive Summarisation.](https://aclanthology.org/2024.lrec-main.941.pdf) In *Proceedings of the 2024 Joint International Conference on Computational Linguistics, Language Resources and Evaluation (LREC-COLING 2024), pages 10777–10789, Torino, Italia. ELRA and ICCL.*
