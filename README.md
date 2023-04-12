"# rstudio-in-singularity" 

Run RStudio on a High Performance Computing Cluster

1) Create the singularity environment -> 
	Download the rocker image: singularity pull docker://rocker/rstudio:4.2 (there is a manual available: https://rocker-project.org/use/singularity.html)

2) run the rstudio script (rstudio.sh) with your job manager, here slurm is used.
sbatch rstudio.sh
cat rstudio-server.job.{JOBID}


3) with ssh-fowarding, forward the rstudio port to your localhost port which should have been displayed after the cat command. open a webbrowser and open http://localhost:8787, the login credentials should have been displayed after the cat command too. 


4) To install libaries (on the hpc), use the correct R-environment (here 4.2) and install the packages into a specific user library via install.packages().

5) Within the RStudio Console, add the path to your new library: <br />
myPaths <- .libPaths() <br />
myPaths <- c(myPaths, "/home/user/R/custom_4.2.2”) <br />
.libPaths(myPaths) <br />
The path can be changed within the install packages tab in RStudio.<br />


6) to install packages: <br />
spack load r <br />
install.packages("packagae_name", lib = "/home/user/R/custom_4.2.2") <br />

7) and when loading a lib in your R script: 
library(packagae_name, lib = "/home/user/R/custom_4.2.2") <br />

8) Good Luck ;)

 

