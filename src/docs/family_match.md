# FamilyMatch

`FamilyMatch` contains information about a match between the [product](./product.md) sequence and a sequence from a known family recorded in an external database. It has the following fields:


| Field             | Type                         | Description |
|-------------------|------------------------------|-------------|
| sequence_family   | SequenceFamily               | See [SequenceFamily](./sequence_family.md)
| via               | ClosestDataProvider or null  | See [ClosestDataProvider](./closest_data_provider.md)
| relative_location | Location                     | `Location` within the product where the hit lands (see [Location](./location.md))
| hit_location      | Location or null             | `Location` within the family sequence that is matched to the `product` sequence (see [Location](./location.md))
| score             | float or null                | Analysis score asserting the presence of this match at this `location`
| evalue            | float or null                | Expectation value for the presence of this match at this `location`

1. For a match between an Ensembl `product` and an external feature, the location of the matching sequence within the Ensembl `product` is referred to here as `relative_location`, the location of the matching sequence within the external feature, as `hit_location`, and the projection of Ensembl `product`'s matching sequence onto genomic coordinates, as `genomic_location`.

![diagram of a match](https://user-images.githubusercontent.com/6834224/117651701-2805bd00-b18a-11eb-9569-a1a27ebcdc5b.png)

2. A [slice](./slice.md) associated with a single `genomic_location` can span multiple [exons](./exon.md); and the exact match is described using a CIGAR string in the `cigar_string` field. Because trans-splicing is possible, the `genomic_locations` field of a `Mapping` is an array.
3. A `relative_location` length may be the same as the `hit_location` length, or it may be different due to mismatches.


### Examples

```json
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
  "relative_location": {
    "start": 1003,
    "end": 1035,
    "length": 33,
    "location_modifier" : null
  },
  "hit_location": {
    "start": 1,
    "end": 33,
    "length": 33,
    "location_modifier" : null
  },
  "score": ???,
  "evalue": ???
}
```
