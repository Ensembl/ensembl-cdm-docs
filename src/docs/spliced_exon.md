# SplicedExon

The `SplicedExon` data type combines the immutable, context-independent set of properties of an [Exon](./exon.md) (q.v.) with the properties that characterise `exon`'s position within a [Transcript](./transcript.md). `SplicedExon` has the following fields:

| Field             | Type             | Description |
|-------------------|------------------|-------------|
| index             | integer          | 0-based, denotes order of exons within a gene
| relative_location | RelativeLocation | [Location](./location.md) of exon relative to the transcript, see [RelativeLocation](./relative_location.md)
| exon              | Exon             | Context-independent properties of the exon, see [Exon](./exon.md)

## Rationale
An `Exon` with the same stable id may be included in different `transcripts`, where it will by necessity have a different location relative to the `transcript`, and may also have a different order in which it is joined with other `exons`. The purpose of the `SplicedExon` data type is to support the separation of context-independent fields, which always contain the same values regardless of the `transcript` the `exon` is included in, from context-dependent fields that may contain different values depending on which `transcript` the `exon` is a part of.

## Notes
1. Hierarchically, `SplicedExon` is direct child of a `Transcript`. It enriches the data contained within the `Exon` data type with the information about `exon`'s position within a `transcript` and its order relative to other `exons`. It follows, therefore, that all `SplicedExons` within a `Transcript` belong to the same transcript. Contrast this with [PhasedExon](./phased_exon.md).

## Examples

```json
{
  "index": 0,
  "relative_location": {
    "start": 1,
    "end": 60,
    "length": 60
  },
  "exon": {
    "version": 1,
    "stable_id": "ENSE00003856928.1",
    "unversioned_stable_id": "ENSE00003856928",
    "type": "Exon",
    "slice": {
      "location": {
        "start": 32315086,
        "end": 32315145,
        "length": 60,
        "location_modifier": null
      },
      "region": {
        "name": "13",
        "code": "chromosome",
        "topology": "linear",
        "sequence": { ... },
        "assembly": { ... },
        "length": 114364328,
        "metadata": { ... }
      },
      "strand": {
        "code": "forward",
        "value": 1
      }  
    },
    "transcripts": [...],
    "metadata": {
      "ontology_terms": [
        {
          "accession_id": "SO:0000147",
          "value": "exon",
          "url": "www.sequenceontology.org/browser/current_release/term/SO:0000147",
          "source": {
            "name": "Sequence Ontology",
            "url": "www.sequenceontology.org",
            "description": "The Sequence Ontology..."
          }
        }
      ]
    }
  }
}
```
