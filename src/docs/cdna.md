# cDNA

The sequence of the spliced exons of a transcript expressed in DNA notation (T rather than U), representing the coding or sense strand. The cDNA contains the whole sequence of the RNA, including coding and untranslated sequence. The sequence reflects any RNA editing. `cDNA` has the following fields:

| Field             | Type      | Description                         |
|-------------------|-----------|-------------------------------------|
| start             | integer   | genomic start coordinate (1-based)
| end               | integer   | genomic end coordinate (1-based, inclusive)
| length            | integer   | length of the cDNA in nucleotides
| sequence          | Sequence | see [Sequence](./sequence.md)

## Notes
1. Fields may not be null.
2. The `start` and the `end` fields, by definition, have the same values as genomic start and genomic end coordinates of the transcript itself, but are included in `cDNA` for convenience. `relative_start` and `relative_end` fields are not included, because `relative_start` will always be 1, and `relative_end` will always be the same as the transcript length.
3. In the case of operons or other polycistronic genes, the cDNA will include intermediate UTRs.
4. cDNAs are not Features, and their complete sequences do not necessarily correspond to any genomic sequence. Therefore, cDNA Sequences will be stored in RefGet and can be retrieved using the sequence checksum.

## Examples
```json
{
    "start": 32379840,
    "end": 32398272,
    "length": 842,
    "sequence": {
      ...
    }
}
```
