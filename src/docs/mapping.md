# Mapping
The `Mapping` data structure describes a match between an Ensembl [feature](./feature.md) and a feature from an external database, e.g. Uniprot. It has the following fields:

| Field             | Type                                                              | Description |
|-------------------|-------------------------------------------------------------------|-------------|
| source            | ExternalDB                                                        | See [ExternalDB](./external_db.md)
| accession_id      | string                                                            | Unique identifier of the feature in the source database
| url               | string                                                            | Url for accessing the feature in the source database
| name              | string or null                                                    | Name of the feature
| relative_location | Location                                                          | Location within the product where the hit lands (see [Location](./location.md))
| hit_location      | Location                                                          | Location within the external feature that is matched to the product sequence (see [Location](./location.md))
| genomic_locations | array of [GenomicMappingLocation](./genomic_mapping_location.md)  | `Location` within the genomic space corresponding to the product sequence that matches the external feature
| score             | float or null                                                     | Analysis score asserting the presence of this match at this location
| evalue            | float or null                                                     | Expectation value for the presence of this match at this location


```json
{
  "source": {
    "id": ???,
    "name": "Uniprot",
    "description": null,
    "url": "https://www.uniprot.org/",
    "release": null
  },
  "accession_id": "P51587",
  "url": "https://www.uniprot.org/uniprot/P51587",
  "name": "Breast cancer type 2 susceptibility protein",
  "relative_location": {
    "start": 25,
    "end": 106,
    "length": 82
  },
  "hit_location": {
    "start": 2,
    "end": 80,
    "length": 79
  },
  "genomic_locations": [
    {
      "slice": { ... },
      "cigar_string": "..."
    }
  ],
  "score": ???,
  "evalue": ???,
}
```
