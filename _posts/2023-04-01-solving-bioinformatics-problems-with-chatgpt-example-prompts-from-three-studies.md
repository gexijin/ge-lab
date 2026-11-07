---
layout: post
title: "Solving bioinformatics problems with ChatGPT: example prompts from three studies"
date: 2023-04-01 18:34:00 +0000
categories: ["AI"]
---

Steven Ge ([Twitter](https://twitter.com/StevenXGe), [LinkedIn](https://www.linkedin.com/in/steven-ge-ab016947/))

In this blog, I summarized the main results from three studies using ChatGPT in bioinformatics and computational biology.

![]({{ site.baseurl }}/assets/uploads/2023/04/040823_1550_Solvingbioi1.jpg)

*Figure 1. Molecular phylogeny using ChatGPT. Shue et al. 2023.*

#### 1. Empowering Beginners in Bioinformatics with ChatGPT

[Shue *et al.*](https://journal.hep.com.cn/qb/EN/10.15302/J-QB-023-0327) demonstrated an "iterative model for refining prompts that guide chatbots in generating code for bioinformatics data analysis tasks." To effectively use ChatGPT, it is crucial to engage in an iterative process. Users should paste error messages back into the chatbot to request fixes and refine their prompts as needed. Most significantly, this research demonstrates how ChatGPT can be integrated into teaching. Through iterative assessment, students develop their coding skills by evaluating the generated results. The proposed OPTIMAL model utilizes ChatGPT to enhance bioinformatics education by providing students with iterative mentoring and assessment, which improves their coding abilities and critical thinking in scientific data analysis.

**Example 1: Write R code to create a phylogenetic tree.**

***Define chatbot's behavior:** Act as an experienced bioinformatician proficient in R, you will write code with number of lines as minimal as possible. Reset the thread if asked to. Reply "YES" if understand.*

***Prompt:** You have a multiple alignment file named as tp53.clustal in ClustalW format. Please write R code that can load the file, calculate evolutionary distance, build a NJ tree, and visualize the phylogeny.*

**Example 2: Write BASH scripts for analyzing ChIP-Seq data.**

***Define chatbot's behavior:** Act as an experienced bioinformatician proficient in ChIP-Seq data analysis, you will assist me by writing code with number of lines as minimal as possible. Reset the thread if asked to. Reply "YES" if understand.*

***Prompt:** I have two fastq files in current folder from single-end sequencing of a ChIP-Seq library: ENCFF000AVS_1m.fastq.gz, and ENCFF000AVS_10m.fastq.gz. For each fastq file, align reads to the human reference genome, save to bam file, and then covert it to bigwig file. Tools to use: bowtie2, samtools, and deepTools. The index for bowtie2 is in the folder "../data/indx/bowtie2_whole_genome/" with "hg38" as the prefix. Use 24 CPU for the alignment. Please draft the code in bash.*

![]({{ site.baseurl }}/assets/uploads/2023/04/040823_1550_Solvingbioi2.png)

*Figure 2. Tips for using ChatGPT in computational biology. Lubiana et al. 2023*

#### 2. Ten Quick Tips for Harnessing the Power of ChatGPT/GPT-4 in Computational Biology

[Lubiana *et al*.](https://arxiv.org/ftp/arxiv/papers/2303/2303.16429.pdf) provide some tips for using ChatGPT and GPT-4 in computational biology.

**Tip 1. Embrace the Technology and Be Ready for Novelty**

**Tip 2. Improve Code Readability and Documentation**

*"Add explanatory comments to this code:"*

*"Rename the variables for clarity:"*

*"Render roxygen2 documentation for the function:"*

**Tip 3. Write Code Efficiently**

*"Extract functions for increased clarity:"*

*"Re-write and optimize this for loop:"*

*"Write a unit test for the following function and help me implement it:"*

Use ChatGPT plugin in VS Code or RStudio (GPTStudio).

**Tip 4. Use ChatGPT to Enhance Data Cleanup**

For small data: *"Act as a table. Add a new column with consistent labels to this dataset:"*

For large data, use GPT for [Google Sheets](https://workspace.google.com/marketplace/app/gpt_for_docs_sheets_slides/451400884190?gclid=Cj0KCQjwz6ShBhCMARIsAH9A0qXcZXk6-3orJRDX1PfrvfaDwg3AoGrEs4hziKWXz4qFW96Hzm8r9fEaAmLdEALw_wcB).

**Tip 5. Use ChatGPT to Improve Your Data Visualization**

*"Change my code to make the plot color-blind friendly:"*

**Tip 6. Use ChatGPT to Improve Your Writing**

*"Provide me some different versions of the following sentence:"*

*"Summarize this text in a 200-word conference abstract:"*

**Tip 7. Ensure You Understand - or Know How to Test - What it Generates**

**Tip 8. Learn the Basics of Prompt Engineering/Design**

*"ChatGPT, I'd like to learn about the use of GATK tools in bioinformatics. Could you provide a brief overview of GATK, its main applications, and some popular tools within the GATK suite that are commonly used in the field of bioinformatics? Please include any advantages and limitations associated with these tools."*

*Compared to "Tell me about GATK", "*This prompt is effective because it clearly states the context (bioinformatics), specifies the topic (GATK tools), outlines the desired information (overview, applications, popular tools, advantages, and limitations), and provides a concise and focused question for the AI to address."

**Tip 9. Consider the GPT API to Extend Your Applications**

**Tip 10. Don't Become Too Dependent on ChatGPT**

![]({{ site.baseurl }}/assets/uploads/2023/04/040823_1550_Solvingbioi3.png)

*Figure 3. Overall performance of LLMs in genomics data questions. Hou & Ji 2023.*

#### 3. GeneTuring tests GPT models in genomics

[Hou and Ji](https://www.biorxiv.org/content/10.1101/2023.03.11.532238v1) evaluated various GPT models for answering genomics questions. GeneTuring: a genomics QA database to evaluate GPT models, with New Bing outperforming others in reducing AI hallucinations. Focusing on incapacity awareness is critical to tackling false answers.

*"Convert ENSG00000149476 to official gene symbol."*

*"Does transcription factor RELA activate or repress gene IL10?"*

*"Which chromosome is RGS16 gene located on human genome?"*

*"Which gene is SNP rs983419152 associated with?"*

*"What is the gene ontology term associated with PARP3, APLF, TFIP11, HMGB1, RAD51, XRCC1?"*

#### Summary

- Debug or improve code **iteratively**.
- Provide context and be specific.
- New Bing is more factual.
