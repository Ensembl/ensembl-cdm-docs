# Product

The `Product` data type contains information about the mature functioning molecule produced from a Gene. It includes the following fields:

| Field                 | Type                         | Description |
|-----------------------|------------------------------|-------------|
| stable_id             | string                       | Unique identifier for the product (versioned)
| unversioned_stable_id | string                       | Unversioned unique identifier for the product
| version               | integer or null              | Version of the product
| type                  | string                       | Type of the product (e.g. "Protein" or "RNA")
| so_term               | string                       | Sequence Ontology term describing the product
| length                | integer                      | Number of subunits (amino acids for proteins, nucleotides for RNA) comprising the product
| external_references   | array of External Reference  | See `External Reference`
| sequence              | Sequence                     | See `Sequence`
| family_matches        | FamilyMatch array            | See `Family Match` below


## Family Match

`FamilyMatch` contains information about a match between the product sequence and a sequence from a known family recorded in an external database. It has the following fields:


| Field           | Type                         | Description |
|-----------------|------------------------------|-------------|
| sequence_family | SequenceFamily               | See below
| via             | ClosestDataProvider or null  | See below
| location        | Location                     | Location of the match in the product sequence (see `Location`)
| hit_location    | Location or null             | Location within the family sequence that is matched to the product sequence (see `Location`)
| score           | float or null                | Analysis score asserting the presence of this match at this location
| evalue          | float or null                | Expectation value for the presence of this match at this location


### Sequence Family

Reference to the sequence family record in the database that is the original provider of the data about this family.

| Field        | Type           | Description |
|--------------|----------------|-------------|
| source       | string         | Name of the source database
| accession_id | string         | Unique identifier of the family in the source database
| description  | string or null | Description of the family


### Closest Data Provider

For cases when a match was calculated using an aggregator database, such as Interpro, this is the reference to the record in such database.

| Field        | Type           | Description |
|--------------|----------------|-------------|
| source       | string         | Name of the database
| accession_id | string         | Unique identifier of the family in the database


## Example

```json
{
  "stable_id": "ENSP00000369497.3",
  "unversioned_stable_id": "ENSP00000369497",
  "version": 3,
  "type": "protein",
  "so_term": "???",
  "length": 3418,
  "external_references": [],
  "sequence": { ... },
  "family_matches": [
    {
      "sequence_family": {
        "source": "Pfam",
        "accession_id": "PF00634",
        "description": "BRCA2 repeat"
      },
      "via": {
        "source": "Interpro",
        "accession_id": "IPR002093"
      },
      "location": {
        "start": 1003,
        "end": 1035,
        "length": 33
      },
      "score": ???,
      "evalue": ???,
      "hit_location": {
        "start": 1,
        "end": 33,
        "length": 33
      },
    }
  ]
}
```
