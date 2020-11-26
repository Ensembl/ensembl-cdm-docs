# Feature metadata

A feature has various kinds of metadata associated with it. For different types of features, the set of fields in the `Metadata` data type may be different.

## Gene metadata

| Field          | Type                                    | Description |
|----------------|-----------------------------------------|-------------|
| name           | TranscriptNameMetadata or null          | see below
| function       | TranscriptFunctionMetadata or null      | see below
| ccds           | TranscriptCCDSMetadata or null          | see below
| genecode_basic | TranscriptGenecodeBasicMetadata or null | see below
| canonical      | TranscriptCanonicalMetadata             | see below
| mane           | TranscriptManeMetadata or null          | see below
| tsl            | TranscriptTSLMetadata                   | see below
| appris         | TranscriptApprisMetadata                | see below
| biotype        | TranscriptBiotypeMetadata               | see below


### TranscriptNameMetadata
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

### TranscriptFunctionMetadata

| Field  | Type       | Description |
|--------|------------|-------------|
| value  | string     | free-form text with transcript function description
| url    | string     | link to the page with info about the function of the transcript 
| source | ExternalDB | see ExternalDB

Transcript function information is provided by Uniprot.

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

### TranscriptCCDSMetadata

| Field  | Type       | Description |
|--------|------------|-------------|
| value  | string     | ???
| url    | string     | ??? 
| source | ExternalDB | see ExternalDB

```json
{
  "ccds": {
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

### TranscriptGenecodeBasicMetadata

| Field  | Type       | Description |
|--------|------------|-------------|
| value  | string     | ???
| source | ExternalDB | see ExternalDB

```json
{
  "gencode_basic": {
    "value": true,
    "source": {
      "name": "...",
      "url": "...",
      "description": "..."
    }
  }
}
```

### TranscriptCanonicalMetadata

There is always one — and only one — transcript among gene transcripts that is designated as canonical.

| Field     | Type       | Description |
|-----------|------------|-------------|
| value     | boolean    | whether the current transcript is canonical
| evidence  | string     | one of a closed set of dictionary terms
| source    | ExternalDB | see ExternalDB

```json
{
  "canonical": {
    "value": true,
    "evidence": "...",
    "source": {
      "name": "...",
      "url": "...", 
      "description": "..."
    }
  }
}
```

### TranscriptManeMetadata

| Field     | Type       | Description |
|-----------|------------|-------------|
| value     | string     | accsession of refseq transcript
| type      | string     | either "plus" or "select"
| source    | ExternalDB | see ExternalDB

```json
{
  "mane": {
    "value": "...",
    "type": "plus",
    "source": {
      "name" : "...",
      "url": "...", 
      "description": "..."
    }
  }
}
```

### TranscriptTSLMetadata

| Field     | Type       | Description |
|-----------|------------|-------------|
| value     | integer    | ???
| source    | ExternalDB | see ExternalDB

```json
{
  "tsl": {
    "value": 1,
    "source": {
      "name" : "...",
      "url" : "...",
      "description": "..."
    }
  }
}
```

### TranscriptApprisMetadata
 
| Field     | Type       | Description |
|-----------|------------|-------------|
| value     | string     | ???
| source    | ExternalDB | see ExternalDB

```json
{
  "appris": {
    "value": "alternative1",
    "source": {
      "name" : "...",
      "url": "...", 
      "description": "..."
    }
  }
}
 ```

### TranscriptBiotypeMetadata

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
