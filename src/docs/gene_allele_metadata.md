# GeneAlleleMetadata

A [GeneAllele](./gene_allele.md) has the following metadata associated with it:

| Field          | Type                         |
|----------------|------------------------------|
| name           | GeneAlleleNameMetadata or null     |
| function       | GeneAlleleFunctionMetadata or null |
| biotype        | GeneAlleleBiotypeMetadata          |


### GeneAlleleNameMetadata
GeneAlleleName metadata is an instance of [XrefMetadata](./feature_metadata.md). Due to issues with data availability, the fields in gene name metadata have to be nullable.

| Field          | Type                 | Description                                   |
|----------------|----------------------|-----------------------------------------------|
| accession_id   | string or null       | item's identifier in an external database     |
| value          | string or null       | relevant information about the item           |
| url            | string or null       | url for accessing the item in another resource|
| source         | ExternalDB or null   | see ExternalDB                                |


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
    }
  }
}
```

### GeneAlleleFunctionMetadata
GeneAlleleFunctionMetadata is an instance of XrefMetadata. The information about gene allele function is provided by Uniprot.

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

### GeneAlleleBiotypeMetadata
GeneAlleleBiotypeMetadata is an instance of [ValueSetMetadata](./feature_metadata.md):

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
