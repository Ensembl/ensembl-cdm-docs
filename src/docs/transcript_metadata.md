# Transcript metadata

A [Transcript](./transcript.md) has the following metadata associated with it:

| Field          | Type                                    | Notes                                        |
|----------------|-----------------------------------------|----------------------------------------------|
| function       | TranscriptFunctionMetadata or null      | See below                                    |
| gencode_basic  | TranscriptGencodeBasicMetadata or null  | See below                                    |
| canonical      | TranscriptCanonicalMetadata             | See below                                    |
| mane           | TranscriptManeMetadata or null          | See below                                    |
| tsl            | TranscriptTSLMetadata                   | See below                                    |
| appris         | TranscriptApprisMetadata                | See below                                    |
| biotype        | BiotypeMetadata                         | See [GenericMetadata](./generic_metadata.md) |

### TranscriptFunctionMetadata
Like [GeneAlleleFunctionMetadata](./gene_allele_metadata.md), `TranscriptFunctionMetadata` is an instance of [ExternalReferenceMetadata](./feature_metadata.md). The information about the function is provided by Uniprot.

```json
{
  "value": "...",
  "url": "...",
  "source": {
    "id": "...",
    "name" : "...",
    "url" : "...",
    "description" : "..."
  }
}
```

### BiotypeMetadata
[BiotypeMetadata](./generic_metadata.md) is an instance of [ValueSetMetadata](./feature_metadata.md).

```json
{
  "accession_id": "biotype.transcript_protein_coding",
  "value": "protein_coding",
  "label": "Protein coding",
  "definition": "An mRNA that can be translated into a protein.",
  "description": "???"
}
```

### TranscriptGencodeBasicMetadata
`TranscriptGencodeBasicMetadata` is an instance of [ValueSetMetadata](./feature_metadata.md):


```json
{
  "accession_id": "gencode_basic.true",
  "value": true,
  "label": "GENCODE Basic",
  "definition": "Gene loci with at least one protein coding transcript.",
  "description": "???"
}
```

Note: `TranscriptGencodeBasicMetadata` is only applicable for human and mouse [transcripts](./transcript.md).

### TranscriptCanonicalMetadata
There is always one — and only one — transcript amongst the transcripts for a Gene that is designated as canonical. The `TranscriptCanonicalMetadata` is an instance of [ValueSetMetadata](./feature_metadata.md):


```json
{
  "accession_id": "canonical_transcript.true",
  "value": true,
  "label": "Ensembl canonical",
  "definition": "???",
  "description": "???"
}
```

_To be determined:_ whether the transcript canonical metadata will also need to include an `evidence` field.

### TranscriptManeMetadata
`TranscriptManeMetadata` is an instance of [ValueSetMetadata](./feature_metadata.md).

```json
{
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

```

Notice that it has a custom `ncbi_transcript` field.

### TranscriptTSLMetadata
`TranscriptTSLMetadata` is an instance of [ValueSetMetadata](./feature_metadata.md).

```json
{
  "accession_id": "tsl.one",
  "value": 1,
  "label": "TSL:1",
  "definition": "All splice junctions of the transcript are supported by at least one non-suspect mRNA.",
  "description": "???"
}

```

### TranscriptApprisMetadata
`TranscriptApprisMetadata` is an instance of [ValueSetMetadata](./feature_metadata.md).

```json
{
  "accession_id": "appris.alternative-one",
  "value": "alternative1",
  "label": "APPRIS alternative:1",
  "definition": "Candidate transcript model that is conserved in at least three tested species.",
  "description": "???"
}

 ```

---
---


## Prospective transcript metadata
Transcript metadata that is expected to be added in the future.

### TranscriptGencodePrimaryMetadata
`TranscriptGencodePrimaryMetadata` is an instance of [ValueSetMetadata](./feature_metadata.md):


```json
{
  "accession_id": "gencode_primary.true",
  "value": true,
  "label": "GENCODE Primary",
  "definition": "Gene loci with at least one protein coding transcript.",
  "description": "???",
}
```

_To be determined:_  whether the transcript gencode primary metadata will also include a `reasons` field containing reasons for inclusion of this transcript in the gencode primary category.

### TranscriptExonicOverlapSameStrandMetadata
`TranscriptExonicOverlapSameStrandMetadata` is an instance of [ValueSetMetadata](./feature_metadata.md). Note the presence of the additional `associated_features` field.

```json
{
  "accession_id": "biotype_additional_attribute.exonic_overlap_same_strand",
  "value": "exonic_overlap_same_strand",
  "label": "Exonic overlap with another transcript (same strand)",
  "definition": "Exonic overlap (same strand) with another Ensembl/GENCODE transcript",
  "associated_features": [
    {
      "type": "GeneAllele",
      "stable_id": "ENSG"
    }
    ]
  }
}

```
