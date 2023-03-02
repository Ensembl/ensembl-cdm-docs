# GenericMetadata

### OntologyTermMetadata
OntologyTermMetadata is common across different types of [features](./features.md) and also exists on non-features, such as [Region](./region.md). It is an instance of [ExternalReferenceMetadata](./metadata.md).


| Field           | Type | Description            |
|-----------------|-------------------------------|------------------------------------------------------------|
| accession_id    | string                        | Accession ID of Ontology term
| value           | string                        | Textual representation of the Ontology term
| url             | string                        | URL for accessing the item in another resource
| source          | ExternalDB or null            | See [ExternalDB](./external_db.md)
| evidence_method | AssignmentMethod or null      | Describes how the ontology term was assigned
| evidence_source | Source or null                | Source of the ontology term assignment 
	
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
  },

  "evidence_method" :{
    "type": "HDA",
    "description": "High throughput direct assay"
  },
  "evidence_source": {
    "id": "...",
    "name": "UniProt",
    "url": "www.uniprot.org",
    "description": "The Sequence Ontology..."
  }
}
```
