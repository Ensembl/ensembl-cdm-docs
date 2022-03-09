# Product

The Product data type contains information about the mature functioning molecule produced from a Gene. Depending on whether this molecule is a protein or an RNA, the Product is subdivided into a [ProteinProduct](./protein_product.md) and, in the future, an RNAProduct.

Both ProteinProduct and the RNAProduct will have the following fields in common:

| Field                       | Type                          | Description |
|-----------------------------|-------------------------------|-------------|
| type                        | string                        | Type of the product (e.g. "Protein" or "RNA")
| length                      | integer                       | Number of subunits (amino acids for proteins, nucleotides for RNA) comprising the product
| external_references         | array of ExternalReference    | See [ExternalReference](./external_reference.md)
| sequence                    | Sequence                      | See [Sequence](./sequence.md)
| metadata                    | Metadata                      | See [Metadata](./metadata.md)
| product_generating_context  | ProductGeneratingContext      | See [ProductGeneratingContext](./product_generating_context.md)




## Notes
1. An RNA product is a mature RNA, which can be described by its cDNA. Since cDNAs don't have stable ids in Ensembl, RNA products are unlikely to have stable ids either.
2. RNA product do not currently exist in the model
3. For a match between an Ensembl product and an external feature, the location of the matching sequence within the Ensembl product is referred to here as `relative_location`, the location of the matching sequence within the external feature, as `hit_location`, and the projection of Ensembl product's matching sequence onto genomic coordinates, as `genomic_location`.

![diagram of a match](https://user-images.githubusercontent.com/6834224/117651701-2805bd00-b18a-11eb-9569-a1a27ebcdc5b.png)

4. A `slice` associated with a single `genomic_location` can span multiple exons; and the exact match is described using a CIGAR string in the `cigar_string` field. Because trans-splicing is possible, the `genomic_locations` field of a `Mapping` is an array.
5. A `relative_location` length may be the same as the `hit_location` length, or it may be different due to mismatches.


## Example

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
