---
title: Loads
description: The loads contains items what are delivered to a location within Open 3P.
---

# Loads

All the complete packaging from different levels (primary, secondary, transit etc.), including multipacks, put together to send to the final destination. Each row corresponds a unique complete packaging (or multipack) item sent to a specific location during a specific time period.

Note that all core entities can be incorporated into loads. This is to faciliate the interface between one organisastion's product is another organisation's packaging item.

## Table
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`mandatory`|UUID|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|name|`optional`|String|The name of this load.|
|description|`optional`|String|A brief description of this load.|
|externalIdentifiers|`optional`|Dictionary|A dictionary of identifiers that might be used to identify the load in other systems. For example: manufacturer's own internal identifier, bar codes or global trade item number (gtin). To provide external identifiers please follow this format. `{'externalIdentifierName1': 'identifier1', 'externalIdentifierName2': 'identifier2'}`|
|loadIdentifiers|`mandatory`|List|The unique identifier of the created load. There must be an equivalent identifier found in the `Load Catalogue`.|
|startDate|`optional`|Date|The date that the load began for the destination. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|
|endDate|`optional`|Date|The date that the load ended at the destination. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|
|destinationAddressName|`optional`|String|The name of the load destination address.|
|destinationAddressStreet|`optional`|String|The street address of this load destination.|
|destinationAddressCountry|`optional`|String|The country of this load destination.|
|destinationPostalCode|`optional`|String|The postal code of this load destination.|
|timesSent|`optional`|Integer|The number of times this load was sent to the destination during the specified time period.|
|manufacturers|`optional`|List|The information regarding the manufacturer(s). The entries should be the [Organisations Relationship List](../6_Relationship_Lists/6_010_Organisations.md) identifiers.|
|manufacturedCountry|`optional`|String|The country the component was manufactured in. Use the country numeric [ISO codes](https://www.iso.org/obp/ui/#search){target=_blank} as described in the [ISO 3166 international standard](https://www.iso.org/iso-3166-country-codes.html){target=_blank}.|
|updateDate|`mandatory`|Date|The date that the load was provided/last updated. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|

## Diagram

``` mermaid
erDiagram
BASE_MATERIALS }o..o{ LOADS : load_constituents
MATERIALS }o..o{ LOADS : load_constituents
COMPLETE_PACKAGING }o..o{ LOADS : load_constituents
COMPONENTS }o..o{ LOADS : load_constituents
MULTIPACK }o..o{ LOADS : load_constituents
COMPONENTS }o..o{ MULTIPACK : multipack_constituents
COMPLETE_PACKAGING }o..o{ MULTIPACK : multipack_constituents
COMPONENTS }o..o{ COMPLETE_PACKAGING : complete_packaging_constituents
  LOADS {
    identifier UUID "*"
    name String
    description String
    externalIdentifier Dictionary
    loadIdentifiers List "*"
    startDate Date
    endDate Date
    destinationAddressName String
    destinationAddressStreet String
    destinationAddressCountry String
    destinationPostalCode String
    timesSent Integer
    manufacturers List
    manufacturedCountry String
    updateDate Date "*"
  }
  LOADS }o--o{ RELATIONSHIP_LISTS : attributes
  RELATIONSHIP_LISTS {
      organisations optional
    }
```

## Example

=== "Wine Delivery - JSON"

    ``` json linenums="1" hl_lines="3 4"
    [
      {
        "identifier": "ED051AFD-EC7F-0428-B054-8837118922FE",
        "name": "Pallet of multicase wine",
        "description": "27 cases of 12 x wine",
        "externalIdentifiers": {
          "GTIN":"00123456789012"
          },
        "loadIdentifiers": "CA88F5CE-2D09-AFE0-08D7-44804780F924",
        "manufacturers": ["GB-COH-10906273"],
        "manufacturedCountry": "826",
        "updateDate": "2022-08-01",
      }
    ]
    ```
=== "Wine Delivery - XML"

    ``` xml linenums="1" hl_lines="3 4"
    <?xml version="1.0" encoding="UTF-8" ?>
      <load>
        <identifier>ED051AFD-EC7F-0428-B054-8837118922FE</identifier>
        <name>Pallet of multicase wine</name>
        <description>27 cases of 12 x wine</description>
        <externalIdentifiers>
          <GTIN>00123456789012</GTIN>
        </externalIdentifiers>
        <loadIdentifiers>CA88F5CE-2D09-AFE0-08D7-44804780F924</loadIdentifiers>
        <manufacturers>GB-COH-10906273</manufacturers>
        <manufacturedCountry>826</manufacturedCountry>
        <updateDate>2022-08-01</updateDate>
      </load>
    ```
    
## Data flow

``` mermaid
flowchart LR
    subgraph completePackages[Complete Packages]
        cp_wineBox[example complete packages]
        cp_pallet[Pallet]
        cp_shrinkWrap[Shrink Wrap]
    end
    subgraph multipacks[Multipacks]
        mp_wineBox["12 pack of wine
        -
        111525c0-9a41-4eea-a9b7-a8c23ffcf94d"]
    end
    subgraph loads["`**Loads**`"]
        lo_load["`**Pallet of multicase wine
        -
        ED051AFD-EC7F-0428-B054-8837118922FE**`"]
    end
    cp_wineBox -.-> multipacks
    mp_wineBox -.-> lo_load
    cp_pallet --> lo_load
    cp_shrinkWrap --> lo_load
```
