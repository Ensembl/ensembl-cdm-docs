# Spliced Exon

_provisional name_

The `Spliced Exon` data type combines the immutable, context-independent set of properties of an `Exon` (q.v.) with the properties that characterise exon's position within a transcript. `Spliced Exon` has the following fields:

| Field             | Type             | Description |
|-------------------|------------------|-------------|
| index             | integer          | 0-based, denotes order of exons within a gene
| relative_location | RelativeLocation | location of exon relative to the transcript, see `Relative Location`
| exon              | Exon             | context-independent properties of the exon, see `Exon`

## Rationale
An `Exon` with the same stable id may be included in different transcripts, where it will by necessity have a different location relative to the transcript, and may also have a different order in which it is joined with other exons. The purpose of the `Spliced Exon` data type is to support the separation of context-independent fields, which always contain the same values regardless of the transcript the exon is included in, from context-dependent fields that may contain different values depending on which transcript the exon is a part of.

## Notes
1. Hierarchically, `Spliced Exon` is direct child of a `Transcript`. It enriches the data contained within the `Exon` data type with the information about exon's position within a transcript and its order relative to other exons. It follows, therefore, that all `Spliced Exons` within a `Transcript` belong to the same transcript. Contrast this with `Phased Exon`.
