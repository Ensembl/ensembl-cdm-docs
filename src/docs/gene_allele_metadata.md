# GeneAlleleMetadata

A [GeneAllele](./gene_allele.md) has the following metadata associated with it:

| Field          | Type                               | Notes                                         |
|----------------|------------------------------------|-----------------------------------------------|
| name           | GeneAlleleNameMetadata or null     | See below                                     |
| function       | GeneAlleleFunctionMetadata or null | See below                                     |
| biotype        | BiotypeMetadata                    | See [GenericMetadata](./generic_metadata.md)  |


### GeneAlleleNameMetadata
`GeneAlleleName` metadata is an instance of [ExternalReferenceMetadata](./metadata.md). Due to issues with data availability, the fields in `GeneAlleleNameMetadata` have to be nullable.

| Field          | Type                 | Description                                      |
|----------------|----------------------|--------------------------------------------------|
| accession_id   | string or null       | GeneAllele's identifier in an external database  |
| value          | string or null       | Relevant information about the item              |
| url            | string or null       | URL for accessing the item in another resource   |
| source         | ExternalDB or null   | See [ExternalDB](./external_db.md)                                   |


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
`GeneAlleleFunctionMetadata` is an instance of [ExternalReferenceMetadata](./metadata.md). The information about the allele's function is provided by Uniprot.

```json
{
  "function": {
    "accession_id": "P78504"
    "value": "JAG1_HUMAN",
    "url": "https://www.uniprot.org/uniprotkb/P78504/entry",
    "source": {
      "id": "Uniprot",
      "name" : "Uniprot entry",
      "url" : "https://www.uniprot.org/",
      "description" : "UniProt is the world’s leading high-quality, comprehensive and freely accessible resource of protein sequence and functional information. "
    }
  }
}
```

### BiotypeMetadata
`GeneAlleleBiotypeMetadata` is an instance of [ValueSetMetadata](./metadata.md):

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
