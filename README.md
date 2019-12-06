# example-netlist-management

This repository contains examples of using `Akamai Netlist as a Code` which enables automated management.

## Setup

### Initial synchronization of all lists

```shell
    akamai netlist get all | jq -r '.networkLists[].uniqueId' | xargs -I{} sh -c "akamai netlist get by-id --id {} --includeElements | jq -r '.list|.[]' > {}"
```

### Credentials required to execute actions
For running this commands you do need to specify credentials with at least required scope of network lists `READ/WRITE`

Snippet from .gitlab-ci.yaml shows that we setup credentials as base64 encoded value and store it for our pipeline under `AKAMAI_EDGE_CREDENTIALS` - therefore if you will decide to take this solution you need to populate this value

```shell
  - echo ${AKAMAI_EDGE_CREDENTIALS} | base64 -d > ${AKAMAI_EDGERC_CONFIG}
```
