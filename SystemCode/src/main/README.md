# Installation

Installation can be done via Anaconda or Miniconda.The steps for installation of Anaconda or Miniconda and of the application libraries are given below.

## Anaconda/Miniconda installation

Miniconda can be installed by downloading the installer for your operating system from the official website: https://docs.conda.io/projects/miniconda/en/latest/index.html. For those who prefer a GUI, Anaconda would be preferable; the installation file is available via the link: https://www.anaconda.com/download

It is recommended that you install mamba to increase installation speed.

```bash
conda install mamba -n base -c conda-forge
```

## Package installations

The steps for installation of the packages are as follows:
In the bash command line, go to the project root folder.

```bash
$ cd ~/SourceCode/src/main
```

Run the Conda command line tool to create a virtual environment and install the packages listed in the `environment.yml` file.

```bash
$ conda env create -f environment.yml
```

After the installation is completed, the backend API server can be started by running the Flask command.

```bash
$ flask run
```

If the API is running locally, the app can be opened via a browser at the URL http://localhost:5000/

## Models

The models need to be placed in the correct folders for the program to run, or for the model training.

### LoRA models

The LoRA models should be downloaded and placed in the `/LoRA/` folder. Each model file should be a Safetensors file and named as `roomifai_{room_type}`, where room_type corresponds with the room types "living" (for living room), "bedroom" and "dining". The folder schema and names of the files should as follows:

- /LoRA/
  - roomifai_bedroom.safetensors
  - roomifai_dining.safetensors
  - roomifai_living.safetensors

### Stable Diffusion 1.5 pre-trained models

The Stable Diffusion 1.5 pretrained model needs to be placed in the `/checkpoints/pretrained_model/`. The checkpoint model file should be Safetensor file named `v1-5-pruned-emaonly.safetensors`. The file can be downloaded here: https://huggingface.co/runwayml/stable-diffusion-v1-5/blob/main/v1-5-pruned-emaonly.safetensors

### VAE (Optional)

This is only required if you are training the model using the downloaded VAE pre-trained model.

The VAE pretrained model needs to be placed in the `/checkpoints/vae/`. The checkpoint model file should be a checkpoint file named `vae-ft-mse-840000-ema-pruned.ckpt`. The file can be downloaded here: https://huggingface.co/stabilityai/sd-vae-ft-mse-original/blob/main/vae-ft-mse-840000-ema-pruned.ckpt

# Training

The training files need to be placed under the folder `/train/LoRA/`.

Place the training images and their corresponding captions (as .txt files) in a folder. Label the folder with the number of training steps per image underscore class name, e.g. `100_bedroom`.

Follow the instructions in the `run_training.ipynb` file.

# View Tensorboard logs

Type this in bash shell:

```bash
$ tensorboard --logdir="./tensorboard_logs"
```
