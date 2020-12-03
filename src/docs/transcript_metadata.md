# Feature metadata

A feature has various kinds of metadata associated with it. For different types of features, the set of fields in the `Metadata` data type may be different.

## Transcript metadata

| Field          | Type                                    | Description |
|----------------|-----------------------------------------|-------------|
| function       | TranscriptFunctionMetadata or null      | see below
| gencode_basic  | TranscriptGencodeBasicMetadata or null  | see below
| canonical      | TranscriptCanonicalMetadata             | see below
| mane           | TranscriptManeMetadata or null          | see below
| tsl            | TranscriptTSLMetadata                   | see below
| appris         | TranscriptApprisMetadata                | see below
| biotype        | TranscriptBiotypeMetadata               | see below


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

### TranscriptGencodeBasicMetadata

| Field  | Type       | Description |
|--------|------------|-------------|
| value  | boolean    | indicates whether transcript belongs to the GENCODE Basic set

```json
{
  "gencode_basic": {
    "value": true,
  }
}
```

Note: is only applicable for human and mouse genes.

### TranscriptCanonicalMetadata

There is always one — and only one — transcript among gene transcripts that is designated as canonical.

| Field     | Type       | Description |
|-----------|------------|-------------|
| value     | boolean    | whether the current transcript is canonical
| evidence  | string     | one of a closed set of dictionary terms

```json
{
  "canonical": {
    "value": true,
    "evidence": "..."
  }
}
```

### TranscriptManeMetadata

| Field     | Type       | Description |
|-----------|------------|-------------|
| value     | string     | accession of refseq transcript
| type      | string     | either "plus" or "select"

```json
{
  "mane": {
    "value": "...",
    "type": "plus"
  }
}
```

### TranscriptTSLMetadata

| Field     | Type       | Description |
|-----------|------------|-------------|
| value     | integer    | transcript support level

```json
{
  "tsl": {
    "value": 1
  }
}
```

### TranscriptApprisMetadata
 
| Field     | Type       | Description |
|-----------|------------|-------------|
| value     | string     | label according to the APPRIS system

```json
{
  "appris": {
    "value": "alternative1"
  }
}
 ```

### TranscriptBiotypeMetadata

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
    "id": "biotype.transcript_protein_coding",
    "label": "Protein coding",
    "definition": "An mRNA that can be translated into a protein.",
    "description": "???"
  }
}
```
