---
title: Multipack Constituents
description: The multipack constituents relationship list.
---

# Multipack Constituents

The multipack constituents relationship list identifies the complete packaging items that are combined to create multipacks. This is only used in [multipack](../3_Data_Specification/3_5_Multipack.md).

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|multipackConstituentsIdentifier|`mandatory`|UUID|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|multipackCombinationIdentifier|`mandatory`|UUID|The unique identifier of components and/or complete packaging that this multipack is made of. There must be an equivalent record in the `Components` OR `Complete Packaging` data.|
|identicalQuantity|`mandatory`|Integer|Number of identical units of the component and/or complete package that this multipack is made of.|

## Diagram

``` mermaid
erDiagram

  MULTIPACK }o..o{ MULTIPACK_CONSTITUENTS : within
  MULTIPACK_CONSTITUENTS {
    multipackConstituentsIdentifier UUID "*"
    multipackCombinationIdentifier UUID "*"
    identicalQuantity integer "*"
  }
  MULTIPACK_CONSTITUENTS }o--o{ COMPLETE_PACKAGING : attributes
  MULTIPACK_CONSTITUENTS }o--o{ COMPONENTS : attributes
```

## Template

Multipack constituents should be provided as a separate csv file.

The specification of this csv file is as follows:

[Multipack Constituents Template](https://www.open3p.org/wp-content/uploads/2023/09/multipackConstituents20230922.csv)