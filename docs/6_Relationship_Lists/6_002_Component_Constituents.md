---
title: Component Constituents
description: The component constituents relationship list.
---

# Component Constituents

The component constituents relationship list identifies the materials that are combined to create components. This is only used in [components](../3_Data_Specification/3_3_Components.md).

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|componentConstituentsIdentifier|`mandatory`|UUID|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|materialCombinationIdentifier|`mandatory`|UUID|The unique identifier of the materials that this component is made of. There must be an equivalent record in the `Materials` OR `Components` data.|

## Diagram

``` mermaid
erDiagram

  COMPONENTS }o..o{ COMPONENT_CONSTITUENTS : within
  COMPONENT_CONSTITUENTS {
    componentConstituentsIdentifier UUID "*"
    componentCombinationIdentifier UUID "*"
  }
  COMPONENT_CONSTITUENTS }o--o{ MATERIALS : attributes
  COMPONENT_CONSTITUENTS }o--o{ COMPONENTS : attributes
```

## Example

=== "To Cardboard Box - JSON"

    ``` json linenums="1" hl_lines="3 4"
    [
      {
        "componentConstituentsIdentifier": "6d856739-3893-4321-84b9-738a4ef1c830",
        "componentCombinationIdentifier": "16f41cca-1a77-4e31-8b0f-2723f752317b"
      }
    ]
    ```
=== "To Glass Wine Bottle - JSON"

    ``` json linenums="1" hl_lines="3 4"
    [
      {
        "componentConstituentsIdentifier": "70023f95-2d0f-4e47-ab6e-0ce51d50e55d",
        "componentCombinationIdentifier": "b050ab75-4bcb-4c7f-b8f5-8a1f9e5ba7d3",
      }
    ]
    ```
=== "To Cardboard Box - XML"

    ``` xml linenums="1" hl_lines="3 4"
    <?xml version="1.0" encoding="UTF-8" ?>
    <root>
      <row>
        <componentConstituentsIdentifier>6d856739-3893-4321-84b9-738a4ef1c830</componentConstituentsIdentifier>
        <componentCombinationIdentifier>16f41cca-1a77-4e31-8b0f-2723f752317b</componentCombinationIdentifier>
      </row>
    </root>
    ```
=== "To Glass Wine Bottle - XML"

    ``` xml linenums="1" hl_lines="3 4"
    <?xml version="1.0" encoding="UTF-8" ?>
    <root>
      <row>
        <componentConstituentsIdentifier>70023f95-2d0f-4e47-ab6e-0ce51d50e55d</componentConstituentsIdentifier>
        <componentCombinationIdentifier>b050ab75-4bcb-4c7f-b8f5-8a1f9e5ba7d3</componentCombinationIdentifier>
      </row>
    </root>
    ```

## Data flow

``` mermaid
flowchart LR
    subgraph materials[Materials]
      ma_cardboard["Cardboard
      -
      16f41cca-1a77-4e31-8b0f-2723f752317b"]
      ma_glass["Glass
      -
      b050ab75-4bcb-4c7f-b8f5-8a1f9e5ba7d3"]
    end
    subgraph componetConstituents["`**-**`"]
      subgraph cocs_cardboard ["`**Cardboard Box Constituents**`"]
        coc_cardboard["`**6d856739-3893-4321-84b9-738a4ef1c830**`"]
      end
      subgraph cocs_glass ["`**Wine bottle Constituents**`"]
        coc_glass["`**70023f95-2d0f-4e47-ab6e-0ce51d50e55d**`"]
      end  
    end
    subgraph components["Components"]
      co_cardboardBox["Cardboard box
      - 
      9dad67b0-d5a2-4afb-9287-e712fd1ea3e6"]
      co_wineBottle["Wine bottle
      - 
      94108707-b914-43f3-bed5-93adbbd208c1"]
    end
    ma_cardboard --> coc_cardboard
    ma_glass --> coc_glass
    cocs_cardboard --> co_cardboardBox
    cocs_glass --> co_wineBottle

```
