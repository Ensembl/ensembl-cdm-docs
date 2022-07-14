# Strand
The purpose of the `strand` data type is to indicate which strand of a double-stranded molecule a [Feature](./feature.md) is located on.

| Field   | Type                   |
|---------|------------------------|
| code    | StrandCode (see below) |
| value   | StrandValue (see below)|

## StrandCode
`StrandCode` is a string-based system for identifying a `strand`. It is an enum of two possible string values:

- "forward"
- "reverse"

## StrandValue
`StrandValue` is a string-based system for identifying a `strand`. It is an enum of two possible numerical values:

- 1
- -1

where `1` signifies forward strand and `-1` signifies the reverse strand.

## Notes
1. The `code` and the `value` properties are two alternative ways of identifying a `strand`.
2. The fields of the `strand` data type are therefore redundant. If the `code` field is set to `"forward"`, the `value` field will necessarily be set to `1`, and vice versa.
3. The purpose of the `value` field is to maintain continuity with the way Ensembl has historically labelled strands. The purpose of the `code` field is to improve human readability of the data received over an API.
4. The `strand` of a single-stranded polynucleotide is always `"forward"`.

## Examples
Below is the exhaustive list of valid values of the `strand` data type:

```json
{
  "code": "forward",
  "value": 1
}
```

```json
{
  "code": "reverse",
  "value": -1
}
```
