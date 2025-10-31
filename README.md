# Latent Codes for Facial Weight Manipulation in StyleGAN
[![arXiv](https://img.shields.io/badge/arXiv-2011.02606-b31b1b.svg)](https://arxiv.org/abs/2011.02606)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![StyleGAN](https://img.shields.io/badge/Model-StyleGAN%20%2F%20StyleGAN2-ff69b4.svg)](https://github.com/NVlabs/stylegan2-ada-pytorch)

This repository provides pre-computed latent direction vectors ($\mathbf{d}$) for manipulating the facial weight attribute within the latent spaces ($\mathcal{W}$ and $\mathcal{W}^{+}$) of pre-trained StyleGAN and StyleGAN2 models.

These direction vectors enable direct and targeted edits to synthesized or projected face images, allowing you to adjust the perceived facial weight of a generated person.


## Folder Structure

The latent directions are organized by the StyleGAN version and the corresponding latent space.
Each direction vector is stored as a NumPy array (`.npy`).

| File                              | StyleGAN Version | Latent Space      | Dimensions      | Description                                                                                   |
| :-------------------------------- | :--------------- | :---------------- | :-------------- | :-------------------------------------------------------------------------------------------- |
| `StyleGAN1/weight.npy`            | StyleGAN1        | $\mathcal{W}^{+}$ | $18 \times 512$ | General facial weight direction.                                                              |
| `StyleGAN1/weight_orth.npy`       | StyleGAN1        | $\mathcal{W}$     | $1 \times 512$  | Orthogonally projected weight direction.                                                      |
| `StyleGAN1/weight_orth_mouth.npy` | StyleGAN1        | $\mathcal{W}$     | $1 \times 512$  | **Best** disentangled result after removing “mouth_open” influence via orthogonal projection. |
| `StyleGAN2/weight.npy`            | StyleGAN2        | $\mathcal{W}^{+}$ | $18 \times 512$ | **Best overall** direction for StyleGAN2 facial weight manipulation.                          |
| `StyleGAN2/weight_2.npy`          | StyleGAN2        | $\mathcal{W}^{+}$ | $18 \times 512$ | Secondary general weight direction.                                                           |


## Usage

To apply an edit, load a latent code $\mathbf{w}$ or $\mathbf{w}^{+}$ (from a generated or projected image), then modify it along the desired direction $\mathbf{d}$ using a scalar factor $\alpha$:

![w' = w ± α·d](https://latex.codecogs.com/png.image?\dpi{110}\bg_white\mathbf{w}'=\mathbf{w}\pm\alpha\cdot\mathbf{d})

Adjust $\alpha$ to control the intensity of the facial weight change.


## Installation and Requirements

You will need:

* NumPy (to load and manipulate direction vectors)
* A StyleGAN or StyleGAN2 implementation, such as:
  * [NVLabs/StyleGAN](https://github.com/NVlabs/stylegan)
  * [NVLabs/StyleGAN2-ADA-PyTorch](https://github.com/NVlabs/stylegan2-ada-pytorch)

Once your environment is set up, simply load the desired `.npy` file and apply the edit as shown above.


## Citation

If you use these latent codes or the associated methodology in your work, please cite:

```bibtex
@misc{pinnimty2020transforming,
  doi = {10.48550/ARXIV.2011.02606},
  url = {https://arxiv.org/abs/2011.02606},
  author = {Pinnimty, V N S Rama Krishna and Zhao, Matt and Achananuparp, Palakorn and Lim, Ee-Peng},
  title = {Transforming Facial Weight of Real Images by Editing Latent Space of StyleGAN},
  publisher = {arXiv},
  year = {2020},
  keywords = {Computer Vision and Pattern Recognition (cs.CV), Artificial Intelligence (cs.AI), Machine Learning (cs.LG)}
}
```
