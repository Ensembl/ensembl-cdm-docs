# Sequence
The `Sequence` data type describes a contiguous set of nucleic acid or amino acid residues in biological molecules, such as DNA, RNA, or proteins.

| Field     | Type                                           | Description |
|-----------|------------------------------------------------|-------------|
| alphabet  | [SequenceAlphabet](./sequence_alphabet.md)     | Alphabet with which the sequence is encoded
| checksum  | string                                         | A checksum digest derived from the underlying sequence held in value


## Notes

## General

GA4GH identifiers are preferred as checksums since they are a CURIE and therefore namespace the checksum


### Sequence strings

For ease of use, some implementations may add sequence to the model to provide the sequence string directly. However, sequence strings can be quite large and therefore this behaviour is not included in the model by default.  If sequence strings are provided, the field should be called `sequence` and it should contain a string of upper-case characters with no white spaces (bound by IUPAC codes for amino acids and DNA), which represents biological sequence using conventional sequence ordering i.e. telomere to centromere to telomere, 5' to 3' or amino-to-caboxyl. Redundancy symbols, such as `N`, are permitted.  

Genomic sequence will be on the forward strand from the lowest 5' end coordinate to the highest 3' end coordinate.

If the `sequence` field is unavailable in a given implementation, the checksum can be used to retrieve the sequence from a RefGet service.


## Examples

```json
{
  "alphabet": {
    "accession_id": "sequence_alphabet.dna",
    "value": "dna",
    "label": "DNA",
    "definition": "IUPAC notation for DNA sequence",
    "description": null
  },
  "checksum": "e8f2b6ffd919c3cd209cb68afe8872da"
}
```

```json
{
  "alphabet": {
    "accession_id": "sequence_alphabet.dna",
    "value": "dna",
    "label": "DNA",
    "definition": "IUPAC notation for DNA sequence",
    "description": null
  },
  "checksum": "e8f2b6ffd919c3cd209cb68afe8872da"
}
