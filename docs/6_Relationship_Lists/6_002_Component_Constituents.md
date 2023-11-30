---
title: Component Constituents
description: The component constituents relationship list.
---

# Component Constituents

The component constituents relationship list identifies the materials that are combined to create components. This is only used in [components](../3_Data_Specification/3_3_Components.md).

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|componentConstituentsIdentifier|`required`|UUID|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|materialCombinationIdentifier|`required`|UUID|The unique identifier of the materials that this component is made of. There must be an equivalent record in the `Materials` OR `Components` data.|

## Diagram

``` mermaid
erDiagram
  COMPONENTS }o..o{ COMPONENT_CONSTITUENTS : within
  COMPONENT_CONSTITUENTS {
    componentConstituentsIdentifier UUID
    componentCombinationIdentifier UUID
  }
  COMPONENT_CONSTITUENTS }o--o{ MATERIALS : attributes
  COMPONENT_CONSTITUENTS }o--o{ COMPONENTS : attributes
```

## Template

Component constituents should be provided as a separate csv file. The specification of this csv file is as follows:

[Component Constituents Template](https://www.open3p.org/wp-content/uploads/2023/09/componentConstituents20230922.csv)