**QIIME 2 in RStudio: Step-by-Step Guide**

Welcome to Advanced Applied Microbiome Bioinformatics, Summer 2025.

This guide will walk you through installing the necessary packages, configuring RStudio to run QIIME 2 commands, and executing a sample demux summarize command entirely within R.


**Prerequisites**

- R (version ≥ 4.1)

- RStudio

- Miniconda or Anaconda

- A QIIME 2 conda environment qiime2-amplicon-2024.10

**Step 1: Activate QIIME2 Environment in your terminal**

I assume you have qiime2-amplicon-2024.10 installed in your system.

```{bash}
conda activate qiime2-amplicon-2024.10
```

Lets verify, you have qiime2 in your machine.

```{bash}

which qiime
```

This "which qiime' should give the path to the binary (CLI).

It should give something like:

```
/Users/ugalab4/anaconda3/envs/qiime2-amplicon-2024.10/bin/qiime
```

If you don't see the output path, most probably you don't have qiime2 installed in your system.

Ask for installation documentation. 


**Step 2: Launch RStudio from within the QIIME 2 Env**

On the activated (qiime2 ) terminal, open R studio.

```
open -a RStudio
```
Or, you can launch R studio manually.


**Step 3: Manually Configure R's PATH**

Point your bin's dir path

```
qiime_bin <- "/Users/ugalab4/anaconda3/envs/qiime2-amplicon-2024.10/bin"

```
The path should be the one you get when you executed the "which qiime" command in your terminal. 










