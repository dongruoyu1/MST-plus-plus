# MST++: Multi-stage Spectral-wise Transformer for Efficient Spectral Reconstruction (CVPRW 2022)

[Yuanhao Cai](caiyuanhao1998.github.io), [Jing Lin](https://scholar.google.com/citations?hl=zh-CN&user=SvaU2GMAAAAJ), [Zudi Lin](https://zudi-lin.github.io/), [Haoqian Wang](https://scholar.google.com.hk/citations?user=eldgnIYAAAAJ&hl=zh-CN), [Yulun Zhang](yulunzhang.com), [Hanspeter Pfister](https://vcg.seas.harvard.edu/people), [Radu Timofte](https://people.ee.ethz.ch/~timofter/), and [Luc Van Gool](https://ee.ethz.ch/the-department/faculty/professors/person-detail.OTAyMzM=.TGlzdC80MTEsMTA1ODA0MjU5.html)

The first two authors contribute equally to this work

#### News
- **April 17, 2022:** Our paper has been accepted by CVPRW 2022, code and models have been released
- **April 2, 2022:** We win the **First** place of NIRE 2022 Challenge on Spectral Reconstruction from RGB

<hr />

> **Abstract:** *Existing leading methods for spectral reconstruction (SR) focus on designing deeper or wider convolutional neural networks (CNNs) to learn the end-to-end mapping from the RGB image to its hyperspectral image (HSI). These CNN-based methods achieve impressive restoration performance while showing limitations in capturing the long-range dependencies and self-similarity prior. To cope with this problem, we propose a novel Transformer-based method, Multi-stage Spectral-wise Transformer (MST++),  for efficient spectral reconstruction. In particular, we employ Spectral-wise Multi-head Self-attention (S-MSA) that is based on the HSI spatially sparse while spectrally self-similar nature to compose the basic unit, Spectral-wise Attention Block (SAB). Then SABs build up Single-stage Spectral-wise Transformer (SST) that exploits a U-shaped structure to extract multi-resolution contextual information. Finally, our MST++, cascaded by several SSTs, progressively improves the reconstruction quality from coarse to fine. Comprehensive experiments show that our MST++ significantly outperforms other state-of-the-art methods. In the NTIRE 2022 Spectral Reconstruction Challenge, our approach won the First place.* 
<hr />

## Network Architecture
![Illustration of MST](/figure/MST.png)

Our MST++ is mainly based on our work [MST](https://github.com/caiyuanhao1998/MST), which is accepted by CVPR 2022.

## Comparison with State-of-the-art Methods
This repo is a baseline and toolbox containing 11 image restoration algorithms for Spectral Reconstruction.

We are going to enlarge our model zoo in the future.


<details close>
<summary><b>Supported algorithms:</b></summary>

* [x] [MST++](https://arxiv.org/abs/2111.07910) (CVPRW 2022)
* [x] [MST](https://arxiv.org/abs/2111.07910) (CVPR 2022)
* [x] [HDNet](https://arxiv.org/abs/2203.02149) (CVPR 2022)
* [x] [Restormer](https://arxiv.org/abs/2111.09881) (CVPR 2022)
* [x] [MPRNet](https://github.com/swz30/MPRNet) (CVPR 2021)
* [x] [HINet](https://arxiv.org/abs/2105.06086) (CVPRW 2021)
* [x] [MIRNet](https://arxiv.org/abs/2003.06792) (ECCV 2020)
* [x] [AWAN](https://arxiv.org/abs/2005.09305) (CVPRW 2020)
* [x] [HRNet](https://arxiv.org/abs/2005.04703) (CVPRW 2020)
* [x] [HSCNN+](https://openaccess.thecvf.com/content_cvpr_2018_workshops/w13/html/Shi_HSCNN_Advanced_CNN-Based_CVPR_2018_paper.html) (CVPRW 2018)
* [x] [EDSR](https://arxiv.org/abs/1707.02921) (CVPRW 2017)

</details>

![comparison_fig](/figure/compare_fig.png)

### Results on NTIRE 2022 HSI Dataset - Validarion
|  Method   | Params (M) | FLOPS (G) |    MRAE    |    RMSE    |   PSNR    |  Model Zoo   |
| :-------: | :--------: | :-------: | :--------: | :--------: | :-------: | :----------: |
|  HSCNN+   |    4.65    |  304.45   |   0.3814   |   0.0588   |   26.36   | Google Drive |
|   HRNet   |   31.70    |  163.81   |   0.3476   |   0.0550   |   26.89   | Google Drive |
|   EDSR    |    2.42    |  158.32   |   0.3277   |   0.0437   |   28.29   | Google Drive |
|   AWAN    |    4.04    |  270.61   |   0.2500   |   0.0367   |   31.22   | Google Drive |
|   HDNet   |    2.66    |  173.81   |   0.2048   |   0.0317   |   32.13   | Google Drive |
|   HINet   |    5.21    |   31.04   |   0.2032   |   0.0303   |   32.51   | Google Drive |
|  MIRNet   |    3.75    |   42.95   |   0.1890   |   0.0274   |   33.29   | Google Drive |
| Restormer |   15.11    |   93.77   |   0.1833   |   0.0274   |   33.40   | Google Drive |
|  MPRNet   |    3.62    |  101.59   |   0.1817   |   0.0270   |   33.50   | Google Drive |
|   MST-L   |    2.45    |   32.07   |   0.1772   |   0.0256   |   33.90   | Google Drive |
| **MST++** |  **1.62**  | **23.05** | **0.1645** | **0.0248** | **34.32** | Google Drive |

Our MST++ siginificantly outperforms other methods while requiring cheaper Params and FLOPS.

## 1. Create Envirement:

- Python 3 (Recommend to use [Anaconda](https://www.anaconda.com/download/#linux))

- [PyTorch >= 1.3](https://pytorch.org/) 

- NVIDIA GPU + [CUDA](https://developer.nvidia.com/cuda-downloads)

- Python packages:

  ```shell
  pip install -r requirements.txt
  ```

## 2. Data preparation:

- Download [training spectral images](https://drive.google.com/file/d/1FQBfDd248dCKClR-BpX5V2drSbeyhKcq/view), [training RGB images](https://drive.google.com/file/d/1A4GUXhVc5k5d_79gNvokEtVPG290qVkd/view),  [validation spectral images](https://drive.google.com/file/d/12QY8LHab3gzljZc3V6UyHgBee48wh9un/view), [validation RGB images](https://drive.google.com/file/d/19vBR_8Il1qcaEZsK42aGfvg5lCuvLh1A/view), and [testing RGB images](https://drive.google.com/file/d/1A5309Gk7kNFI-ORyADueiPOCMQNTA7r5/view) from the [competition website](https://codalab.lisn.upsaclay.fr/competitions/721#participate-get_data).

- Place the training spectral images and validation spectral images to "/MST-plus-plus/dataset/Train_Spec/".

- Place the training RGB images and validation RGB images to "/MST-plus-plus/dataset/Train_RGB/".

- Place the testing RGB images  to "/MST-plus-plus/dataset/Test_RGB/".

- Then the code are collected as the following form:

  ```shell
  |--MST-plus-plus
  	|--test_challenge_code
  	|--test_develop_code
      |--train_code  
      |--dataset 
          |--Train_Spec
              |--ARAD_1K_0001.mat
              |--ARAD_1K_0002.mat
              ： 
              |--ARAD_1K_0950.mat
     		|--Train_RGB
              |--ARAD_1K_0001.jpg
              |--ARAD_1K_0002.jpg
              ： 
              |--ARAD_1K_0950.jpg
          |--Test_RGB
              |--ARAD_1K_0951.jpg
              |--ARAD_1K_0952.jpg
              ： 
              |--ARAD_1K_1000.jpg
          |--split_txt
          	|--train_list.txt
          	|--test_list.txt
  ```

## 2. Evaluation on the validation set:

(1)  Download the pretrained model zoo from [Google Drive](https://drive.google.com/drive/folders/1GzsNbd-XC8UZEq5V4JaisEyCSKVihCQG?usp=sharing) and place them to ' /source_code/test_develop_code/model_zoo/'. 

(2)  Run the following command to test the model on the validation RGB images. 

```shell
cd /MST-plus-plus/test_develop_code/
python test.py --data_root ../dataset/  --method mst_plus_plus --pretrained_model_path ./model_zoo/mst_plus_plus.pth --outf ./exp/mst_plus_plus/  --gpu_id 0
```

The results will be saved in '/MST-plus-plus/test_develop_code/exp/mst_plus_plus/' in the mat format and the evaluation metric (including MRAE,RMSE,PSNR) will be printed.

## 3. Evaluation on the test set:

(1)  Download the pretrained model zoo from [Google Drive](https://drive.google.com/drive/folders/1pAzS3YY8-Av49i-uoF7GLzodnt1qYReL?usp=sharing) and place them to ' /MST-plus-plus/test_challenge_code/model_zoo/'. 

(2)  Run the following command to test the model on the testing RGB images. 

```shell
cd /MST-plus-plus/test_challenge_code/
python test.py --data_root ../dataset/  --method mst_plus_plus --pretrained_model_path ./model_zoo/mst_plus_plus.pth --outf ./exp/mst_plus_plus/  --gpu_id 0
```

## 4. Training


To train a single model, run

```shell
cd /MST-plus-plus/train_code/
python train.py --method mst_plus_plus  --batch_size 20 --end_epoch 300 --init_lr 4e-4 --outf ./exp/mst_plus_plus/ --data_root ../dataset/  --patch_size 128 --stride 8  --gpu_id 0
```

The training log and models will be saved in '/MST-plus-plus/train_code/exp/mst_plus_plus/'.

## Citation
```
@inproceedings{mst,
	title={Mask-guided Spectral-wise Transformer for Efficient Hyperspectral Image Reconstruction},
	author={Yuanhao Cai and Jing Lin and Xiaowan Hu and Haoqian Wang and Xin Yuan and Yulun Zhang and Radu Timofte and Luc Van Gool},
	booktitle={Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},
	year={2022}
}

@inproceedings{mst_pp,
  title={MST++: Multi-stage Spectral-wise Transformer for Efficient Spectral Reconstruction},
  author={Yuanhao Cai and Jing Lin and Zudi Lin and Haoqian Wang and Yulun Zhang and Hanspeter Pfister and Radu Timofte and Luc Van Gool},
  booktitle={Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR) Workshops},
  year={2022}
}
```
