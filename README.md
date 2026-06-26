<div align="center">

# Interaction-Aware 4D Gaussian Splatting for Dynamic Hand-Object Interaction Reconstruction

**ECCV 2026**

[Hao Tian](https://github.com/JasonTian1091)<sup>1,2,5</sup> · Chenyangguang Zhang<sup>3</sup> · Rui Liu<sup>4</sup> · Wen Shen<sup>1,5</sup> · Xiaolin Qin<sup>1,5✉</sup>

<sup>1</sup>Chengdu Institute of Computer Applications, CAS · <sup>2</sup>PetroChina Digital Intelligence Research Institute · <sup>3</sup>Tsinghua University · <sup>4</sup>Minzu University of China · <sup>5</sup>University of Chinese Academy of Sciences

[![Project Page](https://img.shields.io/badge/🌐%20Project-Page-blue?style=for-the-badge)](https://jasontian1091.github.io/Interaction-Aware-Gau-page/)
[![Paper](https://img.shields.io/badge/📄%20Paper-ECCV%202026-red?style=for-the-badge)](https://jasontian1091.github.io/Interaction-Aware-Gau-page/)
[![arXiv](https://img.shields.io/badge/arXiv-coming%20soon-b31b1b?style=for-the-badge&logo=arxiv)](https://arxiv.org)

### 🌐 [Project Page](https://jasontian1091.github.io/Interaction-Aware-Gau-page/) | 📄 [Paper](#bibtex) | 🎬 [Video](https://jasontian1091.github.io/Interaction-Aware-Gau-page/#video)

</div>

---

## Pipeline

<div align="center">
  <img src="https://github.com/JasonTian1091/Interaction-Aware-Gau-page/raw/master/static/images/pipeline_final.png" width="100%" alt="Pipeline">
</div>

> Hand Gaussians and Object Gaussians are each driven by dedicated neural deformation fields, coupled through **Interaction-Aware Parameters**. All components are composited with Background Gaussians and supervised by rendering, alpha, interaction, translation, and rotation losses.

---

## Demo

<div align="center">
  <table>
    <tr>
      <td align="center">
        <img src="https://github.com/JasonTian1091/Interaction-Aware-Gau-page/raw/master/static/media/hoi4d_rgb.gif" width="100%" alt="HOI4D RGB">
        <br><b>HOI4D — RGB Rendering</b>
      </td>
      <td align="center">
        <img src="https://github.com/JasonTian1091/Interaction-Aware-Gau-page/raw/master/static/media/hoi4d_depth.gif" width="100%" alt="HOI4D Depth">
        <br><b>HOI4D — Depth Rendering</b>
      </td>
    </tr>
    <tr>
      <td align="center">
        <img src="https://github.com/JasonTian1091/Interaction-Aware-Gau-page/raw/master/static/media/3dwave_rgb.gif" width="100%" alt="3D Wave RGB">
        <br><b>3D Wave — RGB Rendering</b>
      </td>
      <td align="center">
        <img src="https://github.com/JasonTian1091/Interaction-Aware-Gau-page/raw/master/static/media/3dwave_depth.gif" width="100%" alt="3D Wave Depth">
        <br><b>3D Wave — Depth Rendering</b>
      </td>
    </tr>
  </table>

  <img src="https://github.com/JasonTian1091/Interaction-Aware-Gau-page/raw/master/static/media/transl.gif" width="50%" alt="Translation">
  <br><b>Free-Viewpoint Translation</b>

  <br><br>
  🎬 Full presentation video: <a href="https://jasontian1091.github.io/Interaction-Aware-Gau-page/#video">Project Page → Video</a>
</div>

---

## Abstract

This paper focuses on a challenging setting of simultaneously modeling geometry and appearance of hand-object interaction scenes **without any object priors**. We follow the trend of dynamic 3D Gaussian Splatting based methods, and address several significant challenges.

- **Interaction-Aware Gaussians**: newly introduced optimizable parameters adopting a piecewise linear hypothesis for clearer structural representation under mutual occlusion and edge blur.
- **Interaction-Aware Dynamic Fields**: hand information incorporated into the object deformation field for flexible motion modeling.
- **Progressive Training Strategy**: handles dynamic regions and static background step by step.
- **Explicit Regularizations**: stabilize hand-object representations for smooth motion, physical plausibility, and coherent lighting.

Experiments show state-of-the-art performance on dynamic hand-object interaction reconstruction.

---

## Installation

```bash
git clone https://github.com/JasonTian1091/Interaction-Aware-Gau.git
cd Interaction-Aware-Gau

conda create -n ia4dgs python=3.8
conda activate ia4dgs
pip install -r requirements.txt
```

---

## Dataset

We evaluate on [HOI4D](https://hoi4d.github.io/) and HOID datasets.

Download and place data under `data/`:
```
data/
  HOI4D/
  HOID/
```

---

## Training

```bash
# Stage 1: background
python train.py --config configs/background.yaml --source_path data/HOI4D/scene1

# Stage 2: hand + object (progressive)
python train.py --config configs/full.yaml --source_path data/HOI4D/scene1
```

---

## Evaluation

```bash
python eval.py --model_path output/scene1 --source_path data/HOI4D/scene1
```

---

## BibTeX

```bibtex
@inproceedings{tian2026interactionaware,
  title     = {Interaction-Aware 4D Gaussian Splatting for Dynamic Hand-Object Interaction Reconstruction},
  author    = {Tian, Hao and Zhang, Chenyangguang and Liu, Rui and Shen, Wen and Qin, Xiaolin},
  booktitle = {Proceedings of the European Conference on Computer Vision (ECCV)},
  year      = {2026}
}
```

---

## Acknowledgements

This project builds upon [3D Gaussian Splatting](https://repo-sam.inria.fr/fungraph/3d-gaussian-splatting/), [Deformable 3D Gaussians](https://github.com/ingra14m/Deformable-3D-Gaussians), and [SC-GS](https://github.com/yihua7/SC-GS). We thank the authors for their excellent work.
