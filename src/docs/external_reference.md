# External Reference

The `External Reference` data type represents a reference to a database outside of Ensembl. It has the following fields:

| Field             | Type             | Description |
|-------------------|------------------|-------------|
| accession_id      | string           | item's identifier in an external database
| name              | string           | item name
| description       | string or null   | additional information about the item
| url               | string or null   | url for accessing the item in another resource
| assignment_method | AssignmentMethod | see [AssignmentMethod](./assignment_method.md)
| source            | ExternalDB       | see [ExternalDB](./external_db.md)


## Note
`accession_id` of a given reference is not guaranteed to be unique

## Examples

1. With populated urls:

    ```json
    {
      "accession_id": "NM_001374244",
      "name": "NM_001374244.1",
      "description": null,
      "assignment_method": {
        "type": "DIRECT",
        "description": "A reference made by an external resource of annotation to an Ensembl feature that Ensembl imports without modification"
      },
      "url": "https://www.ncbi.nlm.nih.gov/protein/NM_001374244",
      "source": {
        "id": "RefSeq_mRNA",
        "name": "RefSeq mRNA",
        "description": null,
        "url": "https://www.ncbi.nlm.nih.gov/projects/RefSeq/",
        "release": null
      }
    }
    ```

2. With empty urls:

    ```json
    {
      "accession_id": "ENST00000288602.11",
      "name": "ENST00000288602.11",
      "description": null,
      "assignment_method": {
        "type": "COORDINATE_OVERLAP",
        "description": "A reference inferred from annotation of the same locus as a feature in Ensembl. Mostly relevant when comparing annotation between assemblies with different sequences than Ensembl for the same species"
      },
      "url": null,
      "source": {
        "id": "UCSC",
        "name": "UCSC Stable ID",
        "description": null,
        "url": null,
        "release": null
      }
    }
    ```
