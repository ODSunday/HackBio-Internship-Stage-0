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
This project involves the following tasks:
1. Activating base conda environment:
a. Downloading and installing Miniconda
```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh   # Downloads Miniconda. 
bash Miniconda3-latest-Linux-x86_64.sh                                       # Installs Miniconda.
conda init                                                                   # Runs Miniconda.
```
b. Activating conda by closing and reopening terminal.
c. Verify with:
```bash
conda --version
```
d. Configuring the necessary channels for Bioinformatics:
```bash
conda config --add channels defaults
conda config --add channels bioconda
conda config --add channels conda-forge
```
2. Creating a conda environment named 'funtools'
```bash
conda create -n funtool python=3.10                      # Creates funtool environment with Python 3.10.
```
3. Activating the 'funtools' environment
```bash
conda activate funtools
```
4. Installing Figlet using conda or apt-get
```bash
sudo apt update && sudo apt install -y figlet            # Used apt-get to install Figlet.
```
5. Running 'figlet <my name>'
```bash
figlet sunday                                            # Nicely displays sunday
```
6. Install bwa through the bioconda channel
```bash
conda install -c bioconda bwa
```
7. Installing blast, samtools, bedtools, spades.py, bcftools, fastp, and multiqc through the bioconda channel.
```bash
conda install -c bioconda blast
conda install -c bioconda samtools
conda install -c bioconda bedtools
conda install -c bioconda spades   
conda install -c bioconda bcftools
conda install -c bioconda fastp
conda install -c bioconda multiqc
```



















