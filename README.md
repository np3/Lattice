# Lattice
Code for our paper [Robust (Controlled) Table-to-Text Generation with Structure-Aware Equivariance Learning](https://arxiv.org/abs/2205.03972) at NAACL 2022.

## Quick Links
  - [Overview](#overview)
  - [Requirements](#requirements)
  - [Data](#data)
  - [Run](#run)
  - [Citation](#citation)

## Overview
Previous table-to-text generation methods suffer from the loss of structural information and are brittle to table layout change. Lattice alters Transformer with a [structure-aware self-attention mechanism](model/structural_attention.py), and a [tranformation-invariant positional encoding mechanism](model/invariant_position.py) to address the aforementioned problems.

![](figure/model.png)


## Requirements
```bash
pip install -r requirements.txt
```


## Data

### Download [ToTTo dataset](https://github.com/google-research-datasets/totto)
```bash
 wget https://storage.googleapis.com/totto-public/totto_data.zip
 unzip totto_data.zip
```

### Preprocessing
```bash
python preprocess/preprocess_data.py --input_path="totto_data/totto_dev_data.jsonl" --output_path="totto_data/totto_dev_data_linearized.jsonl"
python preprocess/json_to_csv.py -i totto_data/totto_dev_data_linearized.jsonl -o totto_data/totto_dev_data.csv
```

## Run
```bash
bash run.sh
```

### Evaluation
The BLEU score printed during training is only for reference. 
To get accurate scores, please use the [official evaluation tool](https://github.com/google-research/language/tree/master/language/totto) or [submit the predictions](https://forms.gle/AcF9TRqWrPhPzztt7) to the official leaderboard.

## Citation
Please cite our paper if you use Lattice in your work:
```
@inproceedings{wang2022robust,
  title={Robust (Controlled) Table-to-Text Generation with Structure-Aware Equivariance Learning},
  author={Wang, Fei and Xu, Zhewei and Szekely, Pedro and Chen, Muhao},
  booktitle={Proceedings of the 2022 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies},
  year={2022}
}
```