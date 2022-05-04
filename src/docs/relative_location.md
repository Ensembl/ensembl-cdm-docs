# Relative Location

The `Relative Location` data type describes the position of a Feature **relative to its immediate parent feature**. It has the same fields as does `Location`:

| Field  | Type      | Description |
|------- |-----------|-------------|
| start  | integer   | start coordinate
| end    | integer   | end coordinate
| length | integer   | number of nucleotides between start and end coordinates, inclusive

## Rationale
The purpose of the `Relative Location` data type is to supply the client with coordinates of a feature relative to its immediate parent to relieve the client of the need to calculate these positions by itself. The value of `Relative Location` becomes particularly noticeable for features on the reverse strand or on a circular chromosome overlapping the origin.

## Notes
1. `Relative Location` is relative to the location of the immediate parent feature. For example, `Transcript`'s `Relative Location` is relative to the location of the `GeneAllele` that produces this `Transcript`. Similarly, `Exon`'s `Relative Location` is relative to the location of the `Transcript` that contains this `Exon`.
2. `Relative Location` is always calculated in the 5'->3' direction. Therefore, on the forward strain, relative coordinate 1 points at the same nucleotide as the **start** coordinate of the parent feature; and on the reverse strand relative coordinate 1 points at the same nucleotide as the **end** coordinate of the parent feature.
3. In contrast to `Location`, `Relative Location` guarantees that the end coordinate will be greater than the start coordinate.


## Examples

### Calculating Relative Location

1. For feature on the forward strand (exon ENSE00003856928 within transcript ENST00000671466.1)
- given that the transcript is on the forward strand
- and transcript's genomic coordinates are: start 32315086 and end 32316527
- and exon's genomic coordinates are start 32315086 and end 32315145,

The exon's relative locaiton is:

`start = exon start - transcript start + 1`, i.e. `32315086 - 32315086 + 1`, i.e. `1`

`end = exon end - transcript start  + 1`, i.e. `32315145 - 32315086 + 1`, i.e. `60`

`length = relative end - relative start + 1`, i.e. `60 - 1 + 1`, i.e. 60


```json
{
  "start": 1,
  "end": 60,
  "length": 60
}
```

2. For feature on the reverse strand (transcript ENST00000530622 transcribed from gene allele ENSG00000139597)
- given that the gene allele is on the reverse strand
- and the gene allele's genomic coordinates are: start 32400723 and end 32428311
- and the transcript's genomic coordinates are: start 32401677 and end 32411606

The transcript's relative location is:

`start = gene allele end - transcript end - 1`, i.e. `32428311 - 32411606 + 1`, i.e. `16706`

`end = gene allele end - transcript start  - 1`, i.e. `32428311 - 32401677 + 1`, i.e. `26635`

`length = relative end - relative start + 1`, i.e. `26635 - 16706 + 1`, i.e. `9930`


```json
{
  "start": 16706,
  "end": 26635,
  "length": 9930
}
```

3. For feature on the reverse strand of a circular chromosome (transcript CAK10225 transcribed from gene allele RL4742)
- given that the gene allele is on the reverse strand and overlaps the origin
- and the chromosome is circular and has a length of 5057142bp
- and the gene allele's genomic coordinates are: start 5056183 and end 72
- and the transcript's genomic coordinates are: start -959 and end 72

The transcript's relative location is:

`start = gene allele end - transcript end + 1`, i.e. `72 - 72 + 1`, i.e. `1`

`end = gene allele end - transcript end + 1`, i.e. `72 - -959 + 1`, i.e. `1032`

`length = relative end - relative start + 1`, i.e. `1032 - 1 + 1`, i.e. `1032`

```json
{
  "start": 1,
  "end": 1032,
  "length": 1032
}
```
