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
|identifier|`required`|String|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|name|`recommended`|String|The name of this load.|
|description|`recommended`|String|A brief description of this load.|
|externalIdentifiers|`recommended`|Dictionary|A dictionary of identifiers that might be used to identify the load in other systems. For example: manufacturer's own internal identifier, bar codes or global trade item number (gtin). To provide external identifiers please follow this format. `{'externalIdentifierName1': 'identifier1', 'externalIdentifierName2': 'identifier2'}`|
|loadIdentifiers|`required`|List|The unique identifier of the created load. There must be an equivalent identifier found in the `Load Catalogue`.|
|startDate|`required`|String|The date that the load began for the destination. Use the format `dd/mm/yyyy`.|
|endDate|`required`|String|The date that the load ended for the destination. Use the format `dd/mm/yyyy`.|
|destinationAddressName|`recommended`|String|The name of the load destination address.|
|destinationAddressStreet|`required`|String|The street address of this load destination.|
|destinationAddressCountry|`required`|String|The country of this load destination.|
|destinationPostalCode|`required`|String|The postal code of this load destination.|
|timesSent|`required`|Numeric|The number of times this load was sent to the destination during the specified time period.|
|manufacturers|`recommended`|List|The information regarding the manufacturer(s). The entries should be the [Organisations Relationship List](../6_Relationship_Lists/6_010_Organisations.md) identifiers.|
|manufacturedCountry|`recommended`|Numeric|The country the load was manufactured and/or combined. Use the country numeric [ISO codes](https://www.iban.com/country-codes){target=_blank} as described in the ISO 3166 international standard.|
|updateDate|`required`|String|The date that the load was provided/last updated. Use the format `dd/mm/yyyy`.|

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
    identifier String
    name numeric
    description String
    externalIdentifier Dictionary
    loadIdentifiers List
    startDate String
    destinationAddressName String
    destinationAddressStreet String
    destinationAddressCountry String
    destinationPostalCode String
    timesSent Numeric
    manufacturers List
    manufacturedCountry Numeric
    updateDate String
  }
  LOADS }o--o{ RELATIONSHIP_LISTS : attributes
  RELATIONSHIP_LISTS {
      organisations recommended
    }
```

## Template

Loads should be provided as a separate csv file. The specification of this csv file is as follows:

[Load Template](https://www.open3p.org/wp-content/uploads/2023/09/load20230922.csv){target=_blank}

## Example

=== "JSON"

    ``` json linenums="1"
    {
      "identifier": "ED051AFD-EC7F-0428-B054-8837118922FE",
      "name": "Weekly Load of Guacamole Dip",
      "description": "24 cases of 12 tubs of guacamole dip for example company on high street west",
      "externalIdentifiers": {
        "GTIN":"00123456789012",
        },
      "loadIdentifiers": "CA88F5CE-2D09-AFE0-08D7-44804780F924",
      "startDate": "01/08/2022",
      "endDate": "01/08/2022",
      "destinationAddressName": "Example Company",
      "destinationAddressStreet": "High Street West",
      "destinationAddressCountry": "England",
      "destinationPostalCode": "XX00 0XX",
      "timesSent": "2",
      "manufacturers": [""],
      "manufacturedCountry": 826,
      "updateDate": "01/08/2022",
    }
    ```
=== "CSV download"

    * [Load example download](https://www.opendatamanchester.org.uk/wp-content/uploads/2023/01/7_1_6_Load_Example.csv){target=_blank}
    