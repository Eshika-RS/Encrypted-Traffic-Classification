# CBS: Encrypted Traffic Classification

A practical implementation of the CBS paper ("A Deep Learning Approach for Encrypted Traffic Classification With Mixed Spatio-Temporal and Statistical Features").

## Overview

This repository contains the preprocessing pipeline and model implementation for classifying encrypted network traffic using a multi-branch deep learning approach (1D-CNN + Bi-LSTM + Statistical features).

**Achieved Test Accuracy:** 94.31% (depending on class weighting)

## Project Structure

- `preprocessing/` — All custom scripts for data preparation
- `models/` — Final Colab notebook for training the CBS model


## Key Features

- Memory-safe batch processing for large pcap files
- Fixed-length packet extraction (1500 bytes)
- Statistical feature extraction for SAE branch
- Multi-branch fusion model (Spatial + Temporal + Statistical)
- Class weight handling for imbalance

## Requirements

See `requirements.txt`

## How to Use

1. Clone the repository
2. Download `final_processed_shuffled.7z` from Releases 
3. Extract it into `data/final_processed_shuffled/`
4. Open `models/cbs_model_training.ipynb` in Google Colab
5. Run the notebook (GPU recommended)
## Preprocessing Pipeline


The preprocessing includes:
- Reading and labeling pcap files
- Header + payload extraction to 1500-byte records
- Normalization (0-1 range)
- Statistical feature computation (mean, std, min, max, percentiles)
- Subsampling and global shuffling

All scripts were customized for stability on 16 GB RAM hardware.

## Limitations

- Used 4-class mapping instead of the paper's 12 classes due to hardware constraints
- Statistical branch uses dense layers (not full SAE)
- Packet-level approach (not full flow/session aggregation)

## Future Work

- Implement true 12-class labeling from raw pcaps
- Add full Stacked Autoencoder for statistical branch
- Integrate session/flow-level features
- Experiment with GAN-based augmentation

## Acknowledgments

Based on the CBS paper by Mehdi Seydali et al.

## License

MIT License

