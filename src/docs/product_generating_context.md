# Product-Generating Context

_provisional name; very much in search of a better one_

The `Product-Generating Context` data type contains information about the specific arrangement of exons that results in a product. It has the following fields:

| Field         | Type         | Description |
|---------------|--------------|-------------|
| product_type  | ProductType  | a string that denotes the type of the product that gets generated
| default       | boolean      | a flag indicating whether to treat this context as default
| cds           | CDS or null  | see `CDS`
| 5_prime_utr   | UTR or null  | see `UTR`
| 3_prime_utr   | UTR or null  | see `UTR`
| product       | Product      | a protein or RNA product, see `Product`
| phased_exons  | PhasedExon   | see `PhasedExon`

## ProductType
`ProductType` is an enum of strings from a controlled vocabulary, such as `protein`, or `miRNA`.

## Rationale
By capturing the information about the arrangement of exons and the product that arises from it, the `Product-Generating Context` data type allows modelling a one-to-many relationship between the `Transcript` and the `Product`: one `Product-Generating Context` has one `Product`, but one `Transcript` can have multiple `Product-Generating Context`s.

Note that `Product-Generating Context` is not intended to represent alternative splicing — this has been historically represented at Ensembl as different transcripts of a single gene. However, with `Product-Generating Context` it becomes possible to capture post-translational cleavage of a precursor polypeptide into several proteins, multiple initiation sites, or sequence edits.

## Notes
1. The purpose of the `product_type` field in `Product-Generating Context` is to signal which values in other fields to expect. For example, only if the `product_type` is `protein` will the `cds` field contain the `CDS` data; in all other cases it will be `null`.
