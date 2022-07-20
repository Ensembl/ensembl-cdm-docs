# Product-Generating Context

The `Product-Generating Context` data type contains information about the specific arrangement of exons that results in a product. It has the following fields:

| Field         | Type                | Description |
|---------------|---------------------|-------------|
| product_type  | ProductType         | A string that denotes the type of the product that gets generated. See below.
| default       | boolean             | A flag indicating whether to treat this context as default
| cdna          | cDNA                | See [cDNA](./cdna.md)
| cds           | CDS or null         | See [CDS](./cds.md)
| 5_prime_utr   | UTR or null         | See [UTR](./utr.md)
| 3_prime_utr   | UTR or null         | See [UTR](./utr.md)
| product       | Product             | A protein or RNA product, see [Product](./product.md) and [ProteinProduct](./protein_product.md)
| phased_exons  | Array of PhasedExon | See [PhasedExon](./phased_exon.md)
| transcripts   | Array of Transcript | See [Transcript](./transcript.md)

## ProductType
`ProductType` is an enum of strings from a controlled vocabulary, such as `protein`, or `miRNA`.

## Rationale
By capturing the information about the arrangement of `exons` and the product that arises from it, the `Product-Generating Context` data type allows modelling a one-to-many relationship between the `Transcript` and the `Product`: one `Product-Generating Context` has one `Product`, but one `Transcript` can have multiple `Product-Generating Contexts`.

Note that `Product-Generating Context` is not intended to represent alternative splicing — this has been historically represented at Ensembl as different transcripts of a single gene. However, with `Product-Generating Context` it becomes possible to capture post-translational cleavage of a precursor polypeptide into several proteins, multiple initiation sites, or sequence edits.

## Notes
1. The purpose of the `product_type` field in `Product-Generating Context` is to signal which values in other fields to expect. For example, only if the `product_type` is `protein` will the `cds` field contain the `CDS` data; in all other cases it will be `null`.
2. To represent trans-splicing, a `product_generating_context` can be linked to multiple `transcript`s through `transcripts`.
3. `phased_exon`s will be present for all `product_generating_contexts` regardless of their product.

## Examples

### In a coding transcript

`Product-Generating Context` will have a non-empty `cds` field

```json
{
  "product_type": "protein",
  "default": true,
  "cdna": { ... },
  "cds": { ... },
  "5_prime_utr": { ... },
  "3_prime_utr": { ... },
  "product": { ... },
  "phased_exons": [
    { ... }
  ],
  "transcripts": [
    { ... }
  ]
}
```

### In a non-coding transcript

The `cds`, `5_prime_utr`, and `3_prime_utr` fields will be null.

```json
{
  "product_type": "miRNA",
  "default": true,
  "cdna": { ... },
  "cds": null,
  "5_prime_utr": null,
  "3_prime_utr": null,
  "product": { ... },
  "phased_exons": [
    { ... }
  ],
  "transcripts": [
    { ... }
  ]
}
```
