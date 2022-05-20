# PhasedExon

The `Phased Exon` data type combines the immutable, context-independent set of properties of an [Exon](./exon.md) with the properties that characterise arrangement of `exons` in mature messenger RNA. `Phased Exon` has the following fields:

| Field             | Type             | Description |
|-------------------|------------------|-------------|
| index             | integer          | 0-based, denotes order of exons in mature messenger RNA
| start_phase       | ExonPhase        | See below
| end_phase         | ExonPhase        | See below
| exon              | Exon             | Context-independent properties of the exon, see [Exon](./exon.md)

## ExonPhase
`ExonPhase` is an enum of integers: `-1`, `0`, `1`, or `2`.

Biologically, `ExonPhase` refers to the position of an exon/intron boundary within a codon. A phase of `0` means the boundary falls between codons, `1` means between the first and second nucleotide, and `2` means between the second and third nucleotide. Phase is always calculated in 5'->3' direction. Since for non-coding transcripts the concept of codon does not apply, non-coding exons have both start and end phase of `-1`.

In ascii art, with alternate codons represented by `###` and `+++`, ExonPhase can be illustrated like this:

```

    Previous Exon   Intron   This Exon
...-------------            -------------...
5'                   Phase                 3'
...#+++###+++###       0    +++###+++###+...
...+++###+++###+       1    ++###+++###++...
...++###+++###++       2    +###+++###+++...

```

## Rationale
Similarly to [SplicedExon](./spliced_exon.md), `Phased Exon` supports the separation of context-independent exon properties (through the `Exon` data type) and the properties that emerge within a context of mature messenger RNA.

## Notes
1. `Phased Exons` are a property of `Product-Generating Context`. Ordinarily, they all are children of the same parent transcript; but in cases of trans-splicing they will include `exons` from other `transcripts`.

## Example

```json
{
  "index": 0,
  "start_phase": 0,
  "end_phase": 0,
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
