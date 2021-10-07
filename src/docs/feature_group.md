# FeatureGroup

The `FeatureGroup` data type corresponds to a group of closely linked genetic features.

| Field             | Type              | Description
|-------------------|-------------------|-----------------------------------------
| name              | string            | The name provided by the assembly creator
| type              | FeatureGroupType  |
| Features          | array of Feature  | Array of Features (see Feature) belongs to this FeatureGroup



## FeatureGroupType
FeatureGroupType is an enum of strings with the following possible values:
- `ComplexLocus`

## Example
```
{
  "name": "UGT1A",
  "type": "ComplexLocus",
  "features": [ ... ]
}
```
