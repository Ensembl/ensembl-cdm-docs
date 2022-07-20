# Product

The `Product` data type contains information about the mature functioning molecule produced from a [Gene Allele](./gene_allele.md). Depending on whether this molecule is a protein or an RNA, the Product is subdivided into a [ProteinProduct](./protein_product.md) and, in the future, an [RNAProduct](./rna_product.md).

Both `ProteinProduct` and the `RNAProduct` will have the following fields in common:

| Field                       | Type                          | Description |
|-----------------------------|-------------------------------|-------------|
| type                        | string                        | Type of the product (e.g. "Protein" or "RNA")
| length                      | integer                       | Number of subunits (amino acids for proteins, nucleotides for RNA) comprising the product
| external_references         | array of ExternalReference    | See [ExternalReference](./external_reference.md)
| sequence                    | Sequence                      | See [Sequence](./sequence.md)
| metadata                    | Metadata                      | See [Metadata](./metadata.md)
| product_generating_context  | ProductGeneratingContext      | See [ProductGeneratingContext](./product_generating_context.md)




## Notes
1. An RNA product is a mature RNA, which can be described by its [cDNA](./cdna.md). Since `cDNAs` do not have stable ids in Ensembl, RNA products are unlikely to have stable ids either.
2. RNA product do not currently exist in the model
