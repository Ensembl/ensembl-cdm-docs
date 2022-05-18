# Species

The `Species` data type consists of the following fields:

| Field                     | Type                                    | Description                                           |
|---------------------------|-----------------------------------------|-------------------------------------------------------|
| scientific_name           | string                                  | Scientific name of the species.           
| ncbi_common_name          | string or null                          | Common name of the species from NCBI taxonomy service.        
| alternative_names         | array of strings                        | Alternative names (if any)                 
| taxon_id                  | integer                                 | Taxonomic identifier.
| organisms                 | array of [Organism](./organism.md)      | The organisms linked to the species


## Examples

1. Representation of Cow:

```json
{
  "scientific_name": "Bos taurus",
  "ncbi_common_name": "cattle",
  "alternative_names": ["bovine", "cow", "dairy cow", "domestic cattle", "domestic cow"],
  "taxon_id": 9913,
  "organisms": [...]
}
```

2. Escherichia coli

```json
{
  "scientific_name": "Escherichia coli str. K-12 substr. MG1655",
  "ncbi_common_name": null,
  "alternative_names": [],
  "taxon_id": 511145,
  "organisms": [...]
}
```

3. Pieris rapae

```json
{
  "scientific_name": "Pieris rapae",
  "ncbi_common_name": "cabbage white",
  "alternative_names": [ "small cabbage white", "small white", "european cabbage white"],
  "taxon_id": 64459,
  "organisms": [...]
}
```

4. Trypanosoma rangeli SC58 (only scientific_name provided)

```json
{
  "scientific_name": "Trypanosoma rangeli SC58",
  "ncbi_common_name": null,
  "alternative_names": [],
  "taxon_id": 429131,
  "organisms": [...]
}
```
