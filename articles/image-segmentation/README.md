### Custom Image Segmentation


```bash
conda create --name image-segmentation python=3.9
conda activate image-segmentation
conda install -y -c conda-forge nb_conda
python -m ipykernel install --user --name image-segmentation --display-name "image-segmentation (Python 3.9)"
conda deactivate
conda activate image-segmentation
pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
pip install git+https://github.com/facebookresearch/detectron2
jupyter notebook
```
