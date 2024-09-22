# BioE_230

## Download data from NCBI and upload to Ibex

```bash
scp ncbi_dataset.zip ashhadm@ilogin.ibex.kaust.edu.sa:/home/ashhadm/in_class/
```
## Unzip files

```bash
cd in_class
unzip ncbi_dataset.zip
```
## What is the smallest and what is the largest genome in the ones you just downloaded? How large are these genomes?

```bash
cut -f 1,11 data_summary.tsv > size.tsv
tail -n +2 size.tsv | sort -t$'\t' -k2 -n | head -n 1
tail -n +2 size.tsv | sort -t$'\t' -k2 -n | tail -n 1
```
![image](https://github.com/user-attachments/assets/86e42d6f-3881-4dfe-878a-e39f2ba93243)


## Smallest and largest genome

```bash
cut -f 11 data_summary.tsv | sort -n | uniq -d | head -n 1 > small_genome.txt
cut -f 11 data_summary.tsv | sort -n | uniq -d | tail -n 1 > large_genome.txt
```
## Find the number of genomes that contain at least two “c” in the species name. How many of the species names contain two or more “c” but do not contain the word “coccus”?

```bash
tail -n +2 data_summary.tsv | cut -f 1| grep -c "c.*c" > atleast_2c.txt
tail -n +2 data_summary.tsv | cut -f 1| grep -c "c.*c" | grep -cv "coccus" > atleat_2c_coccus.txt
```
## Use the find command to find all genome files (FASTA) larger than 3 megabyte. How many are there?

```bash
find . -name "*.fna" -size +3M | wc -l > fasta.txt
```
