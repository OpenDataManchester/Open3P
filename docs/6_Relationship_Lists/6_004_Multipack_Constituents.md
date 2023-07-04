---
title: Multipack Constituents
description: The multipack constituents relationship list.
---

# Multipack Constituents

The multipack constituents relationship list identifies the complete packaging items that are combined to create multipacks. This is only used in [multipack](../3_Data_Specification/3_5_Multipack.md).

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|multipackConstituentsIdentifier|`required`|String|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|multipackCombinationIdentifier|`required`|String|The unique identifier of components and/or complete packaging that this multipack is made of. There must be an equivalent record in the `Components` OR `Complete Packaging` data.|

## Diagram

``` mermaid
erDiagram

  MULTIPACK }o..o{ MULTIPACK_CONSTITUENTS : within
  MULTIPACK_CONSTITUENTS {
    multipackConstituentsIdentifier String
    multipackCombinationIdentifier String
  }
  MULTIPACK_CONSTITUENTS }o--o{ COMPLETE_PACKAGING : attributes
  MULTIPACK_CONSTITUENTS }o--o{ COMPONENTS : attributes
```