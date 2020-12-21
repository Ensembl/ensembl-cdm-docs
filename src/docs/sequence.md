# Sequence
The `Sequence` data type describes a contiguous set of nucleic acid or amino acid residues in biological molecules, such as DNA, RNA, or proteins.

| Field    | Type              | Description |
|----------|-------------------|-------------|
| alphabet | SequenceAlphabet  | State the alphabet of the sequence encoded
| type     | string            | Sequence object type. Must be set to Sequence
| checksum | string            | A checksum digest derived from the underlying sequence held in value
| value    | string            | The raw sequence. Contigous with no whitespace. All uppercase characters


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
    "definition": "Deoxyribonucleic acid.",
    "description": "???"
  }
}
```

## Notes

1. The value of a sequence is a string of letters (bound by IUPAC codes for amino acids and DNA), which represents biological sequence using conventional sequence ordering i.e. telomere to centromere to telomere, 5' to 3' or amino-to-caboxyl. Redundancy symbols, such as `N`, are permitted. 
2. GA4GH identifiers are preferred as checksums since they are a CURIE and therefore namespace the checksum
3. All checksum contents can be used in a refget instance to retreive a sequence if value is null
