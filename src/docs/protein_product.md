# ProteinProduct

In addition to the fields common for all [Products](./product.md), a ProteinProduct will have the following fields:

| Field                 | Type                          | Description |
|-----------------------|-------------------------------|-------------|
| stable_id             | string                        | Unique identifier for the product (versioned)
| unversioned_stable_id | string                        | Unversioned unique identifier for the product
| version               | integer or null               | Version of the product
| family_matches        | array of FamilyMatch          | See [FamilyMatch](./family_match.md)
| mappings              | array of Mapping              | See [Mapping](./mapping.md)

## Examples

```json
{
  "type": "protein",
  "length": 3418,
  "external_references": [],
  "sequence": { ... },
  "metadata": { ... },
  "product_generating_context": { ... },
  "stable_id": "ENSP00000369497.3",
  "unversioned_stable_id": "ENSP00000369497",
  "version": 3,
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
      "relative_location": {
        "start": 1003,
        "end": 1035,
        "length": 33
      },
      "hit_location": {
        "start": 1,
        "end": 33,
        "length": 33
      },
      "score": ???,
      "evalue": ???
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
      "relative_location": {
        "start": 25,
        "end": 106,
        "length": 82
      },
      "hit_location": {
        "start": 2,
        "end": 80,
        "length": 79
      },
      "genomic_locations": [
        {
          "slice": { ... },
          "cigar_string": "..."
        }
      ],
      "score": ???,
      "evalue": ???,
    }
  ]
}
```

(notice that in the example above, the mapping to Uniprot has different lengths of `relative_location` and `hit_location`)
