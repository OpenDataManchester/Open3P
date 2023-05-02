---
title: Material Constituents
description: The material constituents relationship list.
---

# Material Constituents

The material constituents relationship list identifies the base_material and other materials that are combined to create materials. This is only used in [materials](../3_Data_Specification/3_2_Materials.md).

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|materialConstituentsIdentifier|`required`|String|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|materialCombinationIdentifier|`required`|String|The unique identifier of the materials that this component is made of. There must be an equivalent record in the `Base_Materials` OR `Materials` data.|
|materialPurpose|`recommended`|String|Why is this base material or material being used? Use the identifier of the material purpose that this row relates to. The entry here should be drawn from the [Material Purpose Controlled List](../5_Controlled_Lists/5_003_Material_Purpose.md).|
|virginMaterial|`recommended`|Numeric|The maximum allowable percent of the material that was newly created for the material.|
|layer|`recommended`|Numeric|The layer associated with the material. The inner most layer (the layer closest to the product) denoted as 1, and the outermost layer is the biggest number.|
|materialPercentage|`recommended`|Numeric|The percentage of the total materials making-up the material. For every unique material, materialPercentage should add to 100%.|

## Diagram

``` mermaid
erDiagram

  MATERIALS }o..o{ MATERIAL_CONSTITUENTS : within
  MATERIAL_CONSTITUENTS {
    materialConstituentsIdentifier String
    materialCombinationIdentifier String
    materialPurpose String
    virginMaterial Numeric
    layer Numeric
    materialPercentage Numeric
  }
  MATERIAL_CONSTITUENTS }o--o{ CONTROLLED_LISTS : attributes
      CONTROLLED_LISTS {
    materialPurposeControlledList required }
  }
```