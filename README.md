# HackBio-Internship-Stage-0
The stage 0 tasks centres on introduction to BASh perfomed under two project. Project 1 involves basic BASh scripting with exercises walking us through common operations such as file management, sequence inspection, and extraction of metadata, using BASh commands. Project 2 mainly involves installation of bioinformatics tools.
## PROJECT 1: BASh BASICS
Summarily, the tasks under this project include:
1. Name printing and creating directories
```bash
echo ‘SUNDAY’
mkdir sunday
mkdir biocomputing && cd biocomputing
```

2. Downloading and managing files:
```bash
wget https://raw.githubusercontent.com/josoga2/dataset-repos/main/wildtype.fna https://raw.githubusercontent.com/josoga2/dataset-repos/main/wildtype.gbk https://raw.githubusercontent.com/josoga2/dataset-repos/main/wildtype.gbk

mv wildtype.fna ../sunday/
rm wildtype.gbk.1
```  

3. Sequence inspection and extraction of metadata.
```bash
#!/bin/bash
if grep -q ‘tatatata’ wildtype.fna; then
    echo ‘mutant’
elif grep -q 'tata' wildtype.fna; then
    echo ‘wildtype’
fi
 
grep ‘tatatata’ wildtype.fna > confirmed_mutant.fna
tail -n +2 wildtype.gbk | wc -l   # Prints number of lines (excluding header) in the '.gbk' file.
grep "^LOCUS" wildtype.gbk | awk '{print $3}'  # Prints the sequence length.
awk '/^SOURCE/ { $1=""; sub(/^ */, ""); print }' wildtype.gbk  # Prints the source organism.
grep "/gene=" wildtype.gbk | cut -d'"' -f2  # Lists all the gene names in the file.
``` 

## Project 2: Installation of Bioinformatics Tools 




















