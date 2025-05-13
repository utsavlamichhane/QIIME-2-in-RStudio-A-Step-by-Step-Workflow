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

Point your bin's dir path.

Run the following command in R console.

```
qiime_bin <- "/Users/ugalab4/anaconda3/envs/qiime2-amplicon-2024.10/bin"
```
The path should be the one you get when you executed the "which qiime" command in your terminal in **Step 2**. 


Now, prepend it to R' path using following command in R console.

```
Sys.setenv(PATH = paste(qiime_bin, Sys.getenv("PATH"), sep = ":"))
```

Verify the path by running the following command in the R console;

```
Sys.which("qiime")
```



**Step 4: Install & Load qiime2R**

qiime2R lets you import QIIME 2 artifacts (QZA/QZV) into R as data frames or lists.

Since, this is not available via CRAN, lets intall it from GitHub.

Run the following command in your console.

This will take a while.

```
install.packages("remotes")                   
remotes::install_github("jbisanz/qiime2R")   
library(qiime2R)
```

**Step 5: Download the sample qza file**

Use the google drive link to download the file.

```
https://drive.google.com/file/d/1R20wyjx0Dd2tcWmL_jK-ePqcouu36sqM/view?usp=sharing
```

**Step 6: Change the working dir**

After you download the paired_end.qza file, change the working directory in R studio to the same directory with the file. 


**Step 7: Define the run_qiime() Helper Function**

Writing function saves us from writing the full command (to use qiime2 command) every time.

Write and execute the following function in your R studio. 

```
run_qiime <- function(..., echo = TRUE) {
  args <- unlist(list(...))
  if (echo) message("Calling: qiime ", paste(args, collapse = " "))
  res <- system2("qiime", args, stdout = TRUE, stderr = TRUE)
  cat(res, sep = "\n")
  invisible(res)
}
```

**Step 8: Run the sample command**


Run the following command in your R studio:

```
run_qiime(
  "demux", "summarize",
  "--i-data",          "paired_end.qza",
  "--o-visualization", "Paired-End_seqs.qzv"
)
```

You should see the output in your working directory.









