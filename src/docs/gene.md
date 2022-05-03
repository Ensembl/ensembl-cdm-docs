# Gene

The Gene data type contains the information to represents the concept of a Gene.  It is without a genomic location, but lists its GeneAlleles which do have genomic locations.
`Gene` has the following fields:

| Field                 | Type                | Description                         |
|-----------------------|---------------------|-------------------------------------|
| symbol                | string              | Short name
| alternative_symbols   | array of string     | List of alternative symbols
| gene_alleles   | array of [GeneAllele](./gene_allele.md)| Related Gene Alleles across Assemblies for the same species
| species   | [Species](./species.md)| Species for the gene.   

## Notes
1. alternative_symbols and alternative_names can be empty lists

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
