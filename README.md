# nf-core-pep example


Starting from an nf-core RNA-seq pipeline sample table
* original file: [samplesheet_test.csv](samplesheet_test.csv)

We convert this into a PEP, which divides the table into 'samples' (one row per sample), and 'subsamples' (for attributes with multiple entries belonging to one sample).

* PEP subsample table: [config.yaml](config.yaml)
* PEP sample table: [pep_samples.csv](pep_samples.csv)
* PEP subsample table: [pep_subsamples.csv](pep_subsamples.csv)

## Validate:

```
eido validate config.yaml -s http://schema.databio.org/pep/2.0.0.yaml
```

## Inspect

We're working on a way to export this in a processed form. For now can grab an individual sample in yaml format like this:

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


## Use derived attributes

We can go a step further and use a PEP modifier. For this sample table, we want to remove the hard-coded paths in the sample table so that it can be reused in a different computing environment that had the data locally, without having to change the sample table. Here, the sample table stays the same, but we change the subsample table like this:

* PEP subsample table: [config_derived_attrs.yaml](config_derived_attrs.yaml)
* PEP subsample table: [pep_subsamples_derived.csv](pep_subsamples_derived.csv)

The result of the processed PEP is the same as the above example:

```
eido validate config_derived_attrs.yaml -s http://schema.databio.org/pep/2.0.0.yaml
```

```
eido inspect config_derived_attrs.yaml -n WT_REP1
```

Same output as above:
```
Sample 'WT_REP1' in Project (/home/nsheff/code/incubator/nf-core-pep/config_derived_attrs.yaml)

sample_name:    WT_REP1
strandedness:   reverse
fastq_1:        https://raw.githubusercontent.com/nf-core/test-datasets/rnaseq/testdata/GSE110004/SRR6357070_1.fastq.gz, https://raw.githubusercontent.com/nf-core/test-datasets/rnaseq/testdata/GSE110004/SRR6357071_1.fastq.gz
fastq_2:        https://raw.githubusercontent.com/nf-core/test-datasets/rnaseq/testdata/GSE110004/SRR6357070_2.fastq.gz, https://raw.githubusercontent.com/nf-core/test-datasets/rnaseq/testdata/GSE110004/SRR6357071_2.fastq.gz
subsample_name: 0, 1

```
