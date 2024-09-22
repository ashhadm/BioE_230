# BioE_230

## Download data from NCBI and upload to Ibex

```bash
scp ncbi_dataset.zip ashhadm@ilogin.ibex.kaust.edu.sa:/home/ashhadm/in_class/

## Unzip files

```bash
unzip ncbi_dataset.zip

## Smallest and largest genome(output files attached)

```bash
cut -f 11 data_summary.tsv | sort -n | uniq -d | head -n 1 > small_genome.txt
cut -f 11 data_summary.tsv | sort -n | uniq -d | tail -n 1 > large_genome.txt
