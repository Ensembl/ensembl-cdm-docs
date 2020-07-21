# UTR

`UTR` (**u**n**t**ranslated **r**egion) is a data type representing the region of a coding cDNA that is either upstream of the start codon (5' UTR) or downstream of the stop codon (3' UTR). `UTR` has the following fields:

| Field     | Type     | Description |
|-----------|----------|-------------|
| location  | Location | genomic location

## Notes
1. The stop codon, although not translated, is not included in 3'UTR, but rather is counted as a part of CDS.
2. The `UTR` data type does not have a dedicated `slice` field, because `UTR`s can be retrieved only as a part of a parent `Feature` (`Transcript`), and thus will share the same `Region` and `Strand` as that `Feature`.
3. The `UTR` data type does not have relative location information, because it is trivially inferred from the start and end relative coordinates of the CDS. 5'-UTR will always have a relative start of `1` and relative end at `CDS`'s relative start - 1; while 3'-UTR will always have relative start at `CDS`'s relative end + 1, and relative end at transcript end.
