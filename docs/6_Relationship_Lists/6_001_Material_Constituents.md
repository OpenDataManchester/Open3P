---
title: Material Constituents
description: The material constituents relationship list.
---

# Material Constituents

The material constituents relationship list identifies the base_material and other materials that are combined to create materials. This is only used in [materials](../3_Data_Specification/3_2_Materials.md).

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|materialConstituentsIdentifier|`mandatory`|UUID|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|materialCombinationIdentifier|`mandatory`|UUID|The unique identifier of the materials that this component is made of. There must be an equivalent record in the `Base_Materials` OR `Materials` data.|
|materialPurpose|`optional`|String|Why is this base material or material being used? Use the identifier of the material purpose that this row relates to. The entry here should be drawn from the [Material Purpose Controlled List](../5_Controlled_Lists/5_003_Material_Purpose.md).|
|virginMaterial|`optional`|Decimal|The maximum allowable percent of the material that was newly created for the material.|
|layer|`optional`|Integer|The layer associated with the material. The inner most layer (the layer closest to the product) denoted as 1, and the outermost layer is the biggest number.|
|materialPercentage|`optional`|Decimal|The percentage of the total materials making-up the material. For every unique material, materialPercentage should add to 100%.|

## Diagram

``` mermaid
erDiagram

  MATERIALS }o..o{ MATERIAL_CONSTITUENTS : within
  MATERIAL_CONSTITUENTS {
    materialConstituentsIdentifier UUID "*"
    materialCombinationIdentifier UUID "*"
    materialPurpose String
    virginMaterial Decimal
    layer Integer
    materialPercentage Decimal
  }
  MATERIAL_CONSTITUENTS }o--o{ BASE_MATERIALS : attributes
  MATERIAL_CONSTITUENTS }o--o{ MATERIALS : attributes
  MATERIAL_CONSTITUENTS }o--o{ CONTROLLED_LISTS : attributes
  CONTROLLED_LISTS {
    materialPurposeControlledList mandatory 
  }
```

## Example

=== "Cardboard - JSON"

    ``` json linenums="1" hl_lines="3 4"
    [
      {
        "materialConstituentsIdentifier": "95b95bf7-80c0-49bc-9367-ae48d6c107d3",
        "materialCombinationIdentifier": "222494f7-6703-49bc-a993-8dd2675709fb",
        "materialPurpose": "m-material-purpose-0015",
        "virginMaterial": 70.0,
        "materialPercentage": 100.0
      }
    ]
    ```
=== "Glass - JSON"

    ``` json linenums="1" hl_lines="3 4"
    [
      {
        "materialConstituentsIdentifier": "11eb7b61-05f1-4894-a57b-80e5082f944a",
        "materialCombinationIdentifier": "ff39892f-0a88-4085-9942-4522cecc8337",
        "materialPurpose": "m-material-purpose-0015",
        "virginMaterial": 100.00,
        "materialPercentage": 10.0
      },
            {
        "materialConstituentsIdentifier": "11eb7b61-05f1-4894-a57b-80e5082f944a",
        "materialCombinationIdentifier": "db481bb7-e57a-4af7-8821-2258338ddd11",
        "materialPurpose": "m-material-purpose-0015",
        "virginMaterial": 0.0,
        "materialPercentage": 70.0
      },
      {
        "materialConstituentsIdentifier": "11eb7b61-05f1-4894-a57b-80e5082f944a",
        "materialCombinationIdentifier": "1bdca07b-ed6a-4799-a027-654322cb302f",
        "materialPurpose": "m-material-purpose-0015",
        "virginMaterial": 100.0,
        "materialPercentage": 15.0
      },
      {
        "materialConstituentsIdentifier": "11eb7b61-05f1-4894-a57b-80e5082f944a",
        "materialCombinationIdentifier": "42b19543-7138-43ff-a867-a1e551ccba14",
        "materialPurpose": "m-material-purpose-0016",
        "virginMaterial": 70.0,
        "materialPercentage": 5.0
      }
    ]
    ```
=== "Cardboard - XML"

    ``` xml linenums="1" hl_lines="3 4"
    <?xml version="1.0" encoding="UTF-8" ?>
      <materialConstituents>
        <materialConstituentsIdentifier>95b95bf7-80c0-49bc-9367-ae48d6c107d3</materialConstituentsIdentifier>
        <materialCombinationIdentifier>222494f7-6703-49bc-a993-8dd2675709fb</materialCombinationIdentifier>
        <materialPurpose>m-material-purpose-0015</materialPurpose>
        <virginMaterial>70</virginMaterial>
        <materialPercentage>100</materialPercentage>
      </materialConstituents>
    ```
=== "Glass - XML"

    ``` xml linenums="1" hl_lines="3 4"
    <?xml version="1.0" encoding="UTF-8" ?>
      <materialConstituents>
        <materialConstituentsIdentifier>11eb7b61-05f1-4894-a57b-80e5082f944a</materialConstituentsIdentifier>
        <materialCombinationIdentifier>ff39892f-0a88-4085-9942-4522cecc8337</materialCombinationIdentifier>
        <materialPurpose>m-material-purpose-0015</materialPurpose>
        <virginMaterial>100</virginMaterial>
        <materialPercentage>10</materialPercentage>
      </materialConstituents>
      <materialConstituents>
        <materialConstituentsIdentifier>11eb7b61-05f1-4894-a57b-80e5082f944a</materialConstituentsIdentifier>
        <materialCombinationIdentifier>db481bb7-e57a-4af7-8821-2258338ddd11</materialCombinationIdentifier>
        <materialPurpose>m-material-purpose-0015</materialPurpose>
        <virginMaterial>0</virginMaterial>
        <materialPercentage>70</materialPercentage>
      </materialConstituents>
      <materialConstituents>
        <materialConstituentsIdentifier>11eb7b61-05f1-4894-a57b-80e5082f944a</materialConstituentsIdentifier>
        <materialCombinationIdentifier>1bdca07b-ed6a-4799-a027-654322cb302f</materialCombinationIdentifier>
        <materialPurpose>m-material-purpose-0015</materialPurpose>
        <virginMaterial>100</virginMaterial>
        <materialPercentage>15</materialPercentage>
      </materialConstituents>
      <materialConstituents>
        <materialConstituentsIdentifier>11eb7b61-05f1-4894-a57b-80e5082f944a</materialConstituentsIdentifier>
        <materialCombinationIdentifier>42b19543-7138-43ff-a867-a1e551ccba14</materialCombinationIdentifier>
        <materialPurpose>m-material-purpose-0016</materialPurpose>
        <virginMaterial>70</virginMaterial>
        <materialPercentage>5</materialPercentage>
      </materialConstituents>
    ```

## Data flow

``` mermaid
flowchart LR
    subgraph baseMaterials[Base Materials]
        bm_cardboard["Cardboard
        -
        222494f7-6703-49bc-a993-8dd2675709fb"]
        bm_sodaAsh["Soda ash
        -
        ff39892f-0a88-4085-9942-4522cecc8337"]
        bm_cullet["Cullet
        -
        db481bb7-e57a-4af7-8821-2258338ddd11"]
        bm_sand["Sand
        -
        1bdca07b-ed6a-4799-a027-654322cb302f"]
        bm_limestone["Limestone
        -
        42b19543-7138-43ff-a867-a1e551ccba14"]
    end
    subgraph materialConstituents["`**Material Constituents**`"]
        subgraph mcs_cardboard ["`**Cardboard Constituents**`"]
          mc_cardboard["`**95b95bf7-80c0-49bc-9367-ae48d6c107d3
          -
          materialPercentage: 100%**`"]
        end
        subgraph mcs_glass ["`**Glass Constituents**`"]
          mc_sodaAsh["`**11eb7b61-05f1-4894-a57b-80e5082f944a
          -
          materialPercentage: 10%**`"]
          mc_cullet["`**11eb7b61-05f1-4894-a57b-80e5082f944a
          -
          materialPercentage: 70%**`"]
          mc_sand["`**11eb7b61-05f1-4894-a57b-80e5082f944a
          -
          materialPercentage: 15%**`"]
          mc_limestone["`**11eb7b61-05f1-4894-a57b-80e5082f944a
          -
          materialPercentage: 5%**`"]
        end  
    end
    subgraph materials["Materials"]
        ma_cardboard["Cardboard
        -
        16f41cca-1a77-4e31-8b0f-2723f752317b"]
        ma_glass["Glass
        -
        b050ab75-4bcb-4c7f-b8f5-8a1f9e5ba7d3"]
    end
    bm_cardboard --> mc_cardboard
    mcs_cardboard --> ma_cardboard
    bm_sodaAsh --> mc_sodaAsh
    bm_cullet --> mc_cullet
    bm_sand --> mc_sand
    bm_limestone --> mc_limestone
    mcs_glass --> ma_glass
```