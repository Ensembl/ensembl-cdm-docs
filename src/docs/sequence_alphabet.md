## SequenceAlphabet
SequenceAlphabet is an Ensembl value set

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
