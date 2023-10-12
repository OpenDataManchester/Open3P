---
title: Load Constituents
description: The load constituents relationship list.
---

# Load Constituents

All the complete packaging from different levels (primary, secondary, transit etc.), and multipacks, put together to send to the final destination. Each row corresponds to a single packaging item.

The loads constituents relationship list identifies the all the complete packaging from different levels (primary, secondary, transit etc.) and multipacks that are combined to create loads. This is only used in [load](../3_Data_Specification/3_7_Load.md).

## Table
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|loadConstituentsIdentifier|`required`|String|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|loadCombinationIdentifier|`required`|String|The unique identifier of the items that this component is made of. There must be an equivalent record in the `Complete_Packaging` OR `Multipacks` data.|
|name|`recommended`|String|The name of this load constituent.|
|externalIdentifiers|`recommended`|Dictionary|A dictionary of identifiers that might be used to identify the load constituents in other systems. For example: manufacturer's own internal identifier, bar codes or global trade item number (gtin). To provide external identifiers please follow this format. `{'externalIdentifierName1': 'identifier1', 'externalIdentifierName2': 'identifier2'}`|
|quantityInLoad|`required`|Numeric|Number of units for the packaging items found in a load that this row corresponds to.|
|level|`required`|String|The intended use of the component for the packaging. The entry here should be drawn from the [level controlled list](../5_Controlled_Lists/5_015_Level.md).|

## Diagram

``` mermaid
erDiagram
  COMPLETE_PACKAGING }o..o{ LOAD_CONSTITUENTS : within
  MULTIPACKS }o..o{ LOAD_CONSTITUENTS : within
  LOAD_CONSTITUENTS {
    loadConstituentsIdentifier String
    loadCombinationIdentifier String
    name String
    externalIdentifiers Dictionary
    quantityInLoad Numeric
    level String
  }
  LOAD_CONSTITUENTS }o--o{ LOAD : attributes
  LOAD_CONSTITUENTS }o--o{ LOAD : within
  CONTROLLED_LISTS {
    level required
  }
```