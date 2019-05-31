---
layout: tutorial_page
permalink: /BiCG_2019_Module8_Lab
title: BiCG 2019 Module 8 Lab
header1: Workshop Pages for Students
header2: Bioinformatics for Cancer Genomics 2019
image: /site_images/CBW_cancerDNA_icon-16.jpg
home: https://bioinformaticsdotca.github.io/BiCG_2019
description: BiCG 2019 Module 8 Lab - Gene Expression
author: Florence Cavalli
modified: May 30th, 2019
---

# Lab Module 8 - Gene Expression

This lab is designed to provide an introduction into Somatic Nucleotide Variation detection using two common programs: [Strelka](https://academic.oup.com/bioinformatics/article-lookup/doi/10.1093/bioinformatics/bts271) and [MuTect](http://www.nature.com/nbt/journal/v31/n3/full/nbt.2514.html). This lab will also go over simple annotation of the files using [Annovar](http://annovar.openbioinformatics.org/en/latest/) and manipulation of vcf files using [SnpEff](http://snpeff.sourceforge.net/SnpEff_manual.html)

## Setup

First login into the server, and then enter the workspace directory:

```
cd ~/workspace
```

In order to keep our files in one location, we're going to create a new directory for this module and enter it:

```
mkdir Module7_snv
cd Module7_snv
```

Now to ease the use of commands that will follow, we're going to set some environment variables. These variables will stand in for the directories where our softwares of interest are location.

**Environment variables are only temporary. This means that once you log out of the server, these variables will be erased and must be reset if you'd like to use them again.**

Now we'll set out environment variables for MuTect and SnpEff (which will be used for processing the outputs from the callers):

```
JAVA_6_DIR=/home/ubuntu/CourseData/CG_data/Module7/install/java/jre1.6.0_45/bin
MUTECT_DIR=/home/ubuntu/CourseData/CG_data/Module7/install/mutect
SNPEFF_DIR=/usr/local/snpEff
ANNOVAR_DIR=/home/ubuntu/CourseData/CG_data/Module7/install/annovar
STRELKA_DIR=/home/ubuntu/CourseData/CG_data/Module7/install/strelka/bin/
```

## Linking the Sequencing and Referencing Data

For this lab module, we'll be using exome data on the HCC1395 breast cancer cell line. The tumour and normal bams have already been processed and placed on the server. So we'll create a soft link to the directory that it's stored. We'll also create a soft link to where the reference genome is stored, as well as a folder we'll use later on in the lab:

```
ln -s /home/ubuntu/CourseData/CG_data/Module7/HCC1395
ln -s /home/ubuntu/CourseData/CG_data/Module7/ref_data
ln -s /home/ubuntu/CourseData/CG_data/Module7/snv_analysis
```

For this lab we're going to limit our analysis to just the 7MB and 8MB region of chromosome 17 to ensure processing occurs quickly. The files we'll be focusing on can be viewed using the following command:

```
ls HCC1395/HCC1395_exome*.17*
```
