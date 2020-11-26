# Feature metadata

A feature has various kinds of metadata associated with it. For different types of features, the set of fields in the `Metadata` data type may be different.

## Gene metadata

| Field          | Type                         | Description |
|----------------|------------------------------|-------------|
| name           | GeneNameMetadata or null     | see below
| function       | GeneFunctionMetadata or null | see below
| biotype        | GeneBiotypeMetadata          | see below


### GeneNameMetadata
Gene name metadata is, in essence, an `External Reference` (see) promoted to the metadata rank. One notable difference is that the instead of a `description` filed, it has a `value` field.

```json
{
  "name": {
    "accession_id": "...",
    "value": "...",
    "url": "...",
    "source": {
      "name": "...",
      "url": "...",
      "description": "..."
    },
    "assignment_method": {
      "type": "...",
      "description": "..."
    },
  }
}
```

### GeneFunctionMetadata

| Field  | Type       | Description |
|--------|------------|-------------|
| value  | string     | free-form text with gene function description
| url    | string     | link to the page with info about the function of the gene 
| source | ExternalDB | see ExternalDB

Gene function information is provided by Uniprot.

```json
{
  "function": {
    "value": "...",
    "url": "...",
    "source": {
      "name" : "...",
      "url" : "...",
      "description" : "..."
    }
  }
}
```

### GeneBiotypeMetadata

| Field       | Type       | Description |
|-------------|------------|-------------|
| id          | string     | identifier of the biotype
| label       | string     | short, pretty-printed label ready for display
| description | string     | brief definition of what is meant by this biotype
| url         | string     | link to the page for this biotype in Ensembl Glossary
| source      | ExternalDB | see ExternalDB

The source of the biotype metadata is Ensembl Glossary

```json
{
  "biotype": {
    "id": "protein_coding",
    "label": "Protein coding",
    "description": "Gene/transcript that contains an open reading frame (ORF).",
    "url": "https://www.ebi.ac.uk/ols/api/ontologies/ensemblglossary/terms?iri=http://ensembl.org/glossary/ENSGLOSSARY_0000026",
    "source": {
      "name": "...",
      "url": "...",
      "description": "..."
    }
  }
}
```
