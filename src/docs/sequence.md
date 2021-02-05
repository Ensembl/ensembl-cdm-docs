# Sequence
The `Sequence` data type describes a contiguous set of nucleic acid or amino acid residues in biological molecules, such as DNA, RNA, or proteins.

| Field     | Type              | Description |
|-----------|-------------------|-------------|
| alphabet  | SequenceAlphabet  | Alphabet with which the sequence is encoded
| checksum  | string            | A checksum digest derived from the underlying sequence held in value
| sequence  | string            | Optional field! Contains the string representing the biological sequence.


## SequenceAlphabet
`SequenceAlphabet` is an Ensembl value set

| Field       | Type           | Description |
|-------------|----------------|-------------|
| accession_id| string         | accession id in Ensembl database of Value Sets
| label       | string         | short, pretty-printed label ready for display
| value       | string         | a string intended for programmatic use by consumer 
| definition  | string         | succinct definition of the term
| description | string or null | optional longer description that can contain nuances

```json
{
  "alphabet": {
    "accession_id": "sequence_alphabet.dna",
    "value": "dna",
    "label": "DNA",
    "definition": "IUPAC notation for DNA sequence",
    "description": null
  }
}
```

## Notes

1. The value of the sequence field is a string of letters (bound by IUPAC codes for amino acids and DNA), which represents biological sequence using conventional sequence ordering i.e. telomere to centromere to telomere, 5' to 3' or amino-to-caboxyl. Redundancy symbols, such as `N`, are permitted.
2. GA4GH identifiers are preferred as checksums since they are a CURIE and therefore namespace the checksum
3. Sequence strings can be quite large (for example, they may represent the nucleotide sequence of a whole chromosome). Therefore, due to technical constraints, some implementations that provide the `Sequence` data type (e.g. a graphQL server) may not contain the `sequence` field. If the `sequence` field is present, it contains a string of upper-case characters with no white spaces.
4. If the `sequence` field is unavailable in a given implementation, the checksum can be used to retreive the sequence from a refget service.

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
