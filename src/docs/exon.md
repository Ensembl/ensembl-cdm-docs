# Exon

The `Exon` data type represents a fragment of a gene that is present in the mature messenger RNA molecule from that gene. It has the following fields:

| Field                 | Type                  | Description                                         |
|-----------------------|-----------------------|-----------------------------------------------------|
| version               | integer               | version of exon's annotation                        |
| stable_id             | string                | exon's stable id                                    |
| unversioned_stable_id | string                | Unversioned unique identifier for the exon          |
| type                  | string                | the value is always `Exon`                          |
| slice                 | Slice                 | see [Slice](./slice.md)                             |
| transcripts           | array of Transcript   | see [Transcript](./transcript.md)                   |
| metadata              | Metadata              | See [FeatureMetadata](./feature_metadata.md)       |


## Notes
1. Ensembl uses the term `Exon` in a broader sense than it traditionally has in molecular and cell biology. In biology, exons, by definition, are restricted to eukaryotes and Archaea, whose RNA, during maturation, undergoes a process of splicing, in which some RNA fragments (introns) are removed, while the remaining RNA fragments (exons) are joined together. In contrast, Ensembl uses the term `Exon` to refer to gene fragments that are present in the final form of the messenger RNA molecule regardless of whether splicing has taken place. Thus, bacterial genes will also be described by Ensembl as containing exons (one exon per gene).
2. The data contained within the `Exon` data type is stable regardless of which `Transcript` the `Exon` is a part of or how it was joined with other exons during splicing (see `Product-Generating Context`). For additional data about the exon that depends on its context, see [Spliced Exon](./spliced_exon.md) and [Phased Exon](./phased_exon.md) data types.
3. Since an `Exon` contains only context-independent data, it can be retrieved directly by its stable id via an api.
4. An `Exon`, uniquely identified by its stable_id, can be present in multiple transcripts

## Example

```json
{
  "version": 1,
  "stable_id": "ENSE00003856928",
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
```
