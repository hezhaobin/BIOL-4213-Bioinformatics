---
title: Homework \#1 Unix
author: Bin He
date: 2018-08-19
---

## Extract information from a genome annotation file (.gff).

1. Go to `~/Documents/2018-Bioinformatics/`. Create a sub-directory called `homework-1`
1. Obtain the gff file by issuing the command `cp /homepage/bhe2/2018-Bioinfo/2018-08-19-hw1-dmel-genome.gff ./`
1. Use `head` to view the file. Notice that the beginning of the file contains a number of comment lines as indicated by the beginning "#" sign. The remaining lines contain genomic annotation information, with each row corresponding to one "feature", e.g. protein coding gene or tRNA.
1. Now use the tools you've learned in class to identify the categories of unique features (this information is contained in the 3rd column of the file) and count the instances for each category, such as below

        xxx tRNA
        xxx protein-coding gene

## Testing knowledge of:
1. Navigate directories
1. Copy, move, create and delete files
1. Know how to use programs such as `head`, `grep`, `cut`, `sort`, `uniq`
