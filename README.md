# [Re]SinGAN: Learning a Generative Model from a Single Natural Image

We successfully reproduce experiments from ICCV 2019 Best paper "SinGAN: Learning a Generative Model from a Single Natural Image" by Tamar Rott Shaham, Tali Dekel and Tomer Michaeli.

> we analyze the reproducibility of SinGAN. In assessing the SinGAN model, we analyze its ability about random sample images generation of different start scales when trained on a specific image and high-resolution image generation when trained on a low-resolution image.

In this repository, we include our reproduction code and data for SinGAN experiments. This code has been modified from the data used in the official project

## Code

### Install dependencies

```
python -m pip install -r requirements.txt
```

This code was tested with python 3.7, torch 1.1

Please note: the code currently only supports torch 1.4 or earlier because of the optimization scheme.

###  Train
To train SinGAN model on your own image, put the desired training image under Input/Images, and run

```
python main_train.py --input_name <input_file_name>
```

This will also use the resulting trained model to generate random samples starting from the coarsest scale (n=0).

To run this code on a cpu machine, specify `--not_cuda` when calling `main_train.py`

###  Random samples
To generate random samples from any starting generation scale, please first train SinGAN model on the desired image (as described above), then run 

```
python random_samples.py --input_name <training_image_file_name> --mode random_samples --gen_start_scale <generation start scale number>
```

pay attention: for using the full model, specify the generation start scale to be 0, to start the generation from the second scale, specify it to be 1, and so on. 

### Super Resolution
To super resolve an image, please run:
```
python SR.py --input_name <LR_image_file_name>
```
This will automatically train a SinGAN model correspond to 4x upsampling factor (if not exist already).
For different SR factors, please specify it using the parameter `--sr_factor` when calling the function.
SinGAN's results on the BSD100 dataset can be download from the 'Downloads' folder.

For additional details please see section the original [paper](https://arxiv.org/pdf/1905.01164.pdf)

<!-- ## Results
### Results reproducing original paper
#### Random samples generation
<p align="center" width="100%">
<img src="imgs\Figure1.png" style="width: 60%; min-width: 300px; display: block; margin: auto;">
</p>

#### Super Resolution
<p align="center" width="100%">
<img src="imgs\Figure2.png" style="width: 60%; min-width: 300px; display: block; margin: auto;">
</p>

### Results beyond original paper
<p align="center" width="100%">
<img src="imgs\Figure3.png" style="width: 60%; min-width: 300px; display: block; margin: auto;">
</p>

#### Super Resolution
<p align="center" width="100%">
<img src="imgs\Figure4.png" style="width: 60%; min-width: 300px; display: block; margin: auto;">
</p> -->