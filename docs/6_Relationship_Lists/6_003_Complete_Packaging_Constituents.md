---
title: Complete Packaging Constituents
description: The complete packaging constituents relationship list.
---

# Complete Packaging Constituents

The complete packaging constituents relationship list identifies the components and other complete packaging that are combined to create complete packages. This is only used in [complete packaging](../3_Data_Specification/3_4_Complete_Packaging.md).

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|completePackagingConstituentsIdentifier|`required`|UUID|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|completePackagingCombinationIdentifier|`required`|UUID|The unique identifier of the components and/or complete packaging that this complete packaging is made of. There must be an equivalent record in the `Components` OR `Complete Packaging` data.|
|contactWithProduct|`required`|Boolean|Does this constituent come into contact with the product? Answer as: `TRUE` for yes and `FALSE` for no.|

## Diagram

``` mermaid
erDiagram

  COMPLETE_PACKAGING }o..o{ COMPLETE_PACKAGING_CONSTITUENTS : within
  COMPLETE_PACKAGING_CONSTITUENTS {
    completePackagingConstituentsIdentifier UUID
    completePackagingCombinationIdentifier UUID
    contactWithProduct Boolean
  }
  COMPLETE_PACKAGING_CONSTITUENTS }o--o{ COMPONENTS : attributes
  COMPLETE_PACKAGING_CONSTITUENTS }o--o{ COMPLETE_PACKAGING : attributes
```

## Template

Complete packaging constituents should be provided as a separate csv file. The specification of this csv file is as follows:

[Complete Packaging Constituents](https://www.open3p.org/wp-content/uploads/2023/09/completePackagingConstituent20230922.csv)