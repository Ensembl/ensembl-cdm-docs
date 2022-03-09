# Sequence
The `Sequence` data type describes a contiguous set of nucleic acid or amino acid residues in biological molecules, such as DNA, RNA, or proteins.

| Field     | Type                                           | Description |
|-----------|------------------------------------------------|-------------|
| alphabet  | [SequenceAlphabet](./sequence_alphabet.md)     | Alphabet with which the sequence is encoded
| checksum  | string                                         | A checksum digest derived from the underlying sequence held in value
| sequence  | string                                         | Optional field! Contains the string representing the biological sequence.


## Notes

1. The value of the sequence field is a string of letters (bound by IUPAC codes for amino acids and DNA), which represents biological sequence using conventional sequence ordering i.e. telomere to centromere to telomere, 5' to 3' or amino-to-caboxyl. Redundancy symbols, such as `N`, are permitted.
2. GA4GH identifiers are preferred as checksums since they are a CURIE and therefore namespace the checksum
3. Sequence strings can be quite large (for example, they may represent the nucleotide sequence of a whole chromosome). Therefore, due to technical constraints, some implementations that provide the Sequence data type (e.g. a graphQL server) may not contain the `sequence` field. If the `sequence` field is present, it contains a string of upper-case characters with no white spaces.
4. If the `sequence` field is unavailable in a given implementation, the checksum can be used to retrieve the sequence from a RefGet service.

## Example

```json
{
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
```
