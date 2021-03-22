# nf-core-pep example

* original file: samplesheet_test.csv
* PEP sample table: `pep_samples.csv`
* PEP subsample table: `pep_subsamples.csv`

## Validate:

```
eido validate config.yaml
```

## Inspect

```
eido inspect config.yaml -n WT_REP1
```

```
Sample 'WT_REP1' in Project (/home/nsheff/code/incubator/nf-core-pep/config.yaml)

sample_name:    WT_REP1
strandedness:   reverse
fastq_1:        https://raw.githubusercontent.com/nf-core/test-datasets/rnaseq/testdata/GSE110004/SRR6357070_1.fastq.gz, https://raw.githubusercontent.com/nf-core/test-datasets/rnaseq/testdata/GSE110004/SRR6357071_1.fastq.gz
fastq_2:        https://raw.githubusercontent.com/nf-core/test-datasets/rnaseq/testdata/GSE110004/SRR6357070_2.fastq.gz, https://raw.githubusercontent.com/nf-core/test-datasets/rnaseq/testdata/GSE110004/SRR6357071_2.fastq.gz
subsample_name: 0, 1
```
