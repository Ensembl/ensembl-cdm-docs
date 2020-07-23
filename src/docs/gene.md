# Gene

The Gene data type contains the information to represents a locus, the genomic region where a gene is located. It will have at least one Transcript data type.
`Gene` has the following fields:
| Field               | Type            | Description                         |
|---------------------|-----------------|-------------------------------------|
| symbol              | string          | Short name
| name                | string          | Name of the gene from a known nomenclature such as HGNC
| alternative_symbols | array of string | List of alternative symbols
| alternative_names   | array of string | List of alternative names
| stable_id           | string          | A unique identifier for the gene
| version             | string          | Version of the gene
| type                | string          | The type describing functionality of the gene such as `protein_coding`
| so_term             | string          | Sequence Ontology accession describing the gene
| sequence            | string          | Genomic sequence on the forward strand from the lowest 5' end coordinate to the highest 3' end coordinate

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
  "stable_id": "ENSG00000139618",
  "version": "15",
  "type": "protein_coding",
  "so_term": "SO:0000010",
  "sequence": "AAGCTTTTGTAATTTTAAAAAATT"
}
```
