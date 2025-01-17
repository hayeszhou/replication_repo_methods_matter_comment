### About this documentation
This documentation gives an overview of those files included in this repository that are needed to replicate the results of "Kranz, S. and Pütz. P.: Methods Matter: p-Hacking and Publication Bias in Causal Analysis in Economics: Comment", aimed for publication in the AER.
The analyses were conducted using R 4.0.5 (64 bit, Windows). All R and Stata scripts are stored in the folder "Scripts", provided and created datasets are located in the folder "Data", manually created latex templates are stored in the folder "Tex_templates" and results obtained by running the scripts are stored in the folder "Results". All datasets and results that either need a long time or Stata to be generated are already provided in the respective folders.

### Manual to replicate the results
If you use RStudio, open the R project 
`mm_replication.Rproj` first, then all R scripts loaded into this project should run as they are. Adjustments of the paths should be only necessary for the do-file (see 6.)
If you do not use an R project, you have to set your working directory at the beginning of each R script (`setwd(…)`) to the directory where the scripts are located.

0. Install the required packages by using "install_packages.R". Note that the package [RoundingMatters](https://github.com/skranz/RoundingMatters) was written mainly for this replication.

1. Run the function "adapt.MM.data" in "make_new_data.R"" to create the adapted version of BCH's data set:
`source("Scripts/make_new_data.R")`
`adapt.MM.data()`

2. Run dsr_job.R to create immediate files for dsr derounding.
`source("Scripts/dsr_job.R")`

3. Source "deround_bch.R" and run the function "study.windows.with.bch.data" to create data for randomization tests.
`source("Scripts/deround_bch.R")`
`study.windows.with.bch.data()`

4. After you have run those functions you can run/knit the RMD files to generate most of the figures and tables. The binomial tests are created by "binom_tables.Rmd".

5. "mc.R" contains code for the Monte-Carlo simulation. Takes very long to run.
`source("Scripts/mc.R")`
`run.mc()`

6. There are no R files for the caliper tests. We used the stata code provided by BCH with slight amendments ("caliper_tables.do"). Adjust working directories whenever the command "cd" is used.
