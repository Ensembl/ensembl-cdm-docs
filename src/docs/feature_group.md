# FeatureGroup

The `FeatureGroup` data type corresponds to a group of closely linked genetic features.

| Field               | Type              | Description
|---------------------|-------------------|-----------------------------------------
| name                | string            | The name provided by the assembly creator
| feature_group_code  | FeatureGroupCode  | See FeatureGroupCode below
| features            | array of Feature  | Array of Features (see Feature) belongs to this FeatureGroup



## FeatureGroupCode
FeatureGroupCode is an enum of strings with the following possible values:
- `ComplexLocus`

## Example
```
{
  "name": "UGT1A",
  "feature_group_code": "ComplexLocus",
  "features": [ ... ]
}
```
