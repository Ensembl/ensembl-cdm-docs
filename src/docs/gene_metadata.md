# GeneMetadata

A [Gene](./gene.md) has the following metadata associated with it:

| Field          | Type                         | Notes
|----------------|------------------------------|-------------|
| symbol         | GeneSymbolMetadata or null   | See below
| biotype        | BiotypeMetadata              | See [GenericMetadata](./generic_metadata.md)


### GeneSymbolMetadata
`GeneSymbolMetadata` is an instance of [ExternalReferenceMetadata](./metadata.md).

| Field          | Type                 | Description                                     |
|----------------|----------------------|-------------------------------------------------|
| accession_id   | string or null       | Gene's identifier in an external database       |
| value          | string or null       | Gene's symbol from an extenral database         |
| url            | string or null       | URL for accessing the item in another resource  |
| source         | ExternalDB or null   | See [ExternalDB](./external_db.md)              |


```json
{
  "name": {
    "accession_id": "HGNC:1101",
    "value": "BRCA2",
    "url": "https://www.genenames.org/data/gene-symbol-report/#!/hgnc_id/HGNC:1101",
    "source": {
      "id": "HGNC",
      "name": "HGNC Symbol",
      "url": "https://www.genenames.org",
      "description": "HUGO Genome Nomenclature Committee"
    }
  }
}
```

### GeneBiotypeMetadata
`GeneBiotypeMetadata` is an instance of [ValueSetMetadata](./metadata.md):

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
