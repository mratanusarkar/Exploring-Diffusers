# Setup

For local setup with offline GPUs available,
first set up diffusers locally.

Here are the steps:
1. Make sure you have nvidia drivers installed correctly, you can check this if ```nvidia-smi``` works.
2. Install conda and make sure its working properly
3. Create a new conda environment using ```conda create -n diffusers python=3.10```
4. Activate the newly created conda environment using ```conda activate diffusers```.
5. Install PyTorch using ```pip install torch```, this would install **pytorch 2.0.1 + cuda11.7**
6. Check if torch+cuda installation was successful using ```python -c "import torch; print(torch.cuda.is_available())"```
7. Install further dependencies using ```pip install diffusers["torch"] transformers compel wandb```
8. Once everyhing is set up, try to perform the aforementioned exercise.

Note:
Here are some more additional inputs for the above mentioned steps:
- step 1: you can see the name of the gpu using ```nvidia-smi -L```
- step 2: any of miniconda or anaconda will do. link: https://www.anaconda.com/download
- step 6: you can also use ```python -c "import torch; print(torch.__version__)"```
- step 3-5: some more useful conda commands:
  - conda config --set auto_activate_base false
  - conda info
  - conda info --envs
  - conda activate <venv-name>
  - conda deactivate
  - conda list -f <search-keyword>
- useful info for jupyter notebooks:
  - if you don't have jupyter, get them via: ```conda install jupyter notebook``` or ```conda install jupyterlab```
  - launch notebook using ```jupyter notebook```
- useful tools for monitoring system resource:
  - using nvidia-smi: ```nvidia-smi -l```
  - using htop
    - below are the steps to download and get htop running:
      1. cd Downloads/
      2. wget http://hisham.hm/htop/releases/2.2.0/htop-2.2.0.tar.gz
      3. sudo apt install libncurses5-dev libncursesw5-dev autotools-dev autoconf automake build-essential
      4. sudo apt install htop
      5. htop [-dChusv]



# Recommended Hardwares

- A100 (best)
- RTX A6000 48GB 4dp + 256GB system RAM
- NVIDIA GeForce RTX 3090 (gets OOM sometimes without refiners)
- T4 (colab)



# Useful Links

## Finetune LLMs
- Fine tuning LLMs: https://huggingface.co/docs/diffusers/training/lora
- Fine tuning SD: https://wandb.ai/geekyrakshit/dreambooth-keras/reports/Fine-Tuning-Stable-Diffusion-Using-Dreambooth-in-Keras--VmlldzozNjMzMzQ4
- DreamBooth NB: https://colab.research.google.com/github/huggingface/notebooks/blob/main/diffusers/SDXL_DreamBooth_LoRA_.ipynb

## Distribute Runs across Hardwares or Interfaces
- Distributed Inference: https://huggingface.co/docs/diffusers/training/distributed_inference
- Model Offloading: https://huggingface.co/docs/diffusers/api/pipelines/stable_diffusion/stable_diffusion_xl#memory-optimization-via-model-offloading
- accelerate: https://huggingface.co/docs/accelerate/basic_tutorials/install
- map individual layers to different devices: https://huggingface.co/blog/accelerate-large-models
- make native pytorch modules to be trained using keras: https://colab.research.google.com/drive/1H8srKBGAfo419oAs8YrM9zaMX7wmuD9o?usp=sharing

## SDXL
- SDXL Showcase Report: https://wandb.ai/geekyrakshit/stable-diffusion-xl/reports/A-Guide-to-using-Stable-Diffusion-XL-with-Diffusers--Vmlldzo1MDMxMDU4
- SDXL 0.9: https://huggingface.co/stabilityai/stable-diffusion-xl-base-0.9
- SDXL 1.0: https://huggingface.co/stabilityai/stable-diffusion-xl-base-1.0

## TODO:
- SDXL Runner NBs: https://github.com/wandb/examples/tree/master/colabs/diffusers
- Sample Run to Replicate: https://wandb.ai/geekyrakshit/stable-diffusion-xl/runs/adip2elp



# Draft (sample prompts and negative prompts)

- config.prompt_1 = "Old man crossing a road with stick in hand. the road is filled with cars vehicles and traffic and people. the old man has one stick in his hand. hairing aids in his ears"
- config.prompt_2 = "old man, stick in hand, struggling, busy traffic background, realistic, 8k"
- config.negative_prompt_1 = "static, painting, illustration, sd character, low quality, low resolution, greyscale, monochrome, nose, cropped, lowres, jpeg artifacts, deformed iris, deformed pupils, bad eyes, semi-realistic worst quality, bad lips, deformed mouth, deformed face, deformed fingers, deformed toes standing still, posing"
- config.negative_prompt_2 = "deformed hand, deformed fingers, deformed face, low quality"

---

- config.prompt_1 = Old blind man crossing a road with a stick in hand. black glasses in eyes, hearing aid in ears. the road is filled with vehicles, traffic, and people. side view of the man, busy traffic background, realistic, 8k
- config.negative_prompt_1 = static, painting, illustration, sd character, low quality, low resolution, greyscale, monochrome, nose cropped, low res, jpeg artifacts, deformed iris, deformed pupils, bad eyes, semi-realistic worst quality, bad lips, deformed mouth, deformed face, deformed fingers, deformed toes standing still, posing, deformed hand, deformed fingers, deformed face, low quality

---
