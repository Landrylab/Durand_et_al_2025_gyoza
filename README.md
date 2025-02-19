# Repo to compare gyōza and DiMSum on a toy DMS dataset

## Installation instructions

To run notebooks from your platform using Jupyter Lab, follow these steps:

0. If you are on Windows or if you don't feel comfortable proceeding to the installation from a terminal, start with step 1a. Otherwise, start with step 1b. If you're on Windows and prefer a light standalone app, you can install [JupyterLab Desktop](https://github.com/jupyterlab/jupyterlab-desktop#download) and skip to step 2.

1. a) Install the [Anaconda](https://www.anaconda.com/download) package/environment management system (if you don't already have it). Registration is optional. Select the appropriate installer for your platform.

1. b) Install [Conda](https://docs.conda.io/).

On MacOS, run:
```
curl -O https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh
sh Miniconda3-latest-MacOSX-x86_64.sh
```
On Linux, run:
```
curl -O https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
sh Miniconda3-latest-Linux-x86_64.sh
```

**IMPORTANT:** If in doubt, respond with "yes" to the following question during installation: "Do you wish the installer to initialize Miniconda3 by running conda init?". In this case Conda will modify your shell scripts (*~/.bashrc* or *~/.bash_profile*) to initialize Miniconda3 on startup. Ensure that any future modifications to your *$PATH* variable in your shell scripts occur **before** this code to initialize Miniconda3.

2. Clone this repository.

If you're using the Anaconda navigator or JupyterLab Desktop, open a prompt. If you don't have git installed, run `conda install git`, then `git clone https://github.com/Landrylab/Durand_et_al_2025_gyoza.git`.

3. Use it to create a virtual environment with the necessary dependencies and activate it:
```
conda env create -n bench-gyoza --file=env.yml
conda activate bench-gyoza
```
At this stage, if you are using the Anaconda navigator, you can simply launch Jupyter Lab and skip steps 4-6.

4. Export kernel.
`python -m ipykernel install --user --name=bench-gyoza`

At this stage, if you are using Jupyter Lab Desktop, you can close the terminal and skip step 5.

5. Run Jupyter Lab from the DMS folder
`jupyter lab`

6. When opening any notebook, depending on the setup, you might need to select the kernel *bench-gyoza*.

## Usage

The [main notebook](DiMSum_benchmark.ipynb) imports data processed by gyōza and DiMSum (toy dataset provided with [gyōza](https://github.com/durr1602/gyoza)). DiMSum's equivalent for the sample layout is this [experimental design file](dimsum/expdesign.txt).

The following command line was used with DiMSum v1.3.2 to process the data:
```
DiMSum --projectName CN_alp_F1 --outputPath /home/rodur28/benchmark/DiMSum/ --experimentDesignPath /home/rodur28/benchmark/DiMSum/expdesign.txt --startStage 1 --numCores 10 --cutadaptErrorRate 0.15 --wildtypeSequence TCTCCTGTTGAAGGTTCTCCAGCTAAGCCAGAAGATTACCCACACTTCATGTCCGTTGCTCACGAACAAGCTTTGAAGTCTTTGTCTGAAGGTGGTATTCCAATTGGTGCTGCTTTGGTTCATTTGCCAACTTCTAGAATTATTTCCAGAGGTCACAACAACAGAGTCCAATTATCTTCTAACGTCCGTCACGGTGAAATGGACTGTTTG --mutagenesisType codon --indels none --maxSubstitutions 3 --fastqFileDir /home/rodur28/gyoza/config/reads/ --vsearchMaxQual 90 --fitnessMinInputCountAll 10 --experimentDesignPairDuplicates T
```