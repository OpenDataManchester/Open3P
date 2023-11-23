---
title: Multipack
description: Multipacks contain multiple identical packaging items within Open 3P.
---

# Multipack

The multipack schema contains information regarding the multipacks that are used to create loads. These are created from a number of either identical or different complete packages from the complete packaging schema.

**Note:** The multipack portion is optional (only applies to multipacks). If the complete packaging or component is *not* in a multipack, all of the fields below are optional. 

## Table
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`required`|String|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|name|`recommended`|String|The name of this multipack.|
|description|`recommended`|String|A brief description of this multipack.|
|externalIdentifiers|`recommended`|Dictionary|A dictionary of identifiers that might be used to identify the multipack in other systems. For example: manufacturer's own internal identifier, bar codes or global trade item number (gtin). To provide external identifiers please follow this format. `{'externalIdentifierName1': 'identifier1', 'externalIdentifierName2': 'identifier2'}`|
|multipackConstituentsIdentifiers|`required`|List|The information regarding the consituents that are combined to create this multipack. The entries should be from the [Multipack Constituents Relationship List](../6_Relationship_Lists/6_004_Multipack_Constituents.md) identifier.|
|tier|`recommended`|Integer|The tier associated with the multipack. The inner most tier denoted as 1, and the outermost tier is the biggest number.|
|identicalQuantity|`required`|Numeric|Number of identical units for the unique complete packaging item or a component this row corresponds to.|
|manufacturers|`recommended`|List|The information regarding the manufacturer(s). The entries should be the [Organisations Relationship List](../6_Relationship_Lists/6_010_Organisations.md) identifiers.|
|manufacturedCountry|`recommended`|Numeric|The country the multipack was manufactured and/or combined. Use the country numeric [ISO codes](https://www.iban.com/country-codes){target=_blank} as described in the ISO 3166 international standard.|
|updateDate|`required`|String|The date that the multipack was provided/last updated. Use the format `dd/mm/yyyy`.|
|releaseDate|`recommended`|String|The date that the component will be available to use. Use the format `dd/mm/yyyy`.|
|discontinueDate|`recommended`|String|The date that the component will no longer be available to use. Use the format `dd/mm/yyyy`.|

## Diagram

``` mermaid
erDiagram
COMPONENTS }o..o{ MULTIPACK : multipack_constituents
COMPONENTS }o..o{ COMPLETE_PACKAGING : complete_packaging_constituents
COMPLETE_PACKAGING }o..o{ MULTIPACK : multipack_constituents
  MULTIPACK {
    identifier String
    name String
    description String
    externalIdentifiers Dictionary
    multipackConstituentsIdentifiers List
    tier String
    identicalQuantity Numeric
    manufacturers List
    manufacturedCountry Numeric
    updateDate String
    releaseDate String
    discontinueDate String
  }
  MULTIPACK }o--o{ RELATIONSHIP_LISTS : attributes
  COMPLETE_PACKAGING }o..o{ LOADS : load_constituents
  MULTIPACK }o..o{ LOADS : load_constituents
  COMPONENTS }o--o{ LOADS : load_constituents
      RELATIONSHIP_LISTS {
        organisations recommended
    }
```

## Template

Multipack should be provided as a separate csv file. The specification of this csv file is as follows:

[Multipack Template](https://www.open3p.org/wp-content/uploads/2023/09/multipack20230922.csv){target=_blank}

## Example

=== "JSON"

    ``` json linenums="1"
    {
      "identifier": "B9574E9A-A561-BCA6-0E36-448A2E46B2BF",
      "name": "4 pack of guacamole dip",
      "description": "4 tubs of guacamole that are sold together. Not to be sold seperately.",
      "externalIdentifiers": {
        "GTIN":"00123456789012",
        },
      "multipackIdentifier": "346C5546-282B-C040-CE74-DD0DD4688C0B",
      "packagingItems": "C29B4703-121C-7552-D905-FD5AB263D611",
      "tier": "1",
      "identicalQuantity": "4",
      "manufacturers": [""],
      "manufacturedCountry": 826,
      "updateDate": "01/08/2022",
      "releaseDate": "01/08/2022",
      "discontinueDate": "",
    }
    ```
=== "CSV download"

    * [Multipack example download](https://www.opendatamanchester.org.uk/wp-content/uploads/2023/01/7_1_4_Multipack_Example.csv){target=_blank}