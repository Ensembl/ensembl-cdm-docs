# ProteinProductMetadata

A [ProteinProduct](./protein_product.md) has the following metadata associated with it:

| Field          | Type                         |
|----------------|------------------------------|
| alphafold      | AlphafoldMetadata or null    |


### AlphafoldMetadata
`AlphafoldMetadata` is an instance of [ExternalReferenceMetadata](./metadata.md).

| Field          | Type                 | Description                                   |
|----------------|----------------------|-----------------------------------------------|
| accession_id   | string               | item's identifier in an external database     |
| value          | string               | relevant information about the item           |
| url            | string               | url for accessing the item in another resource|
| source         | ExternalDB           | see [ExternalDB](./external_db.md)                                |

## Examples
```json
{
  "alphafold": {
    "accession_id": "AF-P63151-F1.A",
    "value": "AF-P63151-F1.A",
    "url": "https://alphafold.ebi.ac.uk/entry/P63151",
    "source": {
      "id": "Alphafold",
      "name": "Alphafold",
      "url": "https://alphafold.ebi.ac.uk/",
      "description": "AlphaFold Protein Structure Database"
    }
  }
}
```
