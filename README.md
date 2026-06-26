# Interaction-Aware 4D Gaussian
Our method focuses on a challenging setting of simultaneously modeling geometry and appearance of hand-object interaction (HOI) scenes without any object priors. Our approach achieves high fidelity, physically realistic hand-object interaction, smooth edge transitions and enhance lighting coherence in HOI scenes.
---
## Video

## Install 
* Python (3.8+)
* PyTorch (2.0.0+)
* CUDA (11.8)
* Mano (MANO_LEFT.pkl, MANO_RIGHT.pkl) is needed to download from Mano's official website.
```bash
conda env create -f environment.yml

# diff-gaussian-rasterization
pip install ./submodules/diff-gaussian-rasterization

# simple-knn
pip install ./submodules/simple-knn
```
---
## Run
```bash
conda activate your_env_name
# train
CUDA_VISIBLE_DEVICES=0 python train_unify_hoi4d.py --source_path /path/to/your/dataset --model_path /path/to/your/outputs/model --iterations_node_rendering 3000 --iterations_hand_rendering 3000 --iterations_scene_rendering 4000
# render
CUDA_VISIBLE_DEVICES=0 python render_unify.py --source_path /path/to/your/dataset --model_path /path/to/your/outputs/model --W 800 --H 800 --gui --mode unify --deform_type node --iteration <iteration of best metrices>
```
