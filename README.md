# Twitter User Language Experiments

Code and saved notebook outputs accompanying *Analysis of Consistent Linguistic Patterns at User Level of Twitter Users Claiming Autism Spectrum Disorder Using Natural Language Processing*.

The study examines linguistic features and within-user variability, and compares text classifiers at the tweet and user levels. Labels follow the source dataset and self-identification; they are not clinical diagnoses.

## Notebook Guide

| Notebook | Contents | Paper results |
|---|---|---|
| [00 — Data and Linguistic Analysis](00_Data_and_Linguistic_Analysis.ipynb) | Data preparation, user splits, linguistic statistics, and robustness analyses | Tables I–II |
| [01 — Base Models](01_Base_Models.ipynb) | ML, DL, Transformers, linguistic baselines, training, prediction, and bootstrap evaluation | Base-model results in Tables III–IV; baselines in Table IV |
| [02 — OOF Stacking](02_OOF_Stacking.ipynb) | User-disjoint OOF training, meta-learner, validation threshold, and test evaluation | Stacking results in Tables III–V |

Read the notebooks in numerical order. Model definitions, parameters, and training code are inline. Result tables are included in the notebook outputs and can be inspected without running the code. The holdout experiment and five-seed experiments are separate protocols.

## Data

The dataset is [Dataset-ASD-twitter-users](https://github.com/srubm/Dataset-ASD-twitter-users), described by [Rubio-Martín et al. (2024)](https://doi.org/10.1007/s13755-024-00281-y).

Raw tweets, user partitions, individual predictions, and model weights are stored separately from this repository. Re-execution requires the corresponding data and experiment artifacts. The public dataset alone does not supply the experiment-specific artifacts. File paths and stage definitions are included in the notebooks.

## Optional Execution

The notebooks use Google Colab and Google Drive. Raw CSVs are read from `/content/drive_research/MyDrive/thesis/dataset`; generated data, models, and results use `/content/drive_research/MyDrive/thesis/saved_results`. Keep the file structure and user partitions defined in the notebooks. Raw counts require the complete raw snapshot or a preprocessing report whose final counts match the loaded cleaned data.

Dependencies are grouped by stage: [evaluation](requirements-eval.txt), [data and statistics](requirements-data.txt), [TensorFlow](requirements-tensorflow.txt), and [PyTorch/Transformers](requirements-transformer.txt).

Compatible checkpoints and text representations are reused for prediction; stored probabilities support evaluation. Model training requires explicit stage selection and ENABLE_TRAINING=True. Meta-learner fitting and threshold search have additional controls. Select stages in the notebook configuration; their names are listed alongside the corresponding functions.

The dataset snapshot commit and some NLP package versions were not recorded. The exact checkpoint provenance of the holdout Transformer results has not been fully verified.
