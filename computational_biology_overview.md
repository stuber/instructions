# Bioinformatics Topics

- [Data Types:](#Data-Types)
  - FASTA
  - FASTQ
- [Read types:](#Read-types)
  - Short read:
    - Ilumina
    - Ion Torrent
  - Long read:
    - PacBio
    - Nanopore
- [Methods:](#Methods)
  - Assembly
  - Alignment
  - kmer analysis
  - BLAST
- [Data Sources:](#Data-Sources)
  - NCBI
    - BLAST databases
    - SRA, assembly and RefSeq
  - EMBL-EBI (ENA)
  - DNA Data Bank of Japan
  - Ensembl
  - Kraken databases
  - SNP databases
- [Graphical User Interfaces:](#Graphical-User-Interfaces)
  - Geneious
  - IGV
  - Krona graphs
  - Figtree
  - VS Code
  - Jupyter Lab
- [Linux:](#Linux)
  - Command-line
  - Ability to handle large files
  - Compute resources
- [Local compute:](#Local-compute)
  - Apple macOS
  - Windows
    - Linux subsystem
  - Storage
  - Memory
  - CPU cores
- [High Performance Computer (HPC):](#High-Performance-Computer)
  - Modules
  - Slurm Job Control
  - Terminal
  - Login node
  - Working node
  - Compute resources
- [File Transfer:](#File-Transfer)
  - Mounted drive
  - FTP client
- [Reporting:](#Reporting)
  - Excel summaries
  - Latex generated PDFs
- [Version control:](#Version-Control)
  - Git
  - GitHub
  - Pull request
- [Anaconda:]
- [Open source resources:](#Open-source-resources)

## Data Types:

### FASTA
- Text file representing sequence
- Format is two lines of a header starting with ">" followed by a line with sequence
- File can include one or many FASTA formated sequences
```
> sample 1
TATCCTGCGCTTA
```

### FASTQ
- Text file representing DNA sequence and quality of that sequence
- Format is four lines of a header starting with "@", sequence, line beginning with "+" and line coding the phred score of each base call
- Files are often very large and contain many individual reads
```
@uniq header
TATCCTGCGCTTA
+
BBFGHHEBHHEEF
```

## Read types:

Read length is the number of continuous bases seqeunced from a fragment of DNA.  Phred score is the logrithmic quality metric given for each base called.  A phred score of 10 says likely a 1/10 call is incorrect.  Phred score of 20, 1/100 call is wrong.  30, 1/1000, etc.

- Short reads: FASTQ read lengths less than 600 bases in length.
  - Illumina: Typically paired reads (sharing genome sequence within a short region) and providing the highest NGS phred quality scores with average phred values of greater than 30.  Notation for typical Illumina reads would be 2x150, paired reads each approximately 150 bases in length.
  - Ion Torrent: Typically single reads with benifits to direct sequencing of RNA viruses.  Average phred scores of 25.
- Long read: Reads greater than 1,000 with the expected goal of lenghts between 10-20kb.  FASTQ read file sizes are typically much larger than short read.
  - PacBio: Instrumentation and start up cost are more expensive than the Oxford Nanopore platform.  Also the DNA quanity requirements are higher.  However, PacBio sequence quality is higher.
  - Nanopore: A relatively inexpensive instrumentation upfront cost making it less of a risk to explore.  DNA quanity requirements are low.  Quality is low with phred scores between 10-15.

## Methods:

### Assembly
- Overlapping matching FASTQ read sequence are combined to make a single sequence formated as FASTA
- Metrics:
  - Number of contigs or scaffolds FASTQ reads assembled to.  If full representation of a genome is being assembled fewer the better.  For a bacterial genome it is expected to have fewer than 100 contigs.
  - Total length of assembly.  How does the total length compare to expected results?

### Alignment
- FASTQ reads are aligned to a known sequence.  This produces and alignment that can be used show difference between the FASTQ reads and known sequence.  Often these differences are stored in a variant call format (VCF) file.

### kmer analysis
- Short sequences of specific length are used to compare against other isolates.

### BLAST
- Basic Local Alignment Search Tool ([BLAST](https://blast.ncbi.nlm.nih.gov/Blast.cgi)) finds sequence similarity. It compares sequences to sequence databases and calculates statistical significance.

## Data Sources:

## Graphical user interfaces:

## Linux:

## Local compute:

## High performance computer:

## File tranfer:

## Reporting:

## Version control:

## Anaconda:
  
### Open source resources:

  - [Abricate](https://github.com/tseemann/abricate)
  - [AMRFinderPlus](https://www.ncbi.nlm.nih.gov/pathogens/antimicrobial-resistance/AMRFinder/)
  - [Anaconda](https://www.anaconda.com/)
  - [BBTools](https://jgi.doe.gov/data-and-tools/bbtools/)
  - [BCFTools](https://samtools.github.io/bcftools/)
  - [Bedtools](https://bedtools.readthedocs.io/en/latest/)
  - [Biopython](http://biopython.org/DIST/docs/tutorial/Tutorial.html)
  - [Bowtie](http://bowtie-bio.sourceforge.net/index.shtml)
  - [BLAST](https://blast.ncbi.nlm.nih.gov/Blast.cgi)
  - [Bracken](https://ccb.jhu.edu/software/bracken/)
  - [BrackenTools](https://github.com/jenniferlu717/Bracken)
  - [BWA](http://bio-bwa.sourceforge.net/)
  - [Canu](https://canu.readthedocs.io/en/latest/quick-start.html)
  - [Clustal](http://www.clustal.org/)
  - [FASTX](http://hannonlab.cshl.edu/fastx_toolkit/)
  - [Freebayes](https://github.com/freebayes/freebayes)
  - [GATK](https://gatk.broadinstitute.org/hc/en-us)
  - [IRMA](https://wonder.cdc.gov/amd/flu/irma/)
  - [Kraken2](https://ccb.jhu.edu/software/kraken2/)
  - [KrakenTools](https://github.com/jenniferlu717/KrakenTools)
  - [kSNP](https://sourceforge.net/projects/ksnp/)
  - [MAFFT](https://mafft.cbrc.jp/alignment/software/)
  - [MLST](https://github.com/tseemann/mlst)
  - [Mummer](https://mummer4.github.io/)
  - [Octoflu](https://github.com/flu-crew/octoFLU)
  - [PlasmidFinder](https://bitbucket.org/genomicepidemiology/plasmidfinder/src)
  - [Python](https://www.python.org/)
  - [RAxML](https://cme.h-its.org/exelixis/web/software/raxml/)
  - [Samtools](http://www.htslib.org/)
  - [SeqSero2](https://github.com/denglab/SeqSero2)
  - [Sistr](https://github.com/phac-nml/sistr_cmd)
  - [SPAdes](https://cab.spbu.ru/software/spades/)
  - [SRA Toolkit](https://www.ncbi.nlm.nih.gov/books/NBK158900/)
  - [vSNP](https://github.com/USDA-VS/vSNP)
