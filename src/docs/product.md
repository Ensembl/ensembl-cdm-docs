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


## Protein Domain

The `Protein Domain` data type has the following fields:

| Field            | Type              | Description |
|------------------|-------------------|-------------|
| id               | string            | Identifier for the protein domain
| name             | string            | Name of the protein domain
| resource_name    | string            | Name of the analysis or data provider for the protein domain
| location         | Location          | Location of the domain on the protein chain (see `Location`)
| hit_location     | Location or null  | Location within the domain that is matched to the protein chain (see `Location`)
| score            | float or null     | Analysis score asserting the presence of this domain at this location
| evalue           | float or null     | Expectation value for the presence of this domain at this location
| hit_description  | string or null    | Description of this protein domain hit 

