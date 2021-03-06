# COALAS 🐨
This repo contains the COrpus of AngLicisms in the SpAnish PresS (COALAS).

COALAS is a corpus of Spanish newswire annotated with unassimilated lexical borrowings. The corpus contains 370,000 tokens and includes various written media written in European Spanish. The test set was designed to be as difficult as possible: it covers sources and dates not seen in the training set, includes a high number of OOV words (92% of the borrowings in the test set are OOV) and is very borrowing-dense (20 borrowings per 1,000 tokens).

## Corpus splits
|Set      | Tokens | ENG  | OTHER |  Unique |
|:-------|-----:|-----:|---------:|---------:|
|Training |231,126 |1,493 | 28 |380 |
|Development |82,578 |306 |49 |316|
|Test |58,997 |1,239 |46 |987|
|**Total** |372,701 |3,038 |123 |1,683 |

## Annotation
The annotation considers two labels:  
* ``ENG``: For English lexical borrowings (*smartphone*, *online*, *podcast*)
* ``OTHER``: For lexical borrowings from any other language (*boutique*, *anime*, *umami*)

The model uses BIO encoding to account for multitoken borrowings.

## Models
There are two publicly-available models trained on this dataset for the task of automatic detection of anglicisms. Both are available in the HuggingFace model hub:
- [Flair BiLSTM model](https://huggingface.co/lirondos/anglicisms-spanish-flair-cs), fed with [codeswitch embeddings](https://huggingface.co/sagorsarker/codeswitch-spaeng-lid-lince) and subword embeddings, based on [Flair library](https://github.com/flairNLP/flair) (F1=85.76)
- [multilingual BERT-based model fine-tuned for the task of detecting anglicisms](https://huggingface.co/lirondos/anglicisms-spanish-mbert), based on [Transformers library](https://github.com/huggingface/transformers/) (F1=83.55)


## More info
More information about the dataset, model experimentation and error analysis can be found in the paper: *[Detecting Unassimilated Borrowings in Spanish: An Annotated Corpus and Approaches to Modeling](https://aclanthology.org/2022.acl-long.268/)*.

## Citation
If you use this dataset or models, please cite the following reference:
```
@inproceedings{alvarez-mellado-lignos-2022-detecting,
    title = "Detecting Unassimilated Borrowings in {S}panish: {A}n Annotated Corpus and Approaches to Modeling",
    author = "{\'A}lvarez-Mellado, Elena  and
      Lignos, Constantine",
    booktitle = "Proceedings of the 60th Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers)",
    month = may,
    year = "2022",
    address = "Dublin, Ireland",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2022.acl-long.268",
    pages = "3868--3888",
    abstract = "This work presents a new resource for borrowing identification and analyzes the performance and errors of several models on this task. We introduce a new annotated corpus of Spanish newswire rich in unassimilated lexical borrowings{---}words from one language that are introduced into another without orthographic adaptation{---}and use it to evaluate how several sequence labeling models (CRF, BiLSTM-CRF, and Transformer-based models) perform. The corpus contains 370,000 tokens and is larger, more borrowing-dense, OOV-rich, and topic-varied than previous corpora available for this task. Our results show that a BiLSTM-CRF model fed with subword embeddings along with either Transformer-based embeddings pretrained on codeswitched data or a combination of contextualized word embeddings outperforms results obtained by a multilingual BERT-based model.",
}
```
