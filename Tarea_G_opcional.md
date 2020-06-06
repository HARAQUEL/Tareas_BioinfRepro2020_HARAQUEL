### Raquel Hernández Austria
### Process_radtgas of Stacks


Stacks is a pipeline designed to work with any restriction-enzyme based data, that is, with data obtained from reduced representation 
techniques such as genotype-by-sequencing (GBS) or Restriction-site Associated DNA sequencing (RAD-seq). How does stacks work? Stacks
curate and assemble large numbers of short-read sequences from multiple samples; identifies loci in a set of individuals (either de novo 
or aligned to a reference genome), and then genotypes each locus; identify sequence polymorphisms and distinguish them from sequencing 
errors and; employs a Catalog to record all loci identified in a population and matches individuals to that Catalog to determine which 
haplotype alleles are present at every locus in each individual. 

The number of stages (6) is greater when we perform a de novo analysis than a reference-based analysis (3). 
The six major stages of the novo analysis are: 

**1**. Demultiplexed and cleaned the reads with **process_radtags** program. **NOTE**: In my project, I only made this stage.

**2**. Build loci with **ustacks**.

**3**. Create the catalog of loci with **cstacks**.

**4**. Match against the catalog with **sstacks**. 

**5**. Assemble and merge paired-end contigs, call variant sites in the population and genotypes in each sample with **gstacks** program.

**6**. Filter data, calculate population genetics statistics, and export a variety of data formats with **populations** program.

The three major stages of the reference-based analysis are: 1) **process_radtags** program, is executed as in a de novo analysis; 
2) read in aligned reads to assemble loci (and genotype them as in a de novo analysis) with the gstacks program, and 3) **populations**
program is executed. 

### How does process_radtags work?

To demultiplex the raw data to recover the individual samples in the Illumina library, and to discard sequencing reads of low quality 
considering the **Phred quality score** provided in the FASTQ files.

*Bioinformatic considerations: 

-You must consider if your data are single-end or paired-end Illumina sequencing (process_radtgas works with both options). 

-You can supply a list of barcodes, or indexes, to process_radtags in order for it to demultiplex your samples; you can supply the 
restriction enzyme used to construct the library too.

The output of the **process_radtags** if you are processing single-end will be one file per barcode into the output directory you specify. 
If the data do not have barcodes, then the file will retain its original name. If you are processing paired-end reads, you will get four 
files per barcode: two for the single-end read and two for the paired-end read.

What information do you need mentioned in methods and results section?

*Method:* 
The quantity of bases pairs that you are trimmed.

*Results:* 
The number of reads obtained after demultiplexing.

The information about Stacks and process_radtgas was obtained from Catchen *et al*. (2011) and Catchen *et al*. (2013).

**References:**

J. Catchen, P. Hohenlohe, S. Bassham, A. Amores, and W. Cresko. Stacks: an analysis tool set for population genomics. Molecular Ecology. 2013.

J. Catchen, A. Amores, P. Hohenlohe, W. Cresko, and J. Postlethwait. Stacks: building and genotyping loci de novo from short-read sequences. 
G3: Genes, Genomes, Genetics, 1:171-182, 2011. 
