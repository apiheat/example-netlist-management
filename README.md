# example-netlist-management

This repository contains examples of using `Akamai Netlist as a Code` which enables automated management.

## Setup

### Initial synchronization of all lists

```
    akamai netlist get all | jq -r '.networkLists[].uniqueId' | xargs -I{} sh -c "akamai netlist get by-id --id {} --includeElements | jq -r '.list|.[]' > {}"
```
