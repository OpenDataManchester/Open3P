---
title: Component Constituents
description: The component constituents relationship list.
---

# Component Constituents

The component constituents relationship list identifies the materials that are combined to create components. This is only used in [components](../3_Data_Specification/3_3_Components.md).

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|componentConstituentsIdentifier|`required`|String|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|materialIdentifier|`required`|String|The unique identifier of the materials that this component is made of. There must be an equivalent record in the `Materials` data.|