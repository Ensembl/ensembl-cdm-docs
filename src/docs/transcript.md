# Transcript

The Transcript data type describes a operational unit of a gene. In a genomic context, transcripts consist of one or more exons, with adjoining exons being separated by introns. The exons/introns are transcribed and then the introns spliced out. Transcripts may or may not encode a protein. `Transcript` has the following fields:

| Field                       | Type                                                | Description                         |
|-----------------------------|-----------------------------------------------------|-------------------------------------|
| symbol                      | string or null                                      | Short name related to the Gene's symbol
| relative_location           | [RelativeLocation](./relative_location.md)          | Location of the transcript in relation to the gene
| stable_id                   | string                                              | A unique identifier for the transcript
| version                     | integer                                             | Version of the transcript
| unversioned_stable_id       | string                                              | Unversioned unique identifier for the transcript
| type                        | string                                              | The value is always `Transcript`
| slice                       | Slice                                               | [Slice](./slice.md) describing the coordinates of the transcript
| spliced_exons               | array of SplicedExon                                | The ordered list of [exons](./exon.md) of the transcript
| introns                     | array of Intron                                     | The ordered list of [introns](./intron.md) of the transcript
| product_generating_contexts | array of ProductGeneratingContext                   | see [ProductGeneratingContext](./product_generating_context.md)
| metadata                    | TranscriptMetadata                                  | See [metadata](./metadata.md)
| gene                        | Gene                                                | The parent [gene](./gene.md) of the transcript, see Gene
| external_references         | array of ExternalReference                          | See [ExternalReference](./external_reference.md)
|sequence_edits | Array of SequenceEdit | See [SequenceEdit](./sequence_edit.md)

## Notes
1. `sequence_edits` in the context of a transcript can be used to describe patches made to the reference sequence

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
  "metadata": { ... },
  "gene": { ... },
  "external_references": [],
  "sequence_edits":[]
}
```
