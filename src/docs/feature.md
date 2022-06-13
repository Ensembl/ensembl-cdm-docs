# Feature

Feature is an abstract representation which other feature-like entities (e.g. Gene, Transcript etc.) can inherit from.

| Field                 | Type                  | Description                         |
|-----------------------|-----------------------|-------------------------------------|
| stable_id             | string or null        | A unique identifier for the feature, which is versioned if a version is available
| version               | integer or null       | Version of the feature
| unversioned_stable_id | string or null        | Unversioned unique identifier for the feature
| type                  | string                | This is the feature type (e.g. Gene, Transcript etc.)
| metadata              | various               | See [metadata](./metadata.md)
| slice                 | Slice or null         | Slice describing the coordinates of the feature, if present
| feature_groups        | array of FeatureGroup | see FeatureGroup

## Notes
1. Features can implement a method `sequence` as a shortcut to obtain the sequence.
3. Concepts which are features include:
 - Gene
 - Exon
 - Intron
 - Transcript
