# Automatic Alignment Model
Implementation of the automatic alignment model from the paper **"Aligning Actions Across Recipe Graphs"**. In this paper we present two automatic alignment models (base, extended) and a simple baseline (cosine similarity).

## Requirements
You can find all the requirements in the file `requirement.txt`.
- Python 3.7
- Conllu 4.2.2
- Matplotlib 3.3.2
- Pandas 1.2.3
- Pytorch 1.7.1
- Transformers 4.0.0
- Flair 0.8.0.post1
- AllenNLP 0.9.0

## Usage

Download the corpus from [here](https://github.com/coli-saar/interactive-cookbook/tree/master/data/Alignment) into `./data` folder for reproducing our experiment results. Additionally, create the results folder where the trained models and their test results will be saved (**Notes:** You can change the hyperparameters and the path names in the file `constants.py`). Per default, the script looks for the following results folders:

Model Name | Saves To
--- | ---
Cosine Similarity Baseline | `./results3`
Naive Model | `./results4`
Alignment Model (base) | `./results2`
Alignment Model (extended) | `./results1`

To reproduce our experimental results, run the following command from this directory:

`python main.py [model_name] --embedding_name [embedding_name]`

where `[model_name]` could be one of the following:
- `Sequence` : Sequential Ordering of Alignments
- `Simple` : Cosine model (Baseline)
- `Naive` :  Common Action Pair Heuristics mode (Naive Model)
- `Alignment-no-feature` : Base Alignment model (w/o parent+child nodes)
- `Alignment-with-feature` : Extended Alignment model (with parent+child nodes)

and `[embedding_name]` could be one of the following:
- `bert` : BERT embeddings (default)
- `elmo` : ELMO embeddings

## Results

Our experiment results are as follows:

| Model Name | Accuracy |
| ---------- | :---: |
|Sequential Order | 16.5 |
|Cosine Similarity | 41.5 |
|Naive Model | 52.1 |
| Alignment Model (base) | 66.3 |
| Alignment Model (extended) | **72.4** |

Both the base and the extended Alignment models were trained for 10 folds each with 40 epochs.

