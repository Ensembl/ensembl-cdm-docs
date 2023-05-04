# Region metadata

A [Region](./region.md) has the following metadata associated with it:

| Field                     | Type                                                      |
|---------------------------|-----------------------------------------------------------|
| synonyms                  | Array of RegionSynonymMetadata                            |
| ontology_terms            | Array of [OntologyTermMetadata](./generic_metadata.md)    |
| biological_locations      | Array of [BiologicalLocation](./generic_metadata.md)      |
 

### RegionSynonymMetadata
Region synonym metadata is an instance of [ExternalReferenceMetadata](./metadata.md). It details all of the synonyms available for a region.

| Field          | Type                 | Description                                       |
|----------------|----------------------|---------------------------------------------------|
| accession_id   | string or null       | item's identifier in an external database         |
| value          | string or null       | relevant information about the item               |
| url            | string or null       | url for accessing the item in another resource    |
| source         | ExternalDB or null   | see [ExternalDB](./external_db.md)                |


```json
 {
    "accession_id": "CM000675.2",
    "value": "CM000675.2",
    "url": "https://www.ncbi.nlm.nih.gov/nuccore/CM000675.2",
    "source": {
        "id": "INSDC",
        "name": "INSDC",
        "url": "https://insdc.org", 
        "description": "INSDC"
    }
}

```