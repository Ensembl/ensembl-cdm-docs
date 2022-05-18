# Intron

The `Intron` data type represents a fragment of a [gene](./gene.md) that is removed by RNA splicing to produce the final messenger RNA molecule. It has the following fields:

| Field             | Type             | Description |
|-------------------|------------------|-------------|
| index             | integer          | Index of `Intron`
| slice             | Slice            | See Slice
| relative_location | RelativeLocation | See RelativeLocation
| type              | string           | Type is Intron

## Notes
1. All `introns` that make up a [transcript](./transcript.md) are stored together in a list called `introns`. The index of an `intron` reflects the position of the `intron` relative to its surrounding `introns`. The order is determined by the alternating pattern of [exons](./exon.md) and `introns` in a `transcript`.
2. `Intron` is a [feature](./feature.md). `Intron` does not have `stable_id`, `unversioned_stable_id` and `version` fields.

## Examples
```json
{
  "index": 0,
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
  "relative_location": {
    "start": 110,
    "end": 120,
    "length": 11
  },
  "type": "Intron"
}
```
