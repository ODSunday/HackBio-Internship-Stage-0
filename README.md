# HackBio-Internship-Stage-0
The stage 0 tasks centres on introduction to BASh perfomed under two project. Project 1 involves basic BASh scripting with exercises walking us through common operations such as file management, sequence inspection, and extraction of metadata, using BASh commands. Project 2 mainly involves installation of bioinformatics tools.
## PROJECT 1: BASh BASICS
Summarily, the tasks under this project include:
1. Name printing and creating directories
```bash
echo ‘SUNDAY’        # Prints my name.
mkdir sunday         # Creates a folder titled my name.
mkdir biocomputing && cd biocomputing        # Creates a new directory and changes to it with one line of command
```

2. Downloading and managing files:
```bash
wget https://raw.githubusercontent.com/josoga2/dataset-repos/main/wildtype.fna https://raw.githubusercontent.com/josoga2/dataset-repos/main/wildtype.gbk https://raw.githubusercontent.com/josoga2/dataset-repos/main/wildtype.gbk
# Downloads all the three files

mv wildtype.fna ../sunday/       # Moves this particular file to the folder tiltle my name. 
rm wildtype.gbk.1                # Deletes the duplicate file.
```  

3. Sequence inspection and extraction of metadata.
```bash
#!/bin/bash

if grep -q ‘tatatata’ wildtype.fna; then
    echo ‘mutant’
elif grep -q 'tata' wildtype.fna; then
    echo ‘wildtype’
fi
# Confirms if the '.fna' file is mutant or wild type (tatatata vs tata).
 
grep ‘tatatata’ wildtype.fna > confirmed_mutant.fna             # Prints all mutant-matching lines into a new file.
tail -n +2 wildtype.gbk | wc -l                                 # Prints number of lines (excluding header) in the '.gbk' file.
grep "^LOCUS" wildtype.gbk | awk '{print $3}'                   # Prints the sequence length.
awk '/^SOURCE/ { $1=""; sub(/^ */, ""); print }' wildtype.gbk   # Prints the source organism.
grep "/gene=" wildtype.gbk | cut -d'"' -f2                      # Lists all the gene names in the file.
``` 

## Project 2: Installation of Bioinformatics Tools 
#1. Activate your base conda environment
# First, On the GitHub Codespace, I downloaded the latest Linux 64-bit Miniconda installer from Miniconda’s official site and installed it as follows:
$ wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
$ bash Miniconda3-latest-Linux-x86_64.sh 
$ conda init # To let it run.
# Next, Conda was activated succesfully by closing and reopening my terminal, and verified with the following command:
$ conda --version
# Finally, I configured the necessary channels for Bioinformatics as follows:
$ conda config --add channels defaults
  conda config --add channels bioconda
  conda config --add channels conda-forge

#2. Create a conda environment named funtools
$ conda create -n funtool python=3.10   # Creates fun

#3. Activate the funtools environment
$ conda activate funtools

#4. Install Figlet using conda or apt-get
$ sudo apt update && sudo apt install -y figlet # Used apt-get to install Figlet.

#5. Run figlet <your name>
$ figlet sunday   # Displays sunday

#6. Install bwa through the bioconda channel
$ conda install -c bioconda bwa

#7. Install blast through the bioconda channel
$ conda install -c bioconda blast

#8. Install samtools through the bioconda channel
$ conda install -c bioconda samtools

#9. Install bedtools through the bioconda channel
$ conda install -c bioconda bedtools

#10. Install spades.py through the bioconda channel
$ conda install -c bioconda spades   

#11. Install bcftools through the bioconda channel
$ conda install -c bioconda bcftools

#12. Install fastp through the bioconda channel
$ conda install -c bioconda fastp

13. Install multiqc through the bioconda channel
$ conda install -c bioconda multiqc




















