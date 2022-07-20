# SequenceFamily

`SequenceFamily` references the original provider of the data about this ([protein](./protein_product.md) or [rna](./rna_product.md)) family. It consists of the following fields:

| Field        | Type           | Description                                            |
|--------------|----------------|--------------------------------------------------------|
| source       | ExternalDB     | See [ExternalDB](./external_db.md) in the documentation
| accession_id | string         | Identifier of the family in the source database
| name         | string         | Name of the family
| description  | string or null | Description of the family
| url          | string or null | URL for accessing the family in the source database

## Examples

```json
{
  "source": {
    "id": "pfam",
    "name": "Pfam",
    "description": null,
    "url": "https://pfam.xfam.org",
    "release": 34
  },
  "accession_id": "PF00634",
  "name": "BRCA2 repeat",
  "description" : "...",
  "url": "https://pfam.xfam.org/family/PF00634"
}
```
