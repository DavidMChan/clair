# CLAIR: A (Surprisingly) simple semantic text metric leveraging large language models.

### [Project](https://davidmchan.github.io/clair/) | [Paper](https://davidmchan.github.io/clair/static/pdfs/_EMNLP_2023__CLAIR__Language_Models_for_Caption_Evaluation.pdf) <br>

Official implementation of the paper: "CLAIR: Evaluating Image Captions with Large Language Models".

The evaluation of machine-generated image captions poses an interesting yet persistent challenge. Effective evaluation measures must consider numerous dimensions of similarity, including semantic relevance, visual structure, object interactions, caption diversity, and specificity. Existing highly-engineered measures attempt to capture specific aspects, but fall short in providing a holistic score that aligns closely with human judgments. Here, we propose CLAIR, a novel method that leverages the zero-shot language modeling capabilities of large language models (LLMs) to evaluate candidate captions. In our evaluations, CLAIR demonstrates a stronger correlation with human judgments of caption quality compared to existing measures. Notably, on Flickr8K-Expert, CLAIR achieves relative correlation improvements over SPICE of 39.6% and over image-augmented methods such as RefCLIP-S of 18.3%. Moreover, CLAIR provides noisily interpretable results by allowing the language model to identify the underlying reasoning behind its assigned score.

## Getting started

### Setup

```bash
pip install git+https://github.com/DavidMChan/clair.git
```

### Usage

```python
import os
from clair import clair

os.environ['OPENAI_API_KEY'] = 'YOUR_API_KEY'

candidates = ['A photo of a cat sitting on a couch', 'A cat sitting on a couch']
references = ['A cat sitting on a couch', 'A cat is sitting on a couch', 'A cat is sitting on a sofa']

clair_score = clair(candidates, references, model='chat-gpt')

print(clair_score)
```

### Models

CLAIR relies on the [Grazier](https://github.com/DavidMChan/grazier) library to inteface with large language models. The following models are currently supported (see the linked repository for more information on configuring each model):

From OpenAI:

-   GPT-4 (Base, 32K) (Chat and Completion Engines)
-   GPT-3.5 (ChatGPT) (Chat and Completion Engines)
-   GPT-3 (Davinci (v2,v3), Ada, Babbage, Curie) (Completion Engine)

From Anthropic:

-   Claude 2 (Base) (Chat and Completion Engines)
-   Claude (Base, 100K) (Chat and Completion Engines)
-   Claude Instant (Base, 100K) (Chat and Completion Engines)

From Google/GCP:

-   PaLM (Chat and Completion Engines)

From Huggingface

-   GPT-2 (Base, Medium, Large, XL) (Completion Engine)
-   GPT-Neo (125M, 1.3B, 2.7B) (Completion Engine)
-   GPT-J (6B) (Completion Engine)
-   Falcon (7B, 40B, rw-1B, rw-7B) (Completion Engine)
-   Dolly (v1 - 6B, v2 - 3B, 7B, 12B) (Chat and Completion Engines)
-   MPT (Instruct - 7B, 30B) (Chat and Completion Engines)

From Facebook (via Huggingface)

-   Llama (7B, 13B, 30B, 65B) (Completion Engine)
-   Llama 2 (7B, 13B, 70B) (Completion Engine)
-   OPT (125M, 350M, 1.3B, 2.7B, 6.7B, 13B, 30B, 66B) (Completion Engine)

From Stanford (via Huggingface)

-   Alpaca (7B) (Chat and Completion Engines)

From Berkeley (via Huggingface)

-   Koala (7B, 13B_v1, 13B_v2) (Chat and Completion Engines)
-   Vicuna (7B, 13B) (Chat and Completion Engines)

From StabilityAI (via Huggingface)

-   StableLM (7B, 13B) (Chat and Completion Engines)

From AllenAI (via Huggingface)

-   Tulu (7B, 13B, 30B, 65B) (Chat and Completion Engines)
-   Open Instruct (ShareGPT) (7B, 13B, 30B, 65B) (Chat and Completion Engines)

From AI21

-   Jurassic 2 (Light, Mid, Ultra) (Completion Engines)

## Citation

If you find this repository useful, please cite our paper:

```bibtex
@inproceedings{chan-etal-2023-clair-evaluating,
    title = "CLAIR: Evaluating Image Captions with Large Language Models",
    author = "Chan, David M and
        Petryk, Suzanne and
        Gonzalez, Joseph E and
        Darrell, Trevor and
        Canny, John",
    booktitle = "Proceedings of the 2023 Conference on Empirical Methods in Natural Language Processing",
    month = dec,
    year = "2023",
    address = "Singapore, Singapore",
    publisher = "Association for Computational Linguistics",
}
```
