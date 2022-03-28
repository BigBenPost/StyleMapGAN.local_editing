# StyleMapGAN.local_editing

![ubuntu](https://img.shields.io/badge/ubuntu-18.04.5_LTS-green.svg?style=plastic) ![CUDA](https://img.shields.io/badge/CUDA-10.0.130-green.svg?style=plastic) ![CUDA-driver](https://img.shields.io/badge/CUDA_driver-410.72-green.svg?style=plastic) ![cudnn7](https://img.shields.io/badge/cudnn-7.6.3-green.svg?style=plastic) ![Python 3.6.12](https://img.shields.io/badge/python-3.6.12-green.svg?style=plastic) ![pytorch 1.4.0](https://img.shields.io/badge/pytorch-1.4.0-green.svg?style=plastic)

My FYP project. 

<p align="left"><img width="100%" src="assets/title.png" /></p>


Project Title: __Towards Superior Control in Automatic Face Editing with Generative Adversarial Networks__

__Abstract__: Generative Adversarial Networks (GANs) have been widely used in image manipulation tasks such as local editing and image interpolation. This project examines StyleMapGAN, a novel approach that evolves from StyleGAN by replacing AdaIN with intermediate latent space carrying information on spatial dimensions, hence capable of performing high-quality local editing. In addition, by introducing a BiSeNet-based face parsing model, this project develops a fully automated process in local editing of human faces that only takes a few seconds. This project demonstrates that the face parsing model outputs masks that rivals manually labelled face datasets. Furthermore, this project explores more controls in local editing by introducing a pair of unaligned masks during stylemap mixing in W+ space in the generator. Local editing with interpolation is achieved and a demo application is developed to demonstrate the local editing process. Source code is avaliable at https://github.com/mushroomsc/StyleMapGAN.local_editing

## Installation

Clone this repository:

```bash
git clone https://github.com/mushroomsc/StyleMapGAN.local_editing
cd StyleMapGAN.local_editing/
```

Install the dependencies:
```bash
conda create -y -n stylemapgan python=3.6.12
conda activate stylemapgan
./install.sh
```

## Demo

<b>Youtube video</b>
Click the figure to watch the demo video.

 __(The current video is a placeholder only. Will be updated by 20th Apr)__

<p align="left"><a target="_blank" rel="noopener noreferrer" href="https://www.youtube.com/watch?v=j5VboflP4NE"><img width="100%" src="assets/teaser_video.png" /></a></p>

<b>Interactive demo app</b>
Run demo in your local machine.

All test images are from [CelebA-HQ](https://arxiv.org/abs/1710.10196).

```bash
python demo.py
```

<b>Use your own images</b>

```bash
cp -R [source folder] demo/components/img/celeba_hq # copy your own images to the demo folder
cd face_parsing
python test.py # mask generation
```

## Generate images

<b>Local editing</b>
Results are saved to `expr/local_editing`. 

```bash
python generate.py --ckpt expr/checkpoints/celeba_hq_256_8x8.pt --mixing_type local_editing --test_lmdb data/celeba_hq/LMDB_test --local_editing_part [part name]
```
<b>Use your own images</b>
```bash
# transforms raw image to LMDB format
python prepare_data.py [raw images path] --out [destination path] --size [TARGET_SIZE] 
```

## Related Projects
This project starts from [StyleMapGAN official code](https://github.com/naver-ai/StyleMapGAN). Face parsing model starts from [face parsing using BiSeNet](https://github.com/zllrunning/face-parsing.PyTorch)。
