# Gene metadata

A [Gene](./gene.md) has the following metadata associated with it:

| Field          | Type                                                       |
|----------------|------------------------------------------------------------|
| name           | GeneNameMetadata or null                                   |
| function       | GeneFunctionMetadata or null                               |
| biotype        | GeneBiotypeMetadata                                        |
| ontology_terms | Array of [OntologyTermMetadata](./generic_metadata.md)     |


### GeneNameMetadata
Gene name metadata is an instance of [ExternalReferenceMetadata](./metadata.md) with additional fields: `assignment_method` and `assignment_score`.  Due to issues with data availability, the fields in gene name metadata have to be nullable (although at least one fields must be filled in).

| Field             | Type                        | Description                                                                                 |
|-------------------|-----------------------------|---------------------------------------------------------------------------------------------|
| accession_id      | string or null              | item's identifier in an external database                                                   |
| value             | string or null              | relevant information about the item                                                         |
| url               | string or null              | url for accessing the item in another resource                                              |
| source            | ExternalDB or null          | see [ExternalDB](./external_db.md)                                                          |
| assignment_method | AssignmentMethod or null    | See [AssignmentMethod](./assignment_method.md)                                              |
| assignment_score  | float or null               | A score (typically a percentage as a float) representing the certainty of the assignment    |


For standard gene name assignment

```json
{
  "name": {
    "accession_id": "HGNC:1101",
    "value": "BRCA2 DNA repair associated",
    "url": "https://www.genenames.org/data/gene-symbol-report/#!/hgnc_id/HGNC:1101",
    "source": {
      "id": "HGNC",
      "name": "HGNC Symbol",
      "url": "https://www.genenames.org",
      "description": "HUGO Genome Nomenclature Committee"
    },
    "assignment_method": {
      "type": "DIRECT",
      "name": null,
      "description": "A reference made by an external resource of annotation to an Ensembl feature that Ensembl imports without modification",
      "version": null
    },
    "assignment_score": null
  }
}
```

For gene name assignment via a machine learning algorithm

```json
{
  "name": {
    "accession_id": "HGNC:1101",
    "value": "BRCA2 DNA repair associated",
    "url": "https://www.genenames.org/data/gene-symbol-report/#!/hgnc_id/HGNC:1101",
    "source": {
      "id": "HGNC",
      "name": "HGNC Symbol",
      "url": "https://www.genenames.org",
      "description": "HUGO Genome Nomenclature Committee"
    },
    "assignment_method": {
      "type": "ENSEMBL_ML",
      "name": "Ensembl Machine Learning Gene Name assignment",
      "description": "Predicted using Ensembl Machine Learning Gene Name assignment method",
      "version": "VERT_NN_1"
    },
    "assignment_score": 1.0
  }
}
```


### GeneFunctionMetadata
Gene function metadata is an instance of XrefMetadata. The information about gene function is provided by Uniprot.

```json
{
  "function": {
    "accession_id": "...",
    "value": "...",
    "url": "...",
    "source": {
      "id": "...",
      "name" : "...",
      "url" : "...",
      "description" : "..."
    }
  }
}
```

### GeneBiotypeMetadata
Gene biotype metadata is an instance of [ValueSetMetadata](./metadata.md):

```json
{
  "biotype": {
    "accession_id": "biotype.gene_protein_coding",
    "value": "protein_coding",
    "label": "Protein coding",
    "definition": "Gene loci with at least one protein coding transcript.",
    "description": "???"
  }
}
```
### OntologyTermMetadata
This is a generic piece of metadata applicaplable to many different entities, and so is not prefixed with "Gene".  There may also be multiple onotology terms associated with a Gene and so this is presented as an array.
