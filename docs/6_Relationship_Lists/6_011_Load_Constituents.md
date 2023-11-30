---
title: Load Constituents
description: The load constituents relationship list.
---

# Load Constituents

The loads constituents relationship list identifies the all the complete packaging from different levels (primary, secondary, transit etc.) and multipacks that are combined to create loads. This is only used in [load](../3_Data_Specification/3_7_Load.md).

## Table
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|loadConstituentsIdentifier|`required`|UUID|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|loadCombinationIdentifier|`required`|UUID|The unique identifier of the items that this component is made of. There must be an equivalent record in the `Complete_Packaging` OR `Multipacks` data.|
|name|`recommended`|String|The name of this load constituent.|
|externalIdentifiers|`recommended`|Dictionary|A dictionary of identifiers that might be used to identify the load constituents in other systems. For example: manufacturer's own internal identifier, bar codes or global trade item number (gtin). To provide external identifiers please follow this format. `{'externalIdentifierName1': 'identifier1', 'externalIdentifierName2': 'identifier2'}`|
|quantityInLoad|`required`|Integer|Number of units for the packaging items found in a load that this row corresponds to.|
|level|`required`|String|The intended use of the component for the packaging. The entry here should be drawn from the [level controlled list](../5_Controlled_Lists/5_015_Level.md).|

## Diagram

``` mermaid
erDiagram
  COMPLETE_PACKAGING }o..o{ LOAD_CONSTITUENTS : attributes
  MULTIPACKS }o..o{ LOAD_CONSTITUENTS : attributes
  LOAD_CONSTITUENTS {
    loadConstituentsIdentifier UUID
    loadCombinationIdentifier UUID
    name String
    externalIdentifiers Dictionary
    quantityInLoad Integer
    level String
  }
  LOAD_CONSTITUENTS }o--o{ LOAD : within
  LOAD_CONSTITUENTS }o--o{ CONTROLLED_LISTS : attributes
  CONTROLLED_LISTS {
    level required
  }
```