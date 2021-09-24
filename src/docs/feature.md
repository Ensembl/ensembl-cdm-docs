# Feature

Feature is an abstract represetnation which other feature-like entities (e.g. Gene, Transcript etc.) can inherit from. 

| Field                 | Type                | Description                         |
|-----------------------|---------------------|-------------------------------------|
| stable_id             | string              | A unique identifier for the feature, which is versioned if a version is available
| version               | integer or Null     | Version of the feature
| unversioned_stable_id | string              | Unversioned unique identifier for the feature
| type                  | string              | This is the feature type (e.g. Gene, Transcript etc.)
| metadata              | various             | See [feature_metadata](./feature_metadata.md)
| localised             | boolean             | Flag for whether or not a feature has a slice 
| slice                 | Slice or Null       | Slice describing the coordinates of the feature, if present

## Notes
1. localised flag allows features such as genes in a pangenome context to exist without requiring a slice.  If it is set to true, then slice should contain a Slice.  If the flag is false, then slice will be null.

