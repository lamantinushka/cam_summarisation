# CAM Summarisation

## Task description
Comparative Argumentative Machine is an algorithm for the object comparison. It extracts information about two objects and their differences from large database and provides score of each object as well as the supproting sentences and the aspects of the comparison. In this project we investigate different techniques to the summarization of the supporting sentences retrieved by CAM.

There are two main difficulties:
- CAM database is an CommonCrawl dump, so the CAM domain is wide. At the same time there are only 538 examples of CAM outputs, that can be a complication for the neural methods. 
- There are no reference summaries, which on the current stage allows only qualitative evaluation.

## Approaches
- MeanSum [[1]](https://arxiv.org/pdf/1810.05739.pdf)
[notebook](MeanSum.ipynb)

Is a seq2seq model learning iterations in the latent space. Summary is generated from the mean vector of the sentences representations.
- GPT-2 [[2]](https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf)
[notebook](GPT2.ipynb)

Is a self-attentive language model pretrained on the web-pages data. Its domain is similar to the CAM one, so it is possible to use GPT-2 both with and without finetuning. The diverse beam search [[3]](https://arxiv.org/pdf/1611.08562.pdf) is applied to support diversity among the generated summaries.

- BERT [[3]](https://arxiv.org/pdf/1810.04805.pdf)
[notebook](BERT.ipynb)

Is a transformer-based model for natural language understanding. It is pretrained for the masked language modelling task, so it is proposed to fill in the gaps in the sequences of form [OBJ1, GAP x n1, ASPECT, GAP x n2, OBJ2, GAP x n3]

- TextRank
[notebook](TextRank.ipynb)

Is a graph method exctracting sentences with the highest rank based on a similarity between sentences. Opposite to the methods mentioned before, TextRank does not generate new text but ranges the CAM supporting sentences. Different similarity functions are used as well as several modifications including graph pruning and weighted initialization [[4]](https://www.researchgate.net/publication/327136473_Graph-based_Text_Summarization_Using_Modified_TextRank) and nodes clusterization with Chinese Whispers Algorithm [[5]](https://pdfs.semanticscholar.org/c64b/9ed6a42b93a24316c7d1d6b3fddbd96dbaf5.pdf?_ga=2.39857698.1066197194.1576664117-825072152.1576664117)
