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

| Field       | Type           | Description |
|-------------|----------------|-------------|
| accession_id| string         | accession id in Ensembl database of Value Sets
| label       | string         | short, pretty-printed label ready for display
| value       | boolean        | indicates whether transcript belongs to the GENCODE Basic set
| definition  | string         | succinct definition of the term
| description | string or null | optional longer description that can contain nuances


```json
{
  "gencode_basic": {
    "accession_id": "gencode_basic.true",
    "value": true,
    "label": "GENCODE Basic",
    "definition": "Gene loci with at least one protein coding transcript.",
    "description": "???"
  }
}
```

Note: is only applicable for human and mouse genes.

### TranscriptCanonicalMetadata

There is always one — and only one — transcript among gene transcripts that is designated as canonical.

| Field       | Type           | Description |
|-------------|----------------|-------------|
| accession_id| string         | accession id in Ensembl database of Value Sets
| label       | string         | short, pretty-printed label ready for display
| value       | boolean        | whether the current transcript is canonical
| definition  | string         | succinct definition of the term
| description | string or null | optional longer description that can contain nuances

```json
{
  "canonical": {
    "accession_id": "canonical_transcript.true",
    "value": true,
    "label": "Ensembl canonical",
    "definition": "???",
    "description": "???"
  }
}
```

_To be determined:_ whether there is a need for the "evidence" field

### TranscriptManeMetadata

| Field       | Type           | Description |
|-------------|----------------|-------------|
| accession_id| string         | accession id in Ensembl database of Value Sets
| label       | string         | short, pretty-printed label ready for display
| value       | string         | "select", "plus", "clinical"
| definition  | string         | succinct definition of the term
| description | string or null | optional longer description that can contain nuances

```json
{
  "mane": {
    "accession_id": "mane.select",
    "value": "select",
    "label": "MANE Select",
    "definition": "Gene loci with at least one protein coding transcript.",
    "description": "???"
  }
}
```

### TranscriptTSLMetadata

| Field       | Type           | Description |
|-------------|----------------|-------------|
| accession_id| string         | accession id in Ensembl database of Value Sets
| label       | string         | short, pretty-printed label ready for display
| value       | integer or null| transcript support level
| definition  | string         | succinct definition of the term
| description | string or null | optional longer description that can contain nuances


```json
{
  "tsl": {
    "accession_id": "tsl.one",
    "value": 1, // there is also a tslNA — would it be a null?
    "label": "TSL:1",
    "definition": "All splice junctions of the transcript are supported by at least one non-suspect mRNA.",
    "description": "???"
  }
}
```

### TranscriptApprisMetadata
 
| Field       | Type           | Description |
|-------------|----------------|-------------|
| accession_id| string         | accession id in Ensembl database of Value Sets
| label       | string         | short, pretty-printed label ready for display
| value       | string         | one of the seven possible APPRIS tags
| definition  | string         | succinct definition of the term
| description | string or null | optional longer description that can contain nuances

```json
{
  "appris": {
    "accession_id": "tsl.one",
    "value": "alternative1",
    "label": "APPRIS alternative:1",
    "definition": "Candidate transcript model that is conserved in at least three tested species.",
    "description": "???"
  }
}
 ```

### TranscriptBiotypeMetadata

The source of the biotype metadata is Ensembl value set

| Field       | Type           | Description |
|-------------|----------------|-------------|
| id          | string         | accession id in Ensembl database of Value Sets
| label       | string         | short, pretty-printed label ready for display
| value       | string         | a string intended for programmatic use by consumer
| definition  | string         | succinct definition of the term
| description | string or null | optional longer description that can contain nuances

```json
{
  "biotype": {
    "accession_id": "biotype.transcript_protein_coding",
    "value": "protein_coding",
    "label": "Protein coding",
    "definition": "An mRNA that can be translated into a protein.",
    "description": "???"
  }
}
```
