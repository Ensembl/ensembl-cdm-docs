# Location

The `Location` data type stores coordinates that position a `Feature` on a `Region`. The `Location` has the following fields:

| Field  | Type      | Description |
|------- |-----------|-------------|
| start  | integer   | start coordinate
| end    | integer   | end coordinate
| length | integer   | number of nucleotides between start and end coordinates, inclusive

## Notes
1. Start coordinate of a Feature is the one closest to the 5'-end of the Region on which it is located; while the end coordinate is the one closest to the 3'-end.
2. Start and end coordinates are 1-based. End coordinate is inclusive. Which means that a Feature that starts at nucleotide 1 and ends at nucleotide 10 will have a Location with the `start` property equal to 1 and the `end` property equal to 10. Since the end coordinate is inclusive, the length of a Feature on a linear Region can be calculated as `end - start + 1`.
3. The value of the end coordinate is guaranteed to be greater than the value of the start coordinate if the Feature is positioned on a linear Region. However, on circular regions, the end coordinate can be less than the start coordinate if the Feature is overlapping the origin.
4. Although the length of a Feature is trivially calculable when the Feature is positioned on a linear Region, the Location data type still contains the `length` field for two reasons:
  - to provide a quick check to guard against off-by-one errors;
  - to help avoid more involved calculations required if a Feature is located on a circular Region and overlaps the origin

## Example

```json
{
  "start": 32315474,
  "end": 32400266,
  "length": 84793
}
```
