# Feature metadata

A feature has various kinds of metadata associated with it. For different types of features, the set of fields in the `Metadata` data type may be different.

## Gene metadata

| Field          | Type                         | Description |
|----------------|------------------------------|-------------|
| name           | GeneNameMetadata or null     | see below
| function       | GeneFunctionMetadata or null | see below
| biotype        | GeneBiotypeMetadata          | see below


### GeneNameMetadata
Gene name metadata is, in essence, an `External Reference` (which see) promoted to the metadata rank. One notable difference is that it doesn't have a `name` field, and instead of the `description` filed, it has the `value` field.

| Field             | Type             | Description |
|-------------------|------------------|-------------|
| accession_id      | string           | item's identifier in an external database
| value             | string           | name of the gene
| url               | string or null   | url for this record in the naming authority
| assignment_method | AssignmentMethod | see AssignmentMethod
| source            | ExternalDB       | see ExternalDB

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

The source of the biotype metadata is Ensembl value set

| Field       | Type           | Description |
|-------------|----------------|-------------|
| id          | string         | accession id in Ensembl database of Value Sets
| label       | string         | short, pretty-printed label ready for display
| definition  | string         | succinct definition of the term
| description | string or null | optional longer description that can contain nuances

```json
{
  "biotype": {
    "id": "biotype.gene_protein_coding",
    "label": "Protein coding",
    "definition": "Gene loci with at least one protein coding transcript.",
    "description": "???"
  }
}
```
