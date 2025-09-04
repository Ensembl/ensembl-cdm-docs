# CDS
The `CDS` (**c**o**d**ing **s**equence) data type represents the region of a [cDNA](./cdna.md) that is translated. It includes the following fields:

| Field            | Type    | Description |
|------------------|---------|-------------|
| start            | integer | Genomic start coordinate (1-based)
| end              | integer | Genomic end coordinate (1-based, inclusive)
| relative_start   | integer | Start coordinate (1-based) relative to the beginning (5'-end) of the [Transcript](./transcript.md)
| relative_end     | integer | End coordinate relative to `Transcript`'s start (1-based, inclusive)
| nucleotide_length| integer | Total number of nucleotides comprising the `CDS`
| protein_length   | integer | Number of amino acids in the protein encoded by the `CDS`
| sequence         | Sequence| See [Sequence](./sequence.md)


## Notes
1. The stop codon is included as part of the `CDS` sequence.
2. The `CDS` data type does not have a dedicated [slice](./slice.md) field, because a `CDS` can be retrieved only as a part of a parent [Feature](./feature.md) ([Transcript](./transcript.md)), and thus will share the same [Region](./region.md) and [Strand](./strand.md) as that `Feature`.

## Examples

_notice that the nucleotide length of the CDS cannot be derived from its genomic coordinates, because of the mRNA editing that has removed the introns_

```json
{
  "start": 32316461,
  "end": 32316527,
  "relative_start": 1376,
  "relative_end": 1442,
  "nucleotide_length": 66,
  "protein_length": 22,
  "sequence": {
    ...
  }
}
```
