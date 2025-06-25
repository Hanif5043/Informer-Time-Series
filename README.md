# Informer-JIGSAW: Position Prediction in Remote Robotic Surgery using Informer

![Python 3.10](https://img.shields.io/badge/python-3.10-green.svg?style=plastic)
![PyTorch 2.0.1](https://img.shields.io/badge/PyTorch%20-%23EE4C2C.svg?style=plastic)
![License: CC BY](https://img.shields.io/badge/license-CC--BY--4.0-green.svg?style=plastic)

This repository contains the official implementation of the following research paper:

📄 **A Predictive Approach for Enhancing Accuracy in Remote Robotic Surgery Using Informer Model**  
*Sensors, 2025 (MDPI)*  
[Read the paper here](https://doi.org/10.3390/s25103067)

---

## 🚀 Overview

This project adapts the **Informer** time-series forecasting architecture for enhancing real-time **position prediction** in **remote robotic surgery** over the Tactile Internet. It specifically focuses on addressing **network-induced packet loss, jitter, and latency** using a **4-State Hidden Markov Model (HMM)** for simulation and optimization.

Key highlights:

- Based on the original [Informer](https://github.com/zhouhaoyi/Informer2020) model
- Optimized for **JIGSAWS** surgical task dataset
- Embedded differentiable optimization constraints (energy, smoothness, robustness)
- Simulated burst and random packet loss for realistic conditions

---

## 🛠 Requirements

- Python 3.10
- PyTorch 2.0.1
- numpy
- pandas
- matplotlib
- scikit-learn

Install all dependencies:
```bash
pip install -r requirements.txt

Dataset: 
We use the JIGSAWS dataset, available from Johns Hopkins University:

🔗 JIGSAWS dataset download

After downloading, place your processed dataset in: /data/JIGSAW/knot_tying.csv

Run the Informer training script:
python -u main_informer.py \
--model informer \
--data JIGSAW \
--attn prob \
--freq t \
--seq_len 96 \
--label_len 48 \
--pred_len 24 \
--root_path ./data/JIGSAW/ \
--data_path knot_tying.csv \
--features M \
--target p_x \
--batch_size 32 \
--learning_rate 0.0005 \
--train_epochs 20 \
--des informer_jigsaws

Modify parameters as needed for your testing (e.g., features, target, paths).

Results: 
Metric	    X (%)	 Y (%)	 Z (%)
Accuracy	96.68	 95.96	 90.37

The Informer model significantly outperforms LSTM, RNN, and TCN models in high packet loss scenarios.

Burst loss and jitter were modeled using a 4-State HMM to simulate real-world TI behavior.

Citation: 
Please cite both our work and the original Informer paper if you use this repository:

@article{lashari2025predictive,
  title={A Predictive Approach for Enhancing Accuracy in Remote Robotic Surgery Using Informer Model},
  author={Lashari, Muhammad Hanif and Ahmed, Shakil and Batayneh, Wafa and Khokhar, Ashfaq},
  journal={Sensors},
  volume={25},
  number={10},
  pages={3067},
  year={2025},
  publisher={MDPI}
}

Acknowledgments
Built on top of Informer2020 by Zhou et al.

JIGSAWS dataset provided by Johns Hopkins University.