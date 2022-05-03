# GeneAllele

The GeneAllele data type contains the information to represents a locus, the genomic region where a allele is located. It will have at least one Transcript data type.
`GeneAllele` has the following fields:

| Field                 | Type                | Description                         |
|-----------------------|---------------------|-------------------------------------|
| symbol                | string              | Short name
| name                  | string              | Name of the gene allele from a known nomenclature such as HGNC
| alternative_symbols   | array of string     | List of alternative symbols
| alternative_names     | array of string     | List of alternative names
| stable_id             | string              | A unique identifier for the gene
| version               | integer             | Version of the gene allele
| unversioned_stable_id | string              | Unversioned unique identifier for the gene allele
| type                  | string              | This is always `GeneAllele`
| metadata              | GeneAlleleMetadata        | See [feature_metadata](./feature_metadata.md) and [gene_allele_metadata](./gene_allele_metadata.md)
| sequence              | string              | Genomic sequence on the forward strand from the lowest 5' end coordinate to the highest 3' end coordinate
| slice                 | Slice               | Slice describing the coordinates of the gene allele
| transcripts           | array of Transcript | List of transcripts
| gene           | Gene or null | The [Gene](./gene.md) which the GeneAllele is derived from

## Notes
1. alternative_symbols and alternative_names can be empty lists

## Examples
```json
{
  "symbol": "BRCA2",
  "name": "BRCA2 DNA repair associated",
  "alternative_symbols": [
    "BRCC2",
    "FACD",
    "FAD",
    "FAD1",
    "FANCD",
    "FANCD1",
    "XRCC11"
  ],
  "alternative_names": [
    "Fanconi anemia, complementation group D1",
    "BRCA1/BRCA2-containing complex, subunit 2"
  ],
  "stable_id": "ENSG00000139618.15",
  "version": 15,
  "unversioned_stable_id": "ENSG00000139618",
  "type": "GeneAllele",
  "metadata": {...},
  "slice": {},
  "transcripts": [],
  "gene": {...}
}
```
