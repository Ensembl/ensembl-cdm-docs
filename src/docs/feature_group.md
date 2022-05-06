# FeatureGroup

The `FeatureGroup` data type corresponds to a group of closely linked genetic features.

| Field               | Type              | Description
|---------------------|-------------------|-----------------------------------------
| name                | string            | The name provided by the assembly creator
| code                | string            | See Note below
| features            | array of Feature  | [Features](./feature.md) which are logically grouped together in this FeatureGroup for the reason specified by the code.



## Note
Code in FeatureGroup is an enum of strings with the following possible values:
- `ComplexLocus`

Other types of relationship/grouping can be added the list of possible codes above.

## Example
```json
{
  "name": "UGT1A",
  "code": "ComplexLocus",
  "features": [ ... ]
}
```
