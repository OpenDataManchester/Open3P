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

## Example

=== "To Multipack of Wine JSON"

    ``` json linenums="1" hl_lines="3 4 8 9"
    [
      {
        "multipackConstituentsIdentifier": "346C5546-282B-C040-CE74-DD0DD4688C0B",
        "multipackCombinationIdentifier": "516ac728-65e3-48c6-9756-37c29c177a7c",
        "identicalQuantity": 1,
      },
      {
        "multipackConstituentsIdentifier": "346C5546-282B-C040-CE74-DD0DD4688C0B",
        "multipackCombinationIdentifier": "123f1eab-f674-4009-862a-7168cd5cf53f",
        "identicalQuantity": 12,
      } 
    ]
    ```
=== "To Multipack of Wine XML"

    ``` xml linenums="1" hl_lines="3 4 8 9"
    <?xml version="1.0" encoding="UTF-8" ?>
    <root>
      <row>
        <multipackConstituentsIdentifier>346C5546-282B-C040-CE74-DD0DD4688C0B</multipackConstituentsIdentifier>
        <multipackCombinationIdentifier>516ac728-65e3-48c6-9756-37c29c177a7c</multipackCombinationIdentifier>
        <identicalQuantity>1</identicalQuantity>
      </row>
      <row>
        <multipackConstituentsIdentifier>346C5546-282B-C040-CE74-DD0DD4688C0B</multipackConstituentsIdentifier>
        <multipackCombinationIdentifier>123f1eab-f674-4009-862a-7168cd5cf53f</multipackCombinationIdentifier>
        <identicalQuantity>12</identicalQuantity>
      </row>
    </root>
    ```

## Data flow

``` mermaid
flowchart LR
    subgraph completePackages[Complete Packages]
        cp_wineBox["Wine Box
        -
        516ac728-65e3-48c6-9756-37c29c177a7c"]
        cp_wineBottle["Wine Bottle
        -
        123f1eab-f674-4009-862a-7168cd5cf53f"]
    end
    subgraph multipackConstituents["`**-**`"]
      subgraph mpcs_wineBox ["`**Wine Multipack Constituents**`"]
        mpc_wineBox["`**346C5546-282B-C040-CE74-DD0DD4688C0B
        -
        identicalQuantity: 1**`"]
        mpc_wineBottle["`**346C5546-282B-C040-CE74-DD0DD4688C0B
        -
        identicalQuantity: 12**`"]
      end
    end
    subgraph multipacks["Multipacks"]
        mp_wineBox["12 pack of wine
        -
        111525c0-9a41-4eea-a9b7-a8c23ffcf94d"]
    end
    cp_wineBox --> mpc_wineBox
    cp_wineBottle --> mpc_wineBottle
    mpcs_wineBox --> mp_wineBox
```