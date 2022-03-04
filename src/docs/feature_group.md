# FeatureGroup

The `FeatureGroup` data type corresponds to a group of closely linked genetic features.

| Field               | Type              | Description
|---------------------|-------------------|-----------------------------------------
| name                | string            | The name provided by the assembly creator
| code                | string            | See Note below
| features            | array of Feature  | Array of Features (see Feature) belongs to this FeatureGroup



## Note
Code in FeatureGroup is an enum of strings with the following possible values:
- `ComplexLocus`

## Example
```
{
  "name": "UGT1A",
  "code": "ComplexLocus",
  "features": [ ... ]
}
```
