# figure2find - Figure to Find

This project consist of three parts. The first part (setup_prepare_variations.ipynb) sets up all the altered images in order to do the VisionTransformer experiments with it. The second part (segmentation.ipynb) does the actual VisionTransformer segmentation loop with the alternated images. These two first parts contain the technical research that concerns the VisionTransformer. In the end, we have a third part (experiment.ipynb) which contains experiments for detecting and segmenting faces and vases by humans in ambiguous images. The interactive experiment in `experiment.ipynb` displays
`faces_vase_color.jpg` under a lot of salt and pepper noise, and by clicking somewhere on the image, the salt and pepper noise (in that area) is being removed for you.

The goal of the game is to see the faces or the vase in as few as clicks as possible.

## Requirements

- Linux, macOS, or Windows
- Miniconda or Anaconda
- Git

The commands below use **Miniconda** on Linux/macOS. On Windows, run the
equivalent commands in Anaconda Prompt or use the appropriate Miniconda
installer.

## 1. Get the project

Clone the repository and change into its directory:

```bash
git clone https://github.com/campmans/figure2find.git
cd figure2find
```

If the repository is already available locally, just change into its directory:

```bash
cd /path/to/figure2find
```

## 2. Install Miniconda

Install Miniconda if `conda` is not already available. Follow the official
instructions at <https://docs.conda.io/projects/miniconda/en/latest/>.

After installation, initialize Conda for your shell:

```bash
conda init bash
```

Close and reopen the terminal, then confirm that Conda is available:

```bash
conda --version
```

For another shell, replace `bash` with the relevant shell name, such as `zsh`.

## 3. Create and activate the project environment

Create the project environment with Python 3.12:

```bash
conda create -n f2f python=3.12
conda activate f2f
```

If Conda asks you to accept the Anaconda channel Terms of Service, accept them
and rerun the environment creation command:

```bash
conda tos accept --override-channels --channel https://repo.anaconda.com/pkgs/main
conda tos accept --override-channels --channel https://repo.anaconda.com/pkgs/r
```

## 4. Install the dependencies

Install all project and notebook dependencies from `requirements.txt`:

```bash
python -m pip install -r requirements.txt
```

The requirements include PyTorch, torchvision, Ultralytics, segmentation-models-pytorch,
Jupyter widgets, the Matplotlib widget backend, Jupyter kernel support, and Voilà.

## 5. Register the Conda kernel

Register the environment as a Jupyter kernel. This ensures that Voilà executes
the notebook with the packages installed in `f2f`, rather than with a system
Python installation:

```bash
python -m ipykernel install --user \
  --name f2f \
  --display-name "Python (f2f)"
```

## 6. Run the experiment notebook with Voilà

From the repository directory, with `f2f` activated, start Voilà:

```bash
cd /path/to/figure2find
conda activate f2f
python -m voila experiment.ipynb \
  --no-browser \
  --port 8869 \
  --VoilaConfiguration.show_tracebacks=True
```

Open the URL printed by Voilà, normally:

<http://127.0.0.1:8869/>

The notebook uses the `ipympl` Matplotlib widget backend. Click the image
repeatedly to increase the salt-and-pepper noise; each click is marked with a
red cross and updates the click count and noise percentage.

To stop Voilà, press `Ctrl+C` in the terminal running it.

## 7. Run the notebook in JupyterLab (optional)

If you want the full notebook interface instead of the Voilà presentation:

```bash
conda activate f2f
python -m pip install jupyterlab
cd /path/to/figure2find
jupyter lab
```

Open `experiment.ipynb` and select the **Python (f2f)** kernel.
