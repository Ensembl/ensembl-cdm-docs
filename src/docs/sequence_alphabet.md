## SequenceAlphabet
`SequenceAlphabet` is an Ensembl value set

| Field        | Type           | Description                                                     |
|--------------|----------------|-----------------------------------------------------------------|
| accession_id | string         | Accession id in Ensembl database of [Value Sets](./value_set.md)
| label        | string         | Short, pretty-printed label ready for display
| value        | string         | A string intended for programmatic use by consumer
| definition   | string or null | Succinct definition of the term
| description  | string or null | Optional longer description that can contain nuances

## Examples

```json
{
  "accession_id": "sequence_alphabet.dna",
  "value": "dna",
  "label": "DNA",
  "definition": "IUPAC notation for DNA sequence",
  "description": null
}
```
