# Species

The Species data type contains information sufficient to describe a given species. It consists of the following fields:

| Field                     | Type                  | Description                               | 
|---------------------------|-----------------------|-------------------------------------------|
| scientific_name           | string                | Scientific name of the species.           
| ncbi_common_name          | string or null        | Common name of the species from NCBI.     
| ensembl_name              | string                | Ensembl's preferred name for the species.  This may be a common name (like dog); an abbreviated scientfic name (like E. coli); the full scientific name with additional information or anything else.       
| alternative_names         | array of strings      | Alternative names (if any)                 
| taxon_id                  | integer               | Taxonomic identifier. 


## Examples

1. Representation of Cow:

```json
{
  "scientific_name": "Bos taurus",
  "ncbi_common_name": "cattle",
  "ensembl_name": "cow",
  "alternative_names": ["bovine", "cow", "dairy cow", "domestic cattle", "domestic cow"],
  "taxon_id": 9913
}
```

2. Escherichia coli — notice that the ensembl_name field can now contain Ensembl's preferred abbreviated name

```json
{
  "scientific_name": "Escherichia coli str. K-12 substr. MG1655",
  "ncbi_common_name": null, 
  "ensembl_name": "E. coli K-12",
  "alternative_names": [],
  "taxon_id": 511145
}
```

3. Mus musculus castaneus

```json
{
  "scientific_name": "Mus musculus castaneus",
  "ncbi_common_name": "southeastern Asian house mouse", 
  "ensembl_name": "SE Asian house mouse",
  "alternative_names": [],
  "taxon_id": 10091
}
```

