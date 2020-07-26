# UTR

`UTR` (**u**n**t**ranslated **r**egion) is a data type representing the region of a coding cDNA that is either upstream of the start codon (5' UTR) or downstream of the stop codon (3' UTR). `UTR` has the following fields:

| Field              | Type    | Description |
|--------------------|---------|-------------|
| start              | integer | genomic start coordinate
| end                | integer | genomic end coordinate
| length             | integer | number of nucleotides comprising the UTR
| sequence_checksum  | string  | a checksum digest of the sequence
| sequence           | string  | raw sequence of the UTR

## Notes
1. The stop codon, although not translated, is not included in 3' UTR, but rather is counted as a part of CDS.
2. Like the `CDS`, the `UTR`s do not have a dedicated `slice` field, because of the mRNA editing involved in the generation of a mature mRNA.
3. The `UTR` data type does not have relative location information, because it is trivially inferred from the start and end relative coordinates of the CDS. 5' UTR will always have a relative start of `1` and relative end at `CDS`'s relative start - 1; while 3' UTR will always have relative start at `CDS`'s relative end + 1, and relative end at transcript end.

## Example

_notice how the length of the UTR (99bp) cannot be derived from its genomic coordinates (start: 32315086, end: 32316461), because of the mRNA editing that has removed the introns_

```json
{
  "start": 32315086,
  "end": 32316461,
  "length": 99,
  "sequence_checksum": "truncatedsha512",
  "sequence": "AAGCTTTTGTAAGATCGGCTCGCTTTGGGGAACAGGTCTTGAGAGAACATCCCTTTTAAGACTTATTTACCAAGCATTGGAGGAATATCGTAGGTAAAA"
}
```
