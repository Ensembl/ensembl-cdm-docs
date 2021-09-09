# Exon

The `Exon` data type represents a fragment of a gene that is present in the mature messenger RNA molecule from that gene. It has the following fields:

| Field     | Type    | Description |
|-----------|---------|-------------|
| so_term   | string  | Sequence Ontology term describing the exon
| version   | integer | version of exon's annotation
| stable_id | string  | exon's stable id
| type      | string  | the value is always "Exon"
| sequence  | string  | raw nucleotide sequence (see also Sequence, value)
| slice     | Slice   | see Slice


## Notes
1. Ensembl uses the term `Exon` in a broader sense than it traditionally has in molecular and cell biology. In biology, exons, by definition, are restricted to eukaryotes and Archaea, whose RNA, during maturation, undergoes a process of splicing, in which some RNA fragments (introns) are removed, while the remaining RNA fragments (exons) are joined together. In contrast, Ensembl uses the term `Exon` to refer to gene fragments that are present in the final form of the messenger RNA molecule regardless of whether splicing has taken place. Thus, bacterial genes will also be described by Ensembl as containing exons (one exon per gene).
2. The data contained within the `Exon` data type is stable regardless of which `Transcript` the `Exon` is a part of or how it was joined with other exons during splicing (see `Product-Generating Context`). For additional data about the exon that depends on its context, see `Spliced Exon` and `Phased Exon` data types.
3. Since an `Exon` contains only context-independent data, it can be retrieved directly by its stable id via an api.


## Example

```json
{
  "stable_id": "ENSE00003856928",
  "version": 1,
  "type": "Exon",
  "so_term": "exon",
  "slice": {
    "location": {
      "start": 32315086,
      "end": 32315145,
      "length": 60
    },
    "region": {
      "name": "13",
      "code": "chromosome"
    },
    "strand": {
      "code": "forward",
      "value": 1
    }
  },
  "sequence": "AAGCTTTTGTAAGATCGGCTCGCTTTGGGGAACAGGTCTTGAGAGAACATCCCTTTTAAG"
}
```
