# Assembly metadata

An [Assembly](./assembly.md) has the following metadata associated with it:

| Field          | Type                                                 |
|----------------|------------------------------------------------------|
| samples        | Array of AssemblySampleMetadata                      |

 
### AssemblySampleMetadata
Assembly sample metadata is a list of [ExternalReferenceMetadata](./metadata.md). It provides references to the sample data related to the assembly which are held in the nucleotide archives.

| Field          | Type                 | Description                                       |
|----------------|----------------------|---------------------------------------------------|
| accession_id   | string               | Sample's identifier in an external database       |
| value          | string or null       | name of the sample                                |
| url            | string or null       | url for accessing the item in another resource    |
| source         | ExternalDB or null   | see [ExternalDB](./external_db.md)                |


```json
 {
    "accession_id": "SAMEA7520487",
    "value": "930bfae7-24c4-4e78-ad3c-6b863cc34ce2-dtol-specimen",
    "url": "https://www.ebi.ac.uk/ena/browser/view/SAMEA7520487",
    "source": {
        "id": "ENA",
        "name": "European Nucleotide Archive",
        "url": "https://www.ebi.ac.uk/ena",
        "description": "The European Nucleotide Archive (ENA)"
    }
}

```