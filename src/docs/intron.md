# Intron

The `Intron` data type represents a fragment of a gene that is removed by RNA splicing to produce the final messenger RNA molecule. It has the following fields:

| Field             | Type             | Description |
|-------------------|------------------|-------------|
| index             | integer          | Index of Intron
| sequence          | Sequence         | see Sequence
| slice             | Slice            | see Slice
| relative_location | RelativeLocation | see RelativeLocation
| type              | string           | type is Intron

## Notes
1. All introns that make up a transcript are stored together in a list called introns. The index of an intron reflectes the postion of the intron relative to its surrounding introns. The order is determined by the alternating pattern of exons and introns in a transcript.
2. Intron is a feature. Intron does not have stable_id and version fields.

## Examples
```json
{
  "index": 0,
  "relative_location": {
    "start": 110,
    "end": 120,
    "length": 11
  },
  "slice": {
    "location": {
      "start": 123456,
      "end": 123466,
      "length": 11,
    },
    "region": {
      "name": "13",
      "code": "chromosome",
      "topology": "linear",
      "length": 114364328
    }
  },
  "type": "Intron"
}
```
