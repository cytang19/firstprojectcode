# MIRUReader

## Description

Identify 24-locus MIRU-VNTR for *Mycobacterium tuberculosis* complex (MTBC) directly from long reads generated by Oxford Nanopore Technologies (ONT) and Pacific Biosciences (PacBio). Also work on assembled genome.

## Requirements

* Linux
* primersearch from [EMBOSS](http://emboss.sourceforge.net/download/)
* [*pandas*](https://pandas.pydata.org/) 
   * can be installed via conda `conda install pandas` or via PyPI `pip install pandas`
* [*statisctics*](https://pypi.org/project/statistics/)
   * can be installed via PyPI `pip install statistics`

## Installation

`git clone https://github.com/cytang19/MIRUReader.git`

## Usage example

For one sample analysis:
```
python /your/path/to/MIRUReader.py -r sample.fasta -p sampleID > miru.txt
```

For multiple samples analysis:
1. Create a mapping file (mappingFile.txt) that looks like:

    sample_001.fasta sample_001 \
    sample_002.fasta sample_002 \
    ...

2. Then run the program:
```
cat mappingFile.txt | while read -a line; do python /your/path/to/MIRUReader.py -r ${line[0]} -p ${line[1]}; done > miru.multiple.txt
```

## Output example

```
sample_prefix   0154    0424    0577    0580    0802    0960    1644    1955    2059    2163b   2165    2347    2401    2461    2531    2687    2996    3007    3171    3192    3690    4052    4156    4348
sample_001      2       4       4       2       3       3       3       2       2       5       4       4       4       2       5       1       6       3       3       5       3       7       2       3
```

Notes:
* The program is compatible to Python 2 and Python 3.
* Accepted reads file format includes '.fastq', '.fastq.gz', '.fasta', and '.fasta.gz'.
* The program output is a tab-delimited plain text which can be copied to or opened in Excel spreadsheet.
