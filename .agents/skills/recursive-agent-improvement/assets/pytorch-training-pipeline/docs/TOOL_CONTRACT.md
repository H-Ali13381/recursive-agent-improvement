# Agent Tool Contract

## Purpose

Define the callable interface before implementing serving code.

## Input JSON

```json
{
  "input": null,
  "options": {}
}
```

## Output JSON

```json
{
  "success": true,
  "label": null,
  "score": null,
  "confidence": null,
  "reasons": [],
  "recommended_action": null,
  "metadata": {}
}
```

## Error JSON

```json
{
  "success": false,
  "error": "machine-readable-error-code",
  "message": "human readable explanation",
  "metadata": {}
}
```

## Latency budget

TODO

## Resource budget

TODO

## Abstention behavior

TODO

## Examples

TODO
