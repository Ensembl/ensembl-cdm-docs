# Gene

The `Gene` data type contains the information to represent the concept of a Gene.  It is without a genomic location, but lists its `GeneAlleles` which do have genomic locations.
`Gene` has the following fields:

| Field                 | Type                                    | Description                         |
|-----------------------|-----------------------------------------|-------------------------------------|
| external_id           | string or null                          | Identifier provided by external nomenclature committee (such as HGNC)
| symbol                | string or null                          | Short name provided by external nomenclature committee (such as HGNC)
| stable_id             | string                                  | A unique identifier for the gene
| version               | integer                                 | Version of the gene
| unversioned_stable_id | string                                  | Unversioned unique identifier for the gene
| alternative_symbols   | array of strings                        | List of alternative symbols
| type                  | string                                  | This is always `Gene`
| gene_alleles          | array of [GeneAllele](./gene_allele.md) | Related Gene Alleles across Assemblies for the same species
| species               | [Species](./species.md)                 | Species for the gene.   
| metadata              | GeneMetadata                            | See [feature_metadata](./feature_metadata.md) and [gene_metadata](./gene_metadata.md)


## Notes
1. `alternative_symbols` can be an empty list
2. `external_id` is the `accession_id` from [GeneSymbolMetadata](./gene_metadata.md)
2. `symbol` is the `value` from [GeneSymbolMetadata](./gene_metadata.md)

## Examples
```json
{
  "symbol": "BRCA2",
  "alternative_symbols": [
    "BRCC2",
    "FACD",
    "FAD",
    "FAD1",
    "FANCD",
    "FANCD1",
    "XRCC11"
  ],
  "type": "Gene",
  "gene_alleles": [{
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
    "metadata": { ... },
    "slice": { ... },
    "transcripts": [ ... ],
    "gene" : { ... }
  }],
  "species": {
    "scientific_name": "Homo sapiens",
    "ncbi_common_name": "human",
    "alternative_names": [],
    "taxon_id": 9606,
    "organisms": [ ... ]
  }
}
```
