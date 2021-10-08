# Product

The `Product` data type contains information about the mature functioning molecule produced from a Gene. Depending on whether this molecule is a protein or an RNA, the `Product` is subdivided into a `ProteinProduct` and an `RNAProduct`.

Both `ProteinProduct` and the `RNAProduct` will have the following fields in common:

| Field                       | Type                          | Description |
|-----------------------------|-------------------------------|-------------|
| type                        | string                        | Type of the product (e.g. "Protein" or "RNA")
| length                      | integer                       | Number of subunits (amino acids for proteins, nucleotides for RNA) comprising the product
| external_references         | array of ExternalReference    | See `ExternalReference`
| sequence                    | Sequence                      | See `Sequence`
| metadata                    | Metadata                      | See `Metadata`
| product_generating_context  | ProductGeneratingContext      | See `ProductGeneratingContext`


## ProteinProduct

In addition to the fields common for all `Product`s, a `ProteinProduct` will have the following fields:

| Field                 | Type                          | Description |
|-----------------------|-------------------------------|-------------|
| stable_id             | string                        | Unique identifier for the product (versioned)
| unversioned_stable_id | string                        | Unversioned unique identifier for the product
| version               | integer or null               | Version of the product
| family_matches        | array of `FamilyMatch`        | See `FamilyMatch` below
| mappings              | array of `Mapping`            | See `Mapping` below

## FamilyMatch

`FamilyMatch` contains information about a match between the product sequence and a sequence from a known family recorded in an external database. It has the following fields:


| Field             | Type                         | Description |
|-------------------|------------------------------|-------------|
| sequence_family   | SequenceFamily               | See SequenceFamily below
| via               | ClosestDataProvider or null  | See ClosestDataProvider below
| relative_location | Location                     | Location within the product where the hit lands (see `Location`)
| hit_location      | Location or null             | Location within the family sequence that is matched to the product sequence (see `Location`)
| score             | float or null                | Analysis score asserting the presence of this match at this location
| evalue            | float or null                | Expectation value for the presence of this match at this location


### Sequence Family

Reference to the sequence family record in the database that is the original provider of the data about this family.

| Field        | Type           | Description |
|--------------|----------------|-------------|
| source       | ExternalDB     | See `ExternalDB` in the documentation of `ExternalReference`
| accession_id | string         | Unique identifier of the family in the source database
| name         | string         | Name of the family
| description  | string or null | Description of the family
| url          | string or null | Url for accessing the family in the source database


### Closest Data Provider

For cases when a match was calculated using an aggregator database, such as Interpro, this is the reference to the record in such database.

| Field        | Type       | Description |
|--------------|------------|-------------|
| source       | ExternalDB | See `ExternalDB` in the documentation of `ExternalReference`
| accession_id | string     | Unique identifier of the family in the database
| url          | string     | Url for accessing the family in the source database


## Mapping
The `Mapping` data structure describes a match between an Ensembl feature and a feature from an external database, e.g. Uniprot. It has the following fields:

| Field             | Type                            | Description |
|-------------------|---------------------------------|-------------|
| source            | ExternalDB                      | See `ExternalDB` in the documentation of `ExternalReference`
| accession_id      | string                          | Unique identifier of the feature in the source database
| url               | string                          | Url for accessing the feature in the source database
| name              | string or null                  | Name of the feature
| relative_location | Location                        | Location within the product where the hit lands (see `Location`)
| hit_location      | Location                        | Location within the external feature that is matched to the product sequence (see `Location`)
| genomic_locations | array of GenomicMappingLocation | Location within the genomic space corresponding to the product sequence that matches the external feature
| score             | float or null                   | Analysis score asserting the presence of this match at this location
| evalue            | float or null                   | Expectation value for the presence of this match at this location


### GenomicMappingLocation
`GenomicMappingLocation` provides the information about how the mapping between an Ensembl product and an external feature projects back onto the genomic space.

| Field        | Type           | Description |
|--------------|----------------|-------------|
| slice        | Slice          | see Slice
| cigar_string | string         | a string representing the alignment


## Notes
1. An RNA product is a mature RNA, which can be described by its cDNA. Since cDNAs don't have stable ids in Ensembl, RNA products are unlikely to have stable ids either.
2. For a match between an Ensembl product and an external feature, the location of the matching sequence within the Ensembl product is referred to here as `relative_location`, the location of the matching sequence within the external feature, as `hit_location`, and the projection of Ensembl product's matching sequence onto genomic coordinates, as `genomic_location`.

![diagram of a match](https://user-images.githubusercontent.com/6834224/117651701-2805bd00-b18a-11eb-9569-a1a27ebcdc5b.png)

3. A `slice` associated with a single `genomic_location` can span multiple exons; and the exact match is described using a CIGAR string in the `cigar_string` field. Because trans-splicing is possible, the `genomic_locations` field of a `Mapping` is an array.
4. A `relative_location` length may be the same as the `hit_location` length, or it may be different due to mismatches.


## Example

```json
{
  "stable_id": "ENSP00000369497.3",
  "unversioned_stable_id": "ENSP00000369497",
  "version": 3,
  "type": "protein",
  "length": 3418,
  "external_references": [],
  "metadata": { ... },
  "sequence": { ... },
  "product_generating_context": { ... },
  "family_matches": [
    {
      "sequence_family": {
        "source": {
          "id": ???,
          "name": "Pfam",
          "description": null,
          "url": "https://pfam.xfam.org",
          "release": 34
        },
        "accession_id": "PF00634",
        "name": "BRCA2 repeat",
        "url": "https://pfam.xfam.org/family/PF00634"
      },
      "via": {
        "source": {
          "id": ???,
          "name": "Interpro",
          "description": null,
          "url": "https://www.ebi.ac.uk/interpro",
          "release": null
        },
        "accession_id": "IPR002093",
        "url": "https://www.ebi.ac.uk/interpro/entry/InterPro/IPR002093/"
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
  ],
  "mappings": [
    {
      "source": {
        "id": ???,
        "name": "Uniprot",
        "description": null,
        "url": "https://www.uniprot.org/",
        "release": null
      },
      "accession_id": "P51587",
      "url": "https://www.uniprot.org/uniprot/P51587",
      "name": "Breast cancer type 2 susceptibility protein",
      "genomic_locations": [
        {
          "slice": { ... },
          "cigar_string": "..."
        }
      ],
      "relative_location": {
        "start": 25,
        "end": 106,
        "length": 82
      },
      "score": ???,
      "evalue": ???,
      "hit_location": {
        "start": 2,
        "end": 80,
        "length": 79
      },
    }
  ]
}
```

(notice that in the example above, the mapping to Uniprot has different lengths of `relative_location` and `hit_location`)


## RNA Product

To be completed in the future, when RNA products will receive identifiers in Ensembl databases.
