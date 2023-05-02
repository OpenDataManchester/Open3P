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
  MATERIAL_CONSTITUENTS }o--o{ BASE_MATERIALS : attributes
  MATERIAL_CONSTITUENTS }o--o{ MATERIALS : attributes
  MATERIAL_CONSTITUENTS }o--o{ CONTROLLED_LISTS : attributes
      CONTROLLED_LISTS {
    materialPurposeControlledList required }
  }
```

## Example

=== "JSON #1"

    ``` json linenums="1"
    --Fibre based composite Polyethylene, EVOH, Paper multi layer
    {
      [
        {
          "materialConstituentsIdentifier": "f87b9bb3-f141-41cf-986e-e3a32b223f09",
          "materialCombinationIdentifier": "3ca24db2-84d5-4681-aa16-136fbdba101f",
          "materialPurpose": "m-material-purpose-0005",
          "virginMaterial": 100,
          "layer": 1,
          "materialPercentage": 7
        },
        {
          "materialConstituentsIdentifier": "f87b9bb3-f141-41cf-986e-e3a32b223f09",
          "materialCombinationIdentifier": "96245c85-5671-4f3d-875f-82665005e9e8",
          "materialPurpose": "m-material-purpose-0015",
          "virginMaterial": 100,
          "layer": 2,
          "materialPercentage": 27
        },
        {
          "materialConstituentsIdentifier": "f87b9bb3-f141-41cf-986e-e3a32b223f09",
          "materialCombinationIdentifier": "3ca24db2-84d5-4681-aa16-136fbdba101f",
          "materialPurpose": "m-material-purpose-0002",
          "virginMaterial": 100,
          "layer": 3,
          "materialPercentage": 7
        },
        {
          "materialConstituentsIdentifier": "f87b9bb3-f141-41cf-986e-e3a32b223f09",
          "materialCombinationIdentifier": "ff249e1f-5015-46b8-8655-6c920fbf2606",
          "materialPurpose": "m-material-purpose-0003",
          "virginMaterial": 100,
          "layer": 4,
          "materialPercentage": 18
        },
        {
          "materialConstituentsIdentifier": "f87b9bb3-f141-41cf-986e-e3a32b223f09",
          "materialCombinationIdentifier": "3ca24db2-84d5-4681-aa16-136fbdba101f",
          "materialPurpose": "m-material-purpose-0002",
          "virginMaterial": 100,
          "layer": 5,
          "materialPercentage": 7
        },
        {
          "materialConstituentsIdentifier": "f87b9bb3-f141-41cf-986e-e3a32b223f09",
          "materialCombinationIdentifier": "96245c85-5671-4f3d-875f-82665005e9e8",
          "materialPurpose": "m-material-purpose-0015",
          "virginMaterial": 100,
          "layer": 6,
          "materialPercentage": 27
        },
        {
          "materialConstituentsIdentifier": "f87b9bb3-f141-41cf-986e-e3a32b223f09",
          "materialCombinationIdentifier": "3ca24db2-84d5-4681-aa16-136fbdba101f",
          "materialPurpose": "m-material-purpose-0005",
          "virginMaterial": 100,
          "layer": 7,
          "materialPercentage": 7
        },
      ]
    } 
    ```
=== "JSON #2"

    ``` json linenums="1"
    --Cellulose - verbose data structure
    {
      "materialConstituentsIdentifier": "a4ef4dec-eceb-417d-bded-9bd1e305a440",
      "materialCombinationIdentifier": {
        "identifier": "m-material-purpose-0015",
        "baseMaterialName": "Cellulose",
        "baseMaterialType": {
          "identifier": "bm-material-type-0001",
          "category": "biobased",
          "detailed": "from renewable products such as carbohydrates, starch, vegetable fats and oils, bacteria and other biological substances."
        },
        "baseMaterialType": "bm-material-type-0001",
        "materialChemCID": "14055602"
      },
      "materialPurpose":{
        "identifier": "m-material-purpose-0015",
        "category": "structure",
        "detailed": "Providing strength and stability."
      },
      "virginMaterial": 100,
      "layer": null,
      "materialPercentage": 100
    }