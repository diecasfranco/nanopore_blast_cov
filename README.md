# Nanotax
Nanotax is intended to produce a table with both **contig information** and the corresponding **taxonomy** for output contigs from Nanopore assembliers (e.g. [Canu](https://github.com/marbl/canu), [Flye](https://github.com/fenderglass/Flye)) 

**contig information** includes contig ID (**#ID**), average coverage (**Avg_fold**), contig length (**Length**) and GC content (**Read_GC**). **taxonomy** includes results from blastn (**blastn**), and/or results from blastx (**blastx**), and/or final taxonomy (**Taxonomy**) based on blastn and blastx. 

Nanotax takes three files as input: contigs in FASTA format, nanopore reads in FASTQ format, and customized nucleotide database in FASTA format. if customized protein datase (in FASTA format) was also provided, blastx (**blastx**) and final taxonomy (**Taxonomy**) will be added to the final table.

Nanotax runs in three steps: 
* Retrieving taxonomy of contigs by blastn (and blastx if protein database was provided)
* Mapping reads onto contigs and calculating basic contig information
* Joining contig information and taxonomy to produce the final table

## Software requirement
* Python 3
* [NCBI blast v2.11.0+](https://blast.ncbi.nlm.nih.gov/Blast.cgi?PAGE_TYPE=BlastDocs&DOC_TYPE=Download)
* [Minimap2](https://github.com/lh3/minimap2)
* [pileup.sh](https://github.com/BioInfoTools/BBMap/blob/master/sh/pileup.sh)

## Usage
```
usage: Nanotax.py [-h] [-f FASTA] [-q FASTQ]
                             [-db_nucl DATABASE_NUCL] [-db_prot DATABASE_PROT]
                             [-o OUTPUT_DIR] [-c Number of Cores]

nanopore

optional arguments:
  -h, --help            show this help message and exit
  -f, --fasta
                        the path to the fasta file/folder
  -q, --fastq
                        the path to the fastq file/folder
  -db_nucl, --database_nucl
                        the path to the nuclotide database
  -db_prot, --database_prot
                        the path to the protein database
  -o, --output_dir
                        output directory name
  -c, --cores
                        The number of CPU cores the script will use (default =
                        max number of CPUs available)
```

## Additional information
This script was developed by [Diego Castillo Franco](https://github.com/diecasfranco) and [Junchen Deng](https://github.com/junchen-deng) in Feburary 2021. 

## Upcoming features
* Allowing analysis of short reads, i.e. illumina 
