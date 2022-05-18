# UTR

`UTR` (**u**n**t**ranslated **r**egion) is a data type representing the region of a coding [cDNA](./cdna.md) that is either upstream of the start codon (`5' UTR`) or downstream of the stop codon (`3' UTR`). `UTR` has the following fields:

| Field              | Type    | Description |
|--------------------|---------|-------------|
| start              | integer | Genomic start coordinate
| end                | integer | Genomic end coordinate
| length             | integer | Number of nucleotides comprising the UTR
| sequence           | Sequence| See [Sequence](./sequence.md)

## Notes
1. The stop codon, although not translated, is not included in `3' UTR`, but rather is counted as a part of [CDS](./cds.md).
2. Like the `CDS`, the `UTR`s do not have a dedicated [slice](./slice.md) field, because of the mRNA editing involved in the generation of a mature mRNA.
3. The `UTR` data type does not have [relative location](./relative_location.md) information, because it is trivially inferred from the start and end relative coordinates of the `CDS`. `5' UTR` will always have a relative start of `1` and relative end at `CDS`'s relative start - 1; while `3' UTR` will always have relative start at `CDS`'s relative end + 1, and relative end at [transcript](./transcript.md) end.

## Examples

_NB: The length of the UTR (99bp) cannot be derived from its genomic coordinates (start: 32315086, end: 32316461), because of the mRNA editing that has removed the introns_

```json
{
  "start": 32315086,
  "end": 32316461,
  "length": 99,
  "sequence": {  
    "alphabet": {
      "accession_id": "sequence_alphabet.dna",
      "value": "dna",
      "label": "DNA",
      "definition": "IUPAC notation for DNA sequence",
      "description": null
    },
    "checksum": "e8f2b6ffd919c3cd209cb68afe8872da",
    "sequence": "ACGGATCGACAGTAGTTAGA"
  }
}
```
