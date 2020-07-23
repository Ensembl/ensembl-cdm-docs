# Gene

The Gene data type contains the information to represents a locus, the genomic region where a gene is located.
`Gene` has the following fields:
| Field               | Type            | Description                         |
|---------------------|-----------------|-------------------------------------|
| symbol              | string          | Short name
| name                | string          | Name of the gene from a known nomenclature such as HGNC
| alternative_symbols | array of string | List of alternative symbols
| alternative_names   | array of string | List of alternative names

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
  ]
}
