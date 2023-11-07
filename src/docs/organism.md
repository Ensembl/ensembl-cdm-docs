# Organism

The `Organism` data type contains information sufficient to describe an abstract representation of a `Species` member.  Organism augments the data provided by [Species](./species.md) and allows assemblies, genes set, analysis for entities to be grouped and named in Ensembl services. Therefore, in Ensembl, multiple `organisms` can exists for the same `species`, such as breeds, strains, cell lines, even (anonymised) individuals

It consists of the following fields:

| Field                     | Type                                                        | Description                               |
|---------------------------|-------------------------------------------------------------|-------------------------------------------|
| scientific_name           | string                                                      | Scientific name of the species.           
| scientific_parlance_name  | string or null                                              | Preferred name for the organism within the scientific domain.
| species                   | [Species](./species.md)                                     | The related NCBI species
| id                        | string                                                      | A unique identifier for an `organism`
| groups                    | array of [OrganismGroup](./organism_group.md)               | An array of `OrganismGroups` to provide additional information about the `organism`
| assemblies                | array of [Assembly](./assembly.md)                          | An array of `Assemblies` for the `Organism`
| is_reference_organism     | Boolean                                                     | Indicates that the `organism` is the reference for a particular `OrganismGroup`
| tolid                     | string or null                                              | Tree of Life Identifier (ToLID) for the organism

Note: The field `is_reference_organism` is only present if `Organism` is accessed from an `OrganismGroup`.  If the `Organism` is referenced directly, this field will not be present.


### Notes:
- `id` will be a UUID


## Examples

1.a. Representation of Cow:

```json
{
  "scientific_name": "Bos taurus",
  "scientific_parlance_name": "cow",
  "id": "37d98713-f25a-4f21-8d2c-0b67fbf5e110",
  "species": {
    "scientific_name": "Bos taurus",
    "ncbi_common_name": "cattle",
    "alternative_names": ["bovine", "cow", "dairy cow", "domestic cattle", "domestic cow"],
    "taxon_id": 9913
  },
 "groups": [
  {
      "code": "hereford_breed",
      "type": "breed",
      "name": "Hereford",
      "is_reference_organism": "true",
      "organisms": [...]
    },
    {
      "code": "farmed_animals",
      "type": "population",
      "name": "Farmed Animals",
      "is_reference_organism": "false",
      "organisms": [...]
    }],
  "assemblies" : [...],
  "tolid" : "mBosTau1"
 }
```

1.b. Representation of a breed group for a Cow:

```json
{
    "code": "hereford_breed",
    "type": "breed",
    "name": "Hereford",
    "organisms":[
        {
          "scientific_name": "Bos taurus",
          "scientific_parlance_name": "cow",
          "id": "827e1fef-74a1-4e9f-ba5a-655f914104d8",
          "groups": [...],
          "assemblies" : [...],
          "tolid" : "mBosTau1",
          "is_reference_organism": "true",
          "species": {
            "scientific_name": "Bos taurus",
            "ncbi_common_name": "cattle",
            "alternative_names": ["bovine", "cow", "dairy cow", "domestic cattle", "domestic cow"],
            "taxon_id": 9913
         }},
        {...}]
  }

```


2. Escherichia coli — notice that the `scientific_parlance_name` field can now contain Ensembl's preferred abbreviated name

```json
{
  "scientific_name": "Escherichia coli str. K-12 substr. MG1655",
  "scientific_parlance_name": "E. coli K-12",
  "id": "b30cfcbc-2ff3-494d-8474-a38e59f1ce74",
  "species": {
    "scientific_name": "Escherichia coli str. K-12 substr. MG1655",
    "ncbi_common_name": null,
    "alternative_names": [],
    "taxon_id": 511145
  },
  "groups" : [...],
  "assemblies" : [...],
}
```

3. Pieris rapae (no `scientific_parlance_name` provided)

```json
{
  "scientific_name": "Pieris rapae",
  "scientific_parlance_name": null,
  "id": "acc1e46c-21cb-4827-a064-5d717a3e6a89",
  "species": {
    "scientific_name": "Pieris rapae",
    "ncbi_common_name": "cabbage white",
    "alternative_names": ["small cabbage white", "small white", "european cabbage white"],
    "taxon_id": 64459
  },
  "groups" : [...],
  "assemblies" : [...],
  "tolid" : "ilPieRapa1"

}
```

4. Trypanosoma rangeli SC58 (only `scientific_name` provided)

```json
{
  "scientific_name": "Trypanosoma rangeli SC58",
  "scientific_parlance_name": null,
  "id": "8c95ec4c-12d7-4c1d-959a-f164311b7967"
  "species": {
    "scientific_name": "Trypanosoma rangeli SC58",
    "ncbi_common_name": null,
    "alternative_names": [],
    "taxon_id": 429131
  },
  "groups" : [...],
  "assemblies" : [...]
}
```
