# CDS
The `CDS` (**c**o**d**ing **s**equence) data type represents the region of a cDNA that is translated. It includes the following fields:

| Field            | Type    | Description |
|------------------|---------|-------------|
| start            | integer | genomic start coordinate (1-based)
| end              | integer | genomic end coordinate (1-based, inclusive)
| relative_start   | integer | start coordinate relative to `Transcript`'s genomic start (1-based)
| relative_end     | integer | end coordinate relative to `Transcript`'s genomic start (1-based, inclusive)
| nucleotide_length| integer | total number of nucleotides comprising the CDS
| protein_length   | integer | number of amino acids in the protein encoded by the CDS
| sequence_checksum| string  | checksum of the corresponding sequence stored in RefGet
| sequence         | string  | raw nucleotide sequence


## Notes
1. The stop codon is included as part of the CDS sequence.
2. The `CDS` data type does not have a dedicated `slice` field, because a `CDS` can be retrieved only as a part of a parent `Feature` (`Transcript`), and thus will share the same `Region` and `Strand` as that `Feature`.
