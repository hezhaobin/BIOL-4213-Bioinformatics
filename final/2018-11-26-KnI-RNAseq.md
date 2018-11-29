---
title: 
author: Bin He
date: 
categories:
tags:
---

# Useful references and instructions for this problem
1. The RNA-seq tutorial on ICON produced by the Minnesota Supercomputing Institute, named "MSI_DGE_Galaxy_Human_2017_Spring.pdf"

2. [Galaxy Tutorial](https://galaxyproject.github.io/training-material/topics/transcriptomics/tutorials/ref-based/tutorial.html). This problem is developed based on this site.

3. [Brooks _et al_., 2011, Conservation of an RNA regulatory map between _Drosophila_ and mammals](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3032923/)

**Important! Please read the following instructions regarding what need to be submitted for this question**

In addition to answering the questions in this problem, make sure that you share your history with me. In practice, when you have satisfactorily finished all the questions in this problem, I suggest that you create a new history so you can cleanup the sequence of steps. When you are satisfied with it, click the cog icon on the top of the history pane, and choose "share and publish". In the resulting page, choose "Share with a user" and type in "bin-he@uiowa.edu". Note, sharing your history with your classmates is considered academic misconduct and will result in serious consequences. If you don't share your history, the relevant points will be deducted.


# Introduction
This problem is built on the publication of [Brooks et al. 2011](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3032923/). Read the abstract and consult details in the paper if needed, and answer the following questions.

1. In a few sentences, describe the main research question/hypothesis, results and conclusions of the paper.

2. Describe the experimental setup, i.e. what are the samples being investigated, how many biological / technical replicates are there, and what type of libraries were prepared?

# Data preparation

The original data is available at NCBI Gene Expression Omnibus (GEO) under accession number GSE18508.

The raw RNA-seq reads have been extracted from the Sequence Read Archive (SRA) files and converted into FASTQ files. In the first part of this problem, we will use the files for 2 of the 7 samples. Later you will use all available data to perform differential gene expression analysis.

# Data upload

- Create a new history for this RNA-seq exercise called final-RNAseq
- Go to "Shared Data"->"Data Libraries/Galaxy Courses/RNA-Seq (on second page)"
- Select all files in the "input sequences" folder and use the "To History" button on the top to import them into the new history buffer you just created.
- Check (using the pencil icon next to each dataset) to make sure that the fastq files are of the correct type, i.e. "fastqsanger"
- Click on the name of each dataset and choose the "tag" function in the expanded screen. Add a hash tag to each dataset, following the rule "#LastName". For example, I would label all my datasets as "#He". Please be sure to do this. Otherwise your results will not belong to you at the time of grading.
- Now go back to the "RNA-seq" folder and enter the "annotation" folder. Import the "Drosophila_melanogaster.BDGP5.78.gtf" into history. Check and make sure that its datatype is "gtf", not "gff". If necessary, change the datatype and make sure to click the "change datatype" button on the top to implement the change.

# Data QC

Use FastQC to assess the quality of the data and discuss what you found. It may be helpful to "aggregate" all the FastQC results so you can compare the quality of them together. Learn about the "MultiQC" tool available in usegalaxy.eu. Briefly, select "FastQC" in the dropdown menu for "Which tool was used to generate logs", and choose "Raw data" for the type of FastQC output. Then in the data selection menu, hold down the Ctrl (Windows) or Command (Mac) key while doing multiple selection. You can also use "Shift" to select consecutive datasets. Use the output from MultiQC to answer the following questions:

1. What's the read length of each dataset?


1. Which datasets seem to have low quality, by what measure? Briefly explain what that measure means and how you will deal with that dataset (continue analyzing? discard? remedy?)



# Genome mapping

1. What is the purpose of genome mapping?




2. There are quite a few genome mapping softwares, some for general purposes while others specialized for particular applications. We have learned to use TopHat in the workshop. This time we will test a few different mapping software and compare their performance. The Galaxy suite we are using has at least three suitable programs, i.e. TopHat, HISAT2 and RNA STAR. You can find the usage for TopHat in the workshop tutorial, while the usage for RNA STAR is documented [here](https://galaxyproject.github.io/training-material/topics/transcriptomics/tutorials/ref-based/tutorial.html#mapping-1). HISAT2 is extremely fast and it's easy to use if you understood the basics of the other two.

    Your task here is to implement _TWO_ different programs to map the paired-end reads from sample GSM461177 (untreated_paired_chr4_R1 and R2). For all three methods, use the "built in reference genome" and select "Drosophila melanogaster: dm6". For RNA STAR, you will find the choice for "Gene model (gff3, gtf) file for spice junctions". Select the gtf file in your history named "Drosophila_melanogaster.BDGP5.78.gtf". For TopHat and HISAT2, this option is hidden. You need to ask for "full parameter settings" or "advanced options" and then look for the option for specifying junction model in its expanded menus, usually with keywords such as "junction" or "splice". Answer the following questions with your results

    a. What information does the GTF file provide that is important for mapping? What is a splice junction and how do programs deal with introns in higher eukaryotes?


    b. What percentage of reads were uniquely mapped by each method? What is the reason for the failure to map the rest of the reads?

# Counting (reads per transcript)

Now that we have the reads mapped back to the genome, unless we care about identifying SNPs between the sample and the reference genome, we will no longer concern ourselves with the actual _sequence_ of a read. Rather, we simply work with its _location_. Since in most cases, the length of a read is far smaller than a gene, we need to tally the total number of reads that map to a particular gene, a process called (feature) counting. Again there are many ways to achieve this goal. We will use the featureCount program to do this.

Follow the Galaxy tutorial and apply featureCounts to the mapped reads file (bam) you just generated. You can use the output from either of the two programs you have used.


