# skills_test_2

This repository stores input files, example output files, and description of the problem which is designed to assist in the evaluation of computational skills of job candidates and prospective MSc/Ph.D. students.

## Problem description

Given a list of genetic variants in compressed Variant Call Format (VCF) files (one file per chromosome) and gene coordinates in compressed GENCODE GTF file, develop a command-line tool which for each variant finds:
  1. List of overlapping genes
  2. List of genes within +/-200000 base pairs from the variant
  3. Nearest gene

## Input data and formats

- Genetic variants are saved in compressed VCF files with the `.vcf.gz` suffix in the `input/` directory. The description of the VCF format can be found at [https://samtools.github.io/hts-specs/](https://samtools.github.io/hts-specs/). If you will find it useful for your solution, the corresponding index files for fast random access (`.tbi` suffix) are located in the same directory.
- Gene coordinates are saved in a compressed GENCODE GTF file `input/gencode.v38.annotation.gtf.gz`. The description of the GENCODE GTF format can be found at [https://www.gencodegenes.org/pages/data_format.html](https://www.gencodegenes.org/pages/data_format.html).

## Output format

The command-line tool must write results to the compressed VCF file. Specifically, for each genetic variant the following key-value pairs must be written into the `INFO` field:
1. `GENES_IN` - comma-separated list of identifiers (`gene_id` key from GENCODE GTF) of overlapping genes. If there are no overlapping genes, the empty value must be denoted with `.` symbol i.e. `GENES_IN=.`.
2. `GENES_200KB` - comma-separated list of identifiers (`gene_id` key from GENCODE GTF) of genes which are within +/-200000 base pairs from the variant. If there are no such genes, the empty value must be denoted with `.` symbol i.e. `GENES_200KB=.`. `GENES_200KB` is a superset of `GENES_IN`.
3. `GENE_NEAREST` - identifier (`gene_id` key from GENCODE GTF) of the nearest gene. If `GENE_IN` is not empty, then `GENE_NEAREST` must be empty. Empty value must be denoted with `.` symbol i.e. `GENE_NEAREST=.`.
An example of the output file can be found in `output/example.vcf.gz`.

## Requirements

To implement this command-line tool you may:
- use any scripting/programming language (or any combination of them) of your choice (e.g. Python, C/C++, Java, Perl, R, shell scripting)
- use any open-source library (e.g. for VCF reading/writing, relevant data structures and etc)

## Solution

Please, send us a single compressed archive which includes:
1. **README**. It should provide: (a) a list of all open-source software tools (and their versions) which were used; (b) any additional requirements for the operating system and/or system libraries; (c) any compilation instructions if such exists (d) detailed step-by-step description on how to run the tool.
3. **Source of your scripts/code**. Please include detailed comments in your source code. This will help us better understand your code.

**Don't send VCF output files!**

## Evaluation

The following will be evaluated:
1. The tool can be easily installed and run.
2. The tool uses data structures and algorithms adequate for the problem i.e. ensure reasonable running time and memory usage.
3. All requested INFO fields are present in the final output VCF files.
4. Values in the requested INFO fields in the final output VCF files are correct.

