# NVIDIA NIM notebooks for Google Colab

Three Colab notebooks that call hosted [NVIDIA NIM](https://build.nvidia.com/) models. They run on the Colab Pro A100 GPU runtime and on the CPU runtime. The models run on NVIDIA data-center GPUs behind `https://integrate.api.nvidia.com`, so each notebook finishes in seconds. The notebooks are committed with their executed outputs, so you can read the replies before you run them.

| Notebook | Model | What it is for |
| --- | --- | --- |
| [Nemotron 3.5 Lightning 30B](notebooks/01_nemotron_3_5_lightning.ipynb) | `nvidia/nemotron-3.5-lightning-30b-a3b` | Fast reasoning. About 30B parameters, 3B active. |
| [Nemotron 3 Ultra 550B](notebooks/02_nemotron_3_ultra.ipynb) | `nvidia/nemotron-3-ultra-550b-a55b` | The largest reasoning model in this set. About 550B parameters, 55B active. |
| [Nemotron 3 Nano Omni 30B](notebooks/03_nemotron_3_nano_omni.ipynb) | `nvidia/nemotron-3-nano-omni-30b-a3b-reasoning` | Image, video, audio, and text in. Text out. |

[![Open Lightning](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/bsudharsh1979/nvidianatlivecolab/blob/main/notebooks/01_nemotron_3_5_lightning.ipynb)
[![Open Ultra](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/bsudharsh1979/nvidianatlivecolab/blob/main/notebooks/02_nemotron_3_ultra.ipynb)
[![Open Omni](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/bsudharsh1979/nvidianatlivecolab/blob/main/notebooks/03_nemotron_3_nano_omni.ipynb)

## Run in Colab

1. Open a notebook with one of the badges above.
2. Click the key icon in the left sidebar.
3. Add a secret named `NVIDIA_API_KEY`.
4. Paste a key from [build.nvidia.com](https://build.nvidia.com/).
5. Enable notebook access for that secret.
6. Choose **Runtime → Change runtime type → A100 GPU**. The first cell prints the attached GPU. If Colab has no A100 free, the CPU runtime gives the same reply because the model runs on NVIDIA's side.
7. Choose **Runtime → Run all**.

Each notebook completes in well under a minute on an A100 runtime. Any Colab runtime with internet access can run them. If the secret is missing, the notebook asks for the key with a hidden prompt instead of printing it.

The demo cells use a few thousand tokens so they finish in a Colab session. Lightning and Ultra accept up to 32,768 tokens. Omni accepts up to 65,536. Raise `MAX_TOKENS` in the last cell if you want a longer reply, and keep it larger than the reasoning trace or the answer comes back empty.

## Local packages

Colab installs these from the first code cells. For a local Jupyter run:

```bash
pip install -r requirements.txt
```

Set `NVIDIA_API_KEY` in the environment before running. Do not commit the key.
