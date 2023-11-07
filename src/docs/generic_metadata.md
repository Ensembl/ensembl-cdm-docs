# GenericMetadata

### OntologyTermMetadata
OntologyTermMetadata is common across different types of [features](./features.md) and also exists on non-features, such as [Region](./region.md). It is an instance of [ExternalReferenceMetadata](./metadata.md).

### Examples

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


### BiologicalLocation
Biological Location metadata is an instance of [ExternalReferenceMetadata](./metadata.md).

```json
 {
    "accession_id": "SO:00001552",
    "value": "plasmid",
    "url": "http://sequenceontology.org/browser/current_release/term/SO:00001552",
    "source": {
        "id": "SO",
        "name": "Sequence ontology",
        "url": "sequenceontology.org",
        "description": "The Sequence Ontology is a set of terms and relationships used to describe the features and attributes of biological sequence."
    }
}

```