---
title: Load Constituents
description: The load constituents relationship list.
---

# Load Constituents

The loads constituents relationship list identifies the all the complete packaging from different levels (primary, secondary, transit etc.) and multipacks that are combined to create loads. This is only used in [load](../3_Data_Specification/3_7_Load.md).

## Table
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|loadConstituentsIdentifier|`mandatory`|UUID|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|loadCombinationIdentifier|`mandatory`|UUID|The unique identifier of the items that this component is made of. There must be an equivalent record in the `Components`, `Complete_Packaging` OR `Multipacks` data.|
|name|`optional`|String|The name of this load constituent.|
|externalIdentifiers|`optional`|Dictionary|A dictionary of identifiers that might be used to identify the load constituents in other systems. For example: manufacturer's own internal identifier, bar codes or global trade item number (gtin). To provide external identifiers please follow this format. `{'externalIdentifierName1': 'identifier1', 'externalIdentifierName2': 'identifier2'}`|
|quantityInLoad|`mandatory`|Integer|Number of units for the packaging items found in a load that this row corresponds to.|
|level|`mandatory`|String|The intended use of the component for the packaging. The entry here should be drawn from the [level controlled list](../5_Controlled_Lists/5_015_Level.md).|

## Diagram

``` mermaid
erDiagram
  COMPONENTS }o..o{ LOAD_CONSTITUENTS : attributes
  COMPLETE_PACKAGING }o..o{ LOAD_CONSTITUENTS : attributes
  MULTIPACKS }o..o{ LOAD_CONSTITUENTS : attributes
  LOAD_CONSTITUENTS {
    loadConstituentsIdentifier UUID "*"
    loadCombinationIdentifier UUID "*"
    name String
    externalIdentifiers Dictionary
    quantityInLoad Integer "*"
    level String "*"
  }
  LOAD_CONSTITUENTS }o--o{ LOAD : within
  LOAD_CONSTITUENTS }o--o{ CONTROLLED_LISTS : attributes
  CONTROLLED_LISTS {
    level mandatory
  }
```
## Example

=== "To Wine Delivery - JSON"

    ``` json linenums="1" hl_lines="3 4"
    [
      {
        "loadConstituentsIdentifier": "CA88F5CE-2D09-AFE0-08D7-44804780F924",
        "loadCombinationIdentifier": "111525c0-9a41-4eea-a9b7-a8c23ffcf94d",
        "name": "Cases of 12 x wine",
        "externalIdentifiers": {
          "GTIN":"00123456789012"
          },
        "quantityInLoad": "27",
        "level": "lc-level-0001"
      }
    ]
    ```
=== "To Wine Delivery - XML"

    ``` xml linenums="1" hl_lines="3 4"
    <?xml version="1.0" encoding="UTF-8" ?>
    <loadConstituent>
      <loadConstituentsIdentifier>CA88F5CE-2D09-AFE0-08D7-44804780F924</loadConstituentsIdentifier>
      <loadCombinationIdentifier>111525c0-9a41-4eea-a9b7-a8c23ffcf94d</loadCombinationIdentifier>
      <name>Cases of 12 x wine</name>
      <externalIdentifiers>
        <GTIN>00123456789012</GTIN>
      </externalIdentifiers>
      <quantityInLoad>27</quantityInLoad>
      <level>lc-level-0001</level>
    </loadConstituent>
    ```

## Data flow

``` mermaid
flowchart LR
    subgraph completePackages["Complete Packages"]
        cp_pallet[Pallet]
        cp_shrinkWrap[Shrink Wrap]
    end
    subgraph multipacks[Multipacks]
        mp_wineBox["12 pack of wine
        -
        111525c0-9a41-4eea-a9b7-a8c23ffcf94d"]
    end
    subgraph multipacks[Multipacks]
        mp_wineBox["12 pack of wine
        -
        111525c0-9a41-4eea-a9b7-a8c23ffcf94d"]
    end
    subgraph loadConstituents["`**-**`"]
      subgraph locs_wineBox ["`**Wine Multipack Constituents**`"]
        loc_wineBox["`**CA88F5CE-2D09-AFE0-08D7-44804780F924
        -
        quantityInLoad: 27
        level: primary**`"]
        loc_pallet["`**CA88F5CE-2D09-AFE0-08D7-44804780F924
        -
        quantityInLoad: 1
        level: transit**`"]
        loc_shrinkWrap["`**CA88F5CE-2D09-AFE0-08D7-44804780F924
        -
        quantityInLoad: 1
        level: transit**`"]
      end
    end
    subgraph loads["Loads"]
        lo_load["Pallet of multicase wine
        -
        ED051AFD-EC7F-0428-B054-8837118922FE"]
    end
    cp_pallet --> loc_pallet
    cp_shrinkWrap --> loc_shrinkWrap
    mp_wineBox --> loc_wineBox
    locs_wineBox --> lo_load
```
