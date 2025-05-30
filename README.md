## Coded-InvNet: Resilient Prediction Serving with Invertible Neural Networks

This repository provides the official implementation of the paper:

**Coded-InvNet for Resilient Prediction Serving Systems** <br/>
Tuan Dinh, Kangwook Lee<br/>
Presented at the 38th International Conference on Machine Learning (ICML 2021)<br/>
[Paper Link](https://proceedings.mlr.press/v139/dinh21a.html) ￼

**Overview**: 
Coded-InvNet is a novel approach designed to enhance the resilience of prediction serving systems against stragglers and node failures. By leveraging invertible neural networks and principles from coded computation, Coded-InvNet enables the reconstruction of missing predictions with high accuracy, even when certain compute nodes fail or are delayed.

**Key Features:**
* Invertible Neural Networks: Utilizes the bijective nature of invertible networks to facilitate the reconstruction of missing outputs.
* Coded Computation: Incorporates coding strategies to distribute computation redundantly, allowing for recovery from partial results.
* High Accuracy Recovery: Achieves up to 85.9% accuracy in recovering missing predictions, significantly outperforming previous methods.
* Low Overhead: Maintains resilience with as little as 10% compute resource overhead. ￼

**Results**: Our experiments demonstrate that Coded-InvNet can recover missing predictions with an accuracy of 85.9%, outperforming previous state-of-the-art methods by 32.5%, even with only 10% compute resource overhead.

--- 
## Training 

*Prerequisites*
* Python 3.6 or higher
* PyTorch 1.7 or higher

We show the script for training our model on MNIST, with the configuration:
* using i-ResNet-64 for the invertible network
* PixPix for the fusion network
* k=2

#### 1. Train the invertible network
```py
python ./main.py --config_file configs/mnist.json
```

#### 2. Generate the fusion dataset 
```py
python ./main.py --config_file configs/mnist.json -fusion --nactors 2 -sample_fusion
```

#### 3. Train fusion network
```py
python ./main.py --config_file configs/mnist.json -fusion --nactors 2 
```

#### 4. Evaluate the fusion network
```py
python ./main.py --config_file configs/mnist.json -fusion --nactors 2 -test_fusion
```

---

**Citation**: If you find this work useful, please cite our paper:

```tex
@inproceedings{pmlr-v139-dinh21a,
  title={Coded-InvNet for Resilient Prediction Serving Systems},
  author={Dinh, Tuan and Lee, Kangwook},
  booktitle={Proceedings of the 38th International Conference on Machine Learning},
  pages={2749--2759},
  year={2021},
  publisher={PMLR}
}
```

