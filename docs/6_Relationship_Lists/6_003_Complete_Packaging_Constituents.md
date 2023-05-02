---
title: Complete Packaging Constituents
description: The complete packaging constituents relationship list.
---

# Complete Packaging Constituents

The complete packaging constituents relationship list identifies the componenets and other complete packaging that are combined to create complete packages. This is only used in [complete packaging](../3_Data_Specification/3_4_Complete_Packaging.md).

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|completePackagingConstituentsIdentifier|`required`|String|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|completePackagingCombinationIdentifier|`required`|String|The unique identifier of the components and/or complete packaging that this complete packaging is made of. There must be an equivalent record in the `Components` OR `Complete Packaging` data.|

## Diagram

``` mermaid
erDiagram

  COMPLETE_PACKAGING }o..o{ COMPLETE_PACKAGING_CONSTITUENTS : within
  COMPLETE_PACKAGING_CONSTITUENTS {
    completePackagingConstituentsIdentifier String
    completePackagingCombinationIdentifier String
  }
  COMPLETE_PACKAGING_CONSTITUENTS }o--o{ COMPONENTS : attributes
  COMPLETE_PACKAGING_CONSTITUENTS }o--o{ COMPLETE_PACKAGING : attributes
```