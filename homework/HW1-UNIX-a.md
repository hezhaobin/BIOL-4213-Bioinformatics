---
title: Bioinformatics Homework \#1 UNIX
---

# Extract information from a genome annotation file (.gtf).
**Due September 3rd**

## Prepare data
1. Go to `~/Documents/2018-Bioinfo/`. 
1. Create a sub-directory called `homework-1`
1. Obtain the gtf file by issuing the command 
   ```bash
   wget ftp://ftp.ensembl.org/pub/release-93/gtf/homo_sapiens/Homo_sapiens.GRCh38.93.gtf.gz
   gunzip Homo_sapiens.GRCh38.93.gtf.gz # will take ~10 sec
   ```
1. Use the shell script to answer the following questions

## Questions
1. (2 pts) How large is the gtf file you just obtained (hint: check out the -h flag in the manual for ls)



1. (3 pts) What command would you use to view the first 5 lines of the file, and what did you learn about this annotation file (use natural language to explain what you understand from those 5 lines).



1. (2 pts) How many lines in this file are comments (start with a "#")? Write down the answer and the command you used to obtain it.



1. (3 pts) What command would you use to view the last 5 lines of the file? How can you highlight the word "gene_name" in those lines and what gene name did you see?



1. (2 pts) What command can you use to view the content of the file with control (namely, you can scroll up and down), and how can you make each row be displayed in one screen line, with the overflow cutoff rather than wrapped around?



1. (2 pts) How can you use `grep` to "remove" the comment lines in order to view the actual annotations with the command above? Write down the command (hint: use pipe)



1. (2 pts) How many genes are there in this build of the human genome? (hint: the third column of the file indicates the type of the feature. Use grep to select only those that match "gene")? Write down the answer and the command you used to obtain it.

    Now let's pick a gene and learn a bit more about it. Please refer to the table below to determine which gene you will be looking up

1. (4 pts) Write down the command you will use to do the following: 1) select all lines that contain the gene name; 2) then select those lines from the last step that contain the word "protein_coding"; 3) finally write the output to a file named "my_gene.txt" and 4) report the total number of lines in this file.  (hint: use `grep` twice). 



1. (4 pts) Looking only at those lines where the second column says "ensembl_havana", answer the following questions
    a. (1 pts) Which chromosome is this gene on? (Note where do you get this information)
    a. (1 pts) How long is this gene?
    a. (1 pts) How many exons are there?
    a. (1 pts) How many coding exons there are 
    a. (bonus 2 pts) How many amino acids does this gene have? (explain how you calculated this)
    _note: the bonus points will be added to the total score until it reaches 24_


| Last name starts with | Gene name to look up |
|-----------------------|----------------------|
| A-E                   | APOE                 |
| H-J                   | FOXO1                |
| K-T                   | SOD1                 |

