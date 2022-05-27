# Transcript metadata

A [Transcript](./transcript.md) has the following metadata associated with it:

| Field          | Type                                    |
|----------------|-----------------------------------------|
| function       | TranscriptFunctionMetadata or null      |
| gencode_basic  | TranscriptGencodeBasicMetadata or null  |
| canonical      | TranscriptCanonicalMetadata             |
| mane           | TranscriptManeMetadata or null          |
| tsl            | TranscriptTSLMetadata                   |
| appris         | TranscriptApprisMetadata                |
| biotype        | TranscriptBiotypeMetadata               |

### TranscriptFunctionMetadata
Like gene function metadata, transcript function metadata is an instance of [XrefMetadata](./metadata.md). The information about gene function is provided by Uniprot.

```json
{
  "function": {
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

### TranscriptBiotypeMetadata
Like gene biotype metadata, transcript biotype metadata is an instance of [ValueSetMetadata](./metadata.md). It will likely have a different definition from gene biotype metadata, necessitating a different accession_id.

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

### TranscriptGencodeBasicMetadata
Transcript gencode basic metadata is an instance of ValueSetMetadata:


```json
{
  "gencode_basic": {
    "accession_id": "gencode_basic.true",
    "value": "true",
    "label": "GENCODE Basic",
    "definition": "Gene loci with at least one protein coding transcript.",
    "description": "???"
  }
}
```

Note: transcript gencode basic metadata is only applicable for human and mouse transcripts.

### TranscriptCanonicalMetadata
There is always one — and only one — transcript among gene transcripts that is designated as canonical. The transcript canonical metadata is an instance of ValueSetMetadata:


```json
{
  "canonical": {
    "accession_id": "canonical_transcript.true",
    "value": "true",
    "label": "Ensembl canonical",
    "definition": "???",
    "description": "???"
  }
}
```

_To be determined:_ whether the transcript canonical metadata will also need to include an `evidence` field.

### TranscriptManeMetadata
Transcript MANE metadata is an instance of ValueSetMetadata.

```json
{
  "mane": {
    "accession_id": "mane.select",
    "value": "select",
    "label": "MANE Select",
    "definition": "Gene loci with at least one protein coding transcript.",
    "description": "???",
    "ncbi_transcript": {
      "id": "NM_001374244",
      "url": "https://www.ncbi.nlm.nih.gov/protein/NM_001374244"
    }
  }
}
```

Notice that it has a custom `ncbi_transcript` field.

### TranscriptTSLMetadata
Transcript TSL metadata is an instance of ValueSetMetadata.

```json
{
  "tsl": {
    "accession_id": "tsl.one",
    "value": "1",
    "label": "TSL:1",
    "definition": "All splice junctions of the transcript are supported by at least one non-suspect mRNA.",
    "description": "???"
  }
}
```

### TranscriptApprisMetadata
Transcript APPRIS metadata is an instance of ValueSetMetadata.

```json
{
  "appris": {
    "accession_id": "appris.alternative-one",
    "value": "alternative1",
    "label": "APPRIS alternative:1",
    "definition": "Candidate transcript model that is conserved in at least three tested species.",
    "description": "???"
  }
}
 ```

===

## Prospective transcript metadata
Transcript metadata that is expected to be added in the future.

### TranscriptGencodePrimaryMetadata
Transcript gencode primary metadata is an instance of ValueSetMetadata:


```json
{
    "gencode_primary": {
      "accession_id": "gencode_primary.true",
      "value": "true",
      "label": "GENCODE Primary",
      "definition": "Gene loci with at least one protein coding transcript.",
      "description": "???",
    },
}
```

_To be determined:_  whether the transcript gencode primary metadata will also include a `reasons` field containing reasons for inclusion of this transcript in the gencode primary category.

### TranscriptExonicOverlapSameStrandMetadata
Transcript APPRIS metadata is an instance of ValueSetMetadata. Note the presence of the additional `associated_features` field.

```json
{
  "exonic_overlap_same_strand": {
    "accession_id": "biotype_additional_attribute.exonic_overlap_same_strand",
    "value": "exonic_overlap_same_strand",
    "label": "Exonic overlap with another transcript (same strand)",
    "definition": "Exonic overlap (same strand) with another Ensembl/GENCODE transcript",
    "associated_features": [
      {
        "type": "Gene",
        "stable_id": "ENSG"
      }
    ]
  }
}
```
