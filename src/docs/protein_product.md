# ProteinProduct

In addition to the fields common for all [Products](./product.md), a ProteinProduct will have the following fields:

| Field                 | Type                          | Description |
|-----------------------|-------------------------------|-------------|
| stable_id             | string                        | Unique identifier for the product (versioned)
| unversioned_stable_id | string                        | Unversioned unique identifier for the product
| version               | integer or null               | Version of the product
| family_matches        | array of FamilyMatch`         | See [FamilyMatch](./family_match.md)
| mappings              | array of Mapping              | See [Mapping](./mapping.md)
