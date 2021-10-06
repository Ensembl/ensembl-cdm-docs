# Transcript

The Transcript data type describes a operational unit of a gene. In a genomic context, transcripts consist of one or more exons, with adjoining exons being separated by introns. The exons/introns are transcribed and then the introns spliced out. Transcripts may or may not encode a protein. `Transcript` has the following fields:

| Field                       | Type                              | Description                         |
|-----------------------------|-----------------------------------|-------------------------------------|
| symbol                      | string                            | Short name
| relative_location           | Location                          | Location of the transcript in relation to the gene
| stable_id                   | string                            | A unique identifier for the transcript
| version                     | integer                           | Version of the transcript
| unversioned_stable_id       | string                            | Unversioned unique identifier for the transcript
| type                        | string                            | The value is always `Transcript`
| slice                       | Slice                             | Slice describing the coordinates of the transcript
| spliced_exons               | array of SplicedExon              | The ordered list of exons of the transcript
| introns                     | array of Intron                   | The ordered list of introns of the transcript
| product_generating_contexts | array of ProductGeneratingContext | see ProductGeneratingContext
| metadata                    | TranscriptMetadata                | See [feature_metadata](./feature_metadata.md)
| gene                        | Gene                              | The parent gene of the transcript, see Gene

## Examples
```json
{
  "symbol": "BRCA2",
  "relative_location": { ... },
  "stable_id": "ENST00000380152.7",
  "version": 7,
  "unversioned_stable_id":"ENST00000380152",
  "type": "Transcript",
  "slice": { ... },
  "spliced_exons": [],
  "introns": [],
  "product_generating_contexts": [],
  "metadata": { ... }
  "gene": { ... }
}
```
