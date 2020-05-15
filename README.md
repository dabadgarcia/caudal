[![Anaconda-Server Badge](https://anaconda.org/dabadgarcia/caudal/badges/latest_release_date.svg)](https://anaconda.org/dabadgarcia/caudal)

<br>

## Index  
  * [About](#about)
  * [Installation](#installation)
  	* [Install Miniconda](#install-miniconda)
	* [Install Caudal](#install-caudal)
  * [Usage](#usage)
  * [Metadata](#metadata)  
  * [Output](#output)
  * [Citation](#citation)
  * [License](#license)

<br>

## About

Caudal is a straightforward pipeline for the analysis of Whole Genome sequences directly from raw Oxford Nanopore Technologies data. It generates a final html report that can be opened in any web browser and easily shared between researchers.  

<br>

## Installation

CAUDAL has been developed as a [Conda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/) environment to make things easier. 

### Install Miniconda

[Miniconda](https://docs.conda.io/en/latest/miniconda.html) provides the [Conda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/) environment and package manager, and is the recommended way to install Caudal: 

```
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
conda update conda
```

### Install Caudal

Once you have [Miniconda](https://docs.conda.io/en/latest/miniconda.html) installed, run the following commands to install Caudal:

```
conda create -n caudal
conda activate caudal
conda install -c dabadgarcia caudal
```
<br>

## Usage
```
usage: caudal <options>

OBLIGATORY OPTIONS:
        -m/--metadata   Path to the file with the metadata regarding the samples
                        The file must have an specific organization for the program to work
                        If you don't have any or you would like to have an example or extra information,
                        please type:
                        /home/biotec/software/links/caudal example-metadata
        -o/--output     Path and name of the output directory

OTHER OPTIONS:
        --assembler     Select the assembler to use. Options available: 'flye', 'canu'
                        (default='flye')
        -c/--config     Path to the configuration file with the location of all dependencies
                        (default="/home/biotec/software/../files/config_file.txt")
        --citation      Show citation
        --filtering     Enables optional filtering with filtlong.
        -g/--genera     Type genera name to allow special analysis (default='none')
                        Options available: 'Escherichia', 'Salmonella'
        -h/--help       Show this help
        --hybrid        Performs an hybrid assembly with illumina reads (path to the files must be specified in the metadata)
        --no-mlst       Disable MLST analysis (default='0')
        --no-pangenome  Disable pangenome analysis (default='0')
        -r/--reference  Type path to reference genome (fasta, gbk) (default='none')
                        Reference will be used for contig ordering of the draft genome
        -t/--threads    Number of threads to use (default=1) <integer>
        --title         Path to a file containing the title in the project that will be used as title in the report
                        Avoid using special characters. CAUDAL will perform a default title if this option is not used
        -v/--version    Show version
        
```
<br>

Example:
```
caudal sample-metadata.tsv --output output_folder -t 32
```
<br>

## Metadata

A metadata text file is needed for CAUDAL to work by using the `-m/--metadata` option. This file will include all the information regarding the sample and requires an specific organization:  

	- Columns must be tab separated
	- First column must me called "Samples" and harbor samples names (avoid special characters)
	- Second column must be called "Reads" and harbor the path to the reads (either fastq or fastq.gz)
	- Third column must be called "Illumina_forward" and harbor the path to the R1 Illumina reads (either fastq or fastq.gz)
	- Fourth column must be called "Illumina_reverse" and harbor the path to the R2 Illumina reads (either fastq or fastq.gz)
	- Fith (and so on) columns are descriptive. They are no needed for the program but the information will appear in the report
          Add as much as you want.

<br>

If you type `caudal example-metadata`, a template file called `sample-metadata.tsv` will be created in your working directory. You can also download the file [here](https://dabadgarcia.github.io/caudal/sample-metadata.tsv).

<br>

## Output
Caudal stores every file generated during the analysis in three different directories, all of them included within the main output directory specified with the `-o/--output` option. 

Once the analysis is finished, Caudal summarizes the results in a interactive html report in your output directory. An example of the report file can be visualized [here](https://dabadgarcia.github.io/caudal/example_report.html).

<br>

## Citation

If you use Caudal before publication is released, please cite as:  
  
David Abad, Narciso M. Quijada and Marta Hernandez. Caudal. (2019) https://github.com/dabadgarcia/caudal

Users are also highly encouraged to cite all the software within Caudal.

<br>

## License
Caudal is a open-source software licensed under [GPLv3](https://github.com/dabadgarcia/caudal/blob/master/LICENSE).
