---
title: Complete Packaging Constituents
description: The complete packaging constituents relationship list.
---

# Complete Packaging Constituents

The complete packaging constituents relationship list identifies the components and other complete packaging that are combined to create complete packages. This is only used in [complete packaging](../3_Data_Specification/3_4_Complete_Packaging.md).

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|completePackagingConstituentsIdentifier|`mandatory`|UUID|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|completePackagingCombinationIdentifier|`mandatory`|UUID|The unique identifier of the components and/or complete packaging that this complete packaging is made of. There must be an equivalent record in the `Components` OR `Complete Packaging` data.|
|contactWithProduct|`mandatory`|Boolean|Does this constituent come into contact with the product? Answer as: `TRUE` for yes and `FALSE` for no.|

## Diagram

``` mermaid
erDiagram

  COMPLETE_PACKAGING }o..o{ COMPLETE_PACKAGING_CONSTITUENTS : within
  COMPLETE_PACKAGING_CONSTITUENTS {
    completePackagingConstituentsIdentifier UUID "*"
    completePackagingCombinationIdentifier UUID "*"
    contactWithProduct Boolean "*"
  }
  COMPLETE_PACKAGING_CONSTITUENTS }o--o{ COMPONENTS : attributes
  COMPLETE_PACKAGING_CONSTITUENTS }o--o{ COMPLETE_PACKAGING : attributes
```
## Example

=== "To Wine Box JSON"

    ``` json linenums="1" hl_lines="3 4 8 9"
    [
      {
        "completePackagingConstituentsIdentifier": "6d856739-3893-4321-84b9-738a4ef1c830",
        "completePackagingCombinationIdentifier": "9dad67b0-d5a2-4afb-9287-e712fd1ea3e6",
        "contactWithProduct": false,
      },
      {
        "completePackagingConstituentsIdentifier": "6d856739-3893-4321-84b9-738a4ef1c830",
        "completePackagingCombinationIdentifier": "8f87c708-8a6b-4c9d-ae6e-af0393f84a12",
        "contactWithProduct": true,
      },
    ]
    ```
## Data flow

``` mermaid
flowchart LR
    subgraph components["Components"]
      co_cardboardBox["Cardboard box
      - 
      9dad67b0-d5a2-4afb-9287-e712fd1ea3e6"]
      co_tape["Tape
      - 
      8f87c708-8a6b-4c9d-ae6e-af0393f84a12"]
      co_wineBottle["Wine bottle
      - 
      94108707-b914-43f3-bed5-93adbbd208c1"]
      co_cork["Cork
      - 
      4b99be14-c89e-4869-abb7-485240ea33c6"]
      co_backLabel["Back label
      - 
      3d77b280-690e-4ccb-84f5-584c4cbcea36"]
      co_frontLabel["Front label
      - 
      4b50247a-b2d1-4438-ac8a-fb6768180136"]
    end
    subgraph completePackagingConstituents["`**-**`"]
      subgraph cpcs_wineBox ["`**Wine Box Constituents**`"]
        cpc_wineBox["`**6d856739-3893-4321-84b9-738a4ef1c830
        -
        contactWithProduct: FALSE**`"]
        cpc_tape["`**6d856739-3893-4321-84b9-738a4ef1c830
        -
        contactWithProduct: FALSE**`"]
      end
      subgraph cpcs_wineBottle ["`**Wine Bottle Constituents**`"]
        cpc_wineBottle["`**70023f95-2d0f-4e47-ab6e-0ce51d50e55d
        -
        contactWithProduct: TRUE**`"]
        cpc_cork["`**70023f95-2d0f-4e47-ab6e-0ce51d50e55d
        -
        contactWithProduct: TRUE**`"]
        cpc_backLabel["`**70023f95-2d0f-4e47-ab6e-0ce51d50e55d
        -
        contactWithProduct: FALSE**`"]
        cpc_frontLabel["`**70023f95-2d0f-4e47-ab6e-0ce51d50e55d
        -
        contactWithProduct: FALSE**`"]
      end  
    end
    subgraph completePackages["Complete Packages"]
        cp_wineBox["Wine Box
        -
        516ac728-65e3-48c6-9756-37c29c177a7c"]
        cp_wineBottle["Wine Bottle
        -
        123f1eab-f674-4009-862a-7168cd5cf53f"]
    end
    co_cardboardBox --> cpc_wineBox
    co_tape --> cpc_tape
    co_wineBottle --> cpc_wineBottle
    co_cork --> cpc_cork
    co_backLabel --> cpc_backLabel
    co_frontLabel --> cpc_frontLabel
    cpcs_wineBox --> cp_wineBox
    cpcs_wineBottle --> cp_wineBottle
```