# LocationModifier


| Field                     | Type                        | Description |
|---------------------------|-----------------------------|-------------|
| partial_start             | boolean                     | defines whether or not the feature has a partial start
| partial_end               | boolean                     | defines whether or not the feature has a partial end


## Notes
LocationModifier will be used to handle the following:

```
<1..888       The feature starts before the first sequenced base and
              continues to and includes base 888
```

In the above snippet, the `start` coordinate in Location would be 888 and `partial_start` in LocationModifier would be set to true.


## Example

```json
{
  "partial_start": true,
  "partial_end": false    
}
```
