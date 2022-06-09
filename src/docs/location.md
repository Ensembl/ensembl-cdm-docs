# Location

The `Location` data type stores coordinates that position a [Feature](./feature.md) on a [Region](./region.md). `Location` has the following fields:

| Field             | Type                                                  | Description |
|-------------------|-------------------------------------------------------|-------------|
| start             | integer                                               | start coordinate
| end               | integer                                               | end coordinate
| length            | integer                                               | number of nucleotides between start and end coordinates, inclusive
| location_modifier | [LocationModifier](./location_modifier.md) or NULL    | `LocationModifier` is used to define whether or not the feature is a "partial model" with undefined start and/or end coordinates.  See point 5 in the notes below

## Notes
1. Start coordinate of a `Feature` is the one closest to the 5'-end of the `Region` on which it is located; while the end coordinate is the one closest to the 3'-end.
2. Start and end coordinates are 1-based. End coordinate is inclusive. Which means that a Feature that starts at nucleotide 1 and ends at nucleotide 10 will have a Location with the `start` property equal to 1 and the `end` property equal to 10. Since the end coordinate is inclusive, the length of a Feature on a linear Region can be calculated as `end - start + 1`.
3. The value of the end coordinate is guaranteed to be greater than the value of the start coordinate if the `Feature` is positioned on a linear `Region`. However, on circular `regions`, the end coordinate can be less than the start coordinate if the `Feature` is overlapping the origin.
4. Although the length of a `Feature` is trivially calculable when the `Feature` is positioned on a linear `Region`, the `Location` data type still contains the `length` field for two reasons:
  - to provide a quick check to guard against off-by-one errors;
  - to help avoid more involved calculations required if a `Feature` is located on a circular `Region` and overlaps the origin
5. Partial models are defined as features where the start and/or coordinates are poorly defined.  For example, `<1..123`, where the feature starts before the first sequenced base and continues to and includes base 123.

## Examples

```json
{
  "start": 32315474,
  "end": 32400266,
  "length": 84793,
  "location_modifier" : null
}
```

```json
{
  "start": 888,
  "end": 368689,
  "length": 83906,
  "location_modifier" {
    "partial_start": true,
    "partial_end": false    
  }
}
```
