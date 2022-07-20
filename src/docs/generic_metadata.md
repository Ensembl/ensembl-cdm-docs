# GenericMetadata

### OntologyTermMetadata
Ontology term metadata is common across different types of features and also exists on non-features, such as [Region](./region.md). It is an instance of [ExternalReferenceMetadata](./metadata.md). An example would look as follows:

```json
{
  "accession_id": "SO:0000147",
  "value": "exon",
  "url": "www.sequenceontology.org/browser/current_release/term/SO:0000147",
  "source": {
    "id": "...",
    "name": "Sequence Ontology",
    "url": "www.sequenceontology.org",
    "description": "The Sequence Ontology..."
  }
}
```

### BiotypeMetadata
BiotypeMetadata is common across different types of features and is an instance of [ValueSetMetadata](./metadata.md).:

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
