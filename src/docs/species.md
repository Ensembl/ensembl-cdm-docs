# Species

The Species data type contains information sufficient to describe a given species. It consists of the following fields:

| Field                     | Type                  | Description                               | 
|---------------------------|-----------------------|-------------------------------------------|
| scientific_name           | string                | Scientific name of the species.           
| ncbi_common_name          | string or null        | Common name of the species from NCBI.     
| ensembl_name              | string                | Preferred name for display purposes, which can be the same as NCBI's common name       
| alternative_names         | array of strings      | Alternative names (if any)                 
| taxon_id                  | integer               | Taxonomic identifier. 
| species_groups            | array of SpeciesGroup | Array of SpeciesGroup describing taxonomic groupings relating to the species


# SpeciesGroup

The SpeciesGroup data type contains information relating to taxonomy:

| Field         | Type                   | Description                               | 
|---------------|------------------------|-------------------------------------------|
| id            | string                 | ID for the species group           
| type          | string                 | Type of the species group   
| name          | string                 | Name of the species group     


## Examples

1. Representation of Cow:

```json
{
  "scientific_name": "Bos taurus",
  "ncbi_common_name": "cattle",
  "ensembl_name": "cow",
  "alternative_names": ["bovine", "cow", "dairy cow", "domestic cattle", "domestic cow"],
  "taxon_id": 9913,
  "species_groups" : []
}
```

2. Escherichia coli — notice that the ensembl_name field can now contain Ensembl's preferred abbreviated name

```json
{
  "scientific_name": "Escherichia coli str. K-12 substr. MG1655",
  "ncbi_common_name": null, 
  "ensembl_name": "E. coli K-12",
  "alternative_names": [],
  "taxon_id": 511145,
  "species_groups": []
}
```

3. Mus musculus castaneus

```json
{
  "scientific_name": "Mus musculus castaneus",
  "ncbi_common_name": "southeastern Asian house mouse", 
  "ensembl_name": "SE Asian house mouse",
  "alternative_names": [],
  "taxon_id": 10091,
  "species_groups": [ 
  {
    "id": "subspecies",
    "type": "subspecies",
    "name": "subspecies"
  }]
}
```

