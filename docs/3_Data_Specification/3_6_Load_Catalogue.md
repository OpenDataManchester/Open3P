---
title: Load Catalogue
description: The load catalogue aids organisations to combine products to form a load within Open 3P.
---

# Load Catalogue

All the complete packaging from different levels (primary, secondary, transit etc.), including multipacks, put together to send to the final destination. Each row corresponds to a single packaging item.

## Table
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`required`|UUID|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|name|`recommended`|String|The name of this load.|
|description|`recommended`|String|A brief description of this load.|
|externalIdentifiers|`recommended`|Dictionary|A dictionary of identifiers that might be used to identify the load catalogue in other systems. For example: manufacturer's own internal identifier, bar codes or global trade item number (gtin). To provide external identifiers please follow this format. `{'externalIdentifierName1': 'identifier1', 'externalIdentifierName2': 'identifier2'}`|
|loadIdentifier|`required`|UUID|The unique identifier of the created load. A globally unique identifier. See identifiers section for information on how to construct this identifier.|
|packagingItems|`required`|List|The complete packaging and/or the multipack identifiers used to create the load. There must be an equivalent record in the `Complete Packaging` or `Multipack` data.|
|quantityInLoad|`required`|Integer|Number of units for the packaging items found in a load that this row corresponds to.|
|level|`required`|String|The intended use of the component for the packaging. The entry here should be drawn from the [level controlled list](../5_Controlled_Lists/5_015_Level.md).|
|updateDate|`required`|Date|The date that the load catalogue was provided/last updated. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|

## Diagram

``` mermaid
erDiagram
COMPONENTS }o..o{ LOAD_CATALOGUE : within
COMPONENTS }o..o{ COMPLETE_PACKAGING : within
COMPONENTS }o..o{ MULTIPACK : within
MULTIPACK }o..o{ LOAD_CATALOGUE : within
COMPLETE_PACKAGING }o..o{ LOAD_CATALOGUE : within
COMPLETE_PACKAGING }o..o{ MULTIPACK : within

  LOAD_CATALOGUE {
    identifier UUID
    name String
    description String
    externalIdentifiers Dictionary
    loadIdentifier UUID
    packagingItems List
    quantityInLoad Integer
    level String
    updateDate Date
  }
  LOAD_CATALOGUE }o..o{ CONTROLLED_LISTS : attributes
  LOAD_CATALOGUE }o--o{ LOAD : within
        CONTROLLED_LISTS {
    level required
    }
```

## Template

Loads should be provided as a separate csv file. The specification of this csv file is as follows:

[Load Catalogue Template](https://www.open3p.org/wp-content/uploads/2023/09/loadCatalogue20230922.csv){target=_blank}

## Example

=== "JSON"

    ``` json linenums="1"
    {
      "identifier": "91F2060F-17CD-DA56-7746-0018A90AEF5A",
      "name": "Full pallet of multipack guacamole dip",
      "description": "24 cases of 3 x multipack tubs of guacamole dip",
      "externalIdentifiers": {
        "GTIN":"00123456789012",
        },
      "loadIdentifiers": "CA88F5CE-2D09-AFE0-08D7-44804780F924",
      "packagingItems": "346C5546-282B-C040-CE74-DD0DD4688C0B",
      "quantityInLoad": 72,
      "level": {
        "identifier":"lc-level-0001",
        "category":"primary",
        "detailed":"The individual container that you store goods in to sell to consumers. This is called a "sales unit". For example, if you sell peas in steel tins with paper labels, the primary packaging is "steel tin" and "paper label"."
      },
      "updateDate": "2023-01-01",
    }
    ```
=== "CSV download"

    * [Load Catalogue example download](https://www.opendatamanchester.org.uk/wp-content/uploads/2023/01/7_1_5_Load_Catalogue_Example.csv){target=_blank}
