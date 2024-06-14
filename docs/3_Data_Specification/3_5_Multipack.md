---
title: Multipacks
description: Multipacks contain multiple identical packaging items within Open 3P.
---

# Multipacks

The multipacks schema contains information regarding the multipacks that are used to create loads. These are created from a number of either identical or different complete packages from the complete packaging schema.

**Note:** The multipack portion is optional (only applies to multipacks). If the complete packaging or component is *not* in a multipack, all of the fields below are optional. 

## Table
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`mandatory`|UUID|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|name|`optional`|String|The name of this multipack.|
|description|`optional`|String|A brief description of this multipack.|
|externalIdentifiers|`optional`|Dictionary|A dictionary of identifiers that might be used to identify the multipack in other systems. For example: manufacturer's own internal identifier, bar codes or global trade item number (gtin). To provide external identifiers please follow this format. `{'externalIdentifierName1': 'identifier1', 'externalIdentifierName2': 'identifier2'}`|
|multipackConstituentsIdentifiers|`mandatory`|List|The information regarding the consituents that are combined to create this multipack. The entries should be from the [Multipack Constituents Relationship List](../6_Relationship_Lists/6_004_Multipack_Constituents.md) identifier.|
|tier|`optional`|Integer|The tier associated with the multipack. The inner most tier denoted as 1, and the outermost tier is the biggest number.|
|measurements|`optional`|List|The information regarding the measurements of the multipack. The entries should be from the [Measurements Relationship List](../6_Relationship_Lists/6_012_Measurements.md).|
|manufacturers|`optional`|List|The information regarding the manufacturer(s). The entries should be the [Organisations Relationship List](../6_Relationship_Lists/6_010_Organisations.md) identifiers.|
|manufacturedCountry|`optional`|String|The country the component was manufactured in. Use the country numeric [ISO codes](https://www.iso.org/obp/ui/#search){target=_blank} as described in the [ISO 3166 international standard](https://www.iso.org/iso-3166-country-codes.html){target=_blank}.|
|updateDate|`mandatory`|Date|The date that the multipack was provided/last updated. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|
|releaseDate|`optional`|Date|The date that the component will be available to use. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|
|discontinueDate|`optional`|Date|The date that the component will no longer be available to use. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|

## Diagram

``` mermaid
erDiagram
COMPONENTS }o..o{ MULTIPACK : multipack_constituents
COMPONENTS }o..o{ COMPLETE_PACKAGING : complete_packaging_constituents
COMPLETE_PACKAGING }o..o{ MULTIPACK : multipack_constituents
  MULTIPACK {
    identifier UUID "*"
    name String
    description String
    externalIdentifiers Dictionary
    multipackConstituentsIdentifiers List "*"
    tier String
    measurements List
    manufacturers List
    manufacturedCountry String
    updateDate Date "*"
    releaseDate Date
    discontinueDate Date
  }
  MULTIPACK }o--o{ RELATIONSHIP_LISTS : attributes
  COMPLETE_PACKAGING }o..o{ LOADS : load_constituents
  MULTIPACK }o..o{ LOADS : load_constituents
  COMPONENTS }o--o{ LOADS : load_constituents
      RELATIONSHIP_LISTS {
        organisations optional
        measurements optional
    }
```

## Example

=== "12 Multipack of Wine JSON"

    ``` json linenums="1" hl_lines="3 4"
    [
      {
        "identifier": "111525c0-9a41-4eea-a9b7-a8c23ffcf94d",
        "name": "12 pack of wine",
        "description": "12 x 750ml of red wine that are sold together. Not to be sold separately.",
        "externalIdentifiers": {
          "GTIN":"00123456789012",
          },
        "multipackConstituentsIdentifiers": [
          {
          "multipackConstituentsIdentifier": "346C5546-282B-C040-CE74-DD0DD4688C0B",
          "multipackCombinationIdentifier": "516ac728-65e3-48c6-9756-37c29c177a7c"
          },
          {
          "multipackConstituentsIdentifier": "346C5546-282B-C040-CE74-DD0DD4688C0B",
          "multipackCombinationIdentifier": "123f1eab-f674-4009-862a-7168cd5cf53f"
          }
        ],
        "tier": 1,
        "manufacturers": ["GB-COH-10906273"],
        "manufacturedCountry": "826",
        "updateDate": "2022-08-01",
        "releaseDate": "2022-08-01",
        "discontinueDate": "",
      }
    ]
    ```
=== "12 Multipack of Wine XML"

    ``` xml linenums="1" hl_lines="3 4"
    <?xml version="1.0" encoding="UTF-8" ?>
      <multipack>
        <identifier>111525c0-9a41-4eea-a9b7-a8c23ffcf94d</identifier>
        <name>12 pack of wine</name>
        <description>12 x 750ml of red wine that are sold together. Not to be sold separately.</description>
        <externalIdentifiers>
          <GTIN>00123456789012</GTIN>
        </externalIdentifiers>
        <multipackConstituentsIdentifiers>
          <multipackConstituentsIdentifier>346C5546-282B-C040-CE74-DD0DD4688C0B</multipackConstituentsIdentifier>
          <multipackCombinationIdentifier>516ac728-65e3-48c6-9756-37c29c177a7c</multipackCombinationIdentifier>
        </multipackConstituentsIdentifiers>
        <multipackConstituentsIdentifiers>
          <multipackConstituentsIdentifier>346C5546-282B-C040-CE74-DD0DD4688C0B</multipackConstituentsIdentifier>
          <multipackCombinationIdentifier>123f1eab-f674-4009-862a-7168cd5cf53f</multipackCombinationIdentifier>
        </multipackConstituentsIdentifiers>
        <tier>1</tier>
        <manufacturers>GB-COH-10906273</manufacturers>
        <manufacturedCountry>826</manufacturedCountry>
        <updateDate>2022-08-01</updateDate>
        <releaseDate>2022-08-01</releaseDate>
        <discontinueDate></discontinueDate>
      </multipack>
    ```
## Data flow

``` mermaid
flowchart LR
    subgraph components[Components]
        co_example["example components"]
    end
    subgraph completePackages[Complete Packages]
        cp_wineBox["Wine Box
        -
        516ac728-65e3-48c6-9756-37c29c177a7c"]
        cp_wineBottle["Wine Bottle
        -
        123f1eab-f674-4009-862a-7168cd5cf53f"]
    end
    subgraph multipacks["`**Multipacks**`"]
        mp_wineBox["`**12 pack of wine
        -
        111525c0-9a41-4eea-a9b7-a8c23ffcf94d**`"]
    end
    subgraph loads[Loads]
        lo_load["example loads"]
    end
    components --> completePackages
    cp_wineBox -.-> mp_wineBox
    cp_wineBottle -.-> mp_wineBox
    mp_wineBox -.-> loads
```