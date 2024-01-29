---
title: Organisations
description: The organisations relationship list.
---

# Organisations

The organisations relationship list identifies the organisations that are involved within the packaging value chain. This is used in the following schemas:

* [Base Materials](../3_Data_Specification/3_1_Base_Materials.md)
* [Materials](../3_Data_Specification/3_2_Materials.md)
* [Components](../3_Data_Specification/3_3_Components.md)
* [Complete Packaging](../3_Data_Specification/3_4_Complete_Packaging.md)
* [Multipack](../3_Data_Specification/3_5_Multipack.md)
* [Load](../3_Data_Specification/3_7_Load.md)

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|organisationIdentifier|`mandatory`|String|Unique identifier for organisation using [Org.Id format](https://github.com/OpenDataServices/org-ids/). Where possible, using company numbers as the baseline for unambiguous identification. This allows an internationally unique ID (EG: An identifier of the form GB-COH-XXXXXXXX for a UK-registered company). To lookup the format for a location & organisation type use [org-id.guide](http://org-id.guide/).|
|organisationName|`optional`|String|Name of the organisation.|
|postcode|`optional`|String|Postcode for organisation headquarters.|

## Diagram

``` mermaid
erDiagram
  BASE_MATERIALS }o..o{ ORGANISATIONS : within
  MATERIALS }o..o{ ORGANISATIONS : within
  COMPONENTS }o..o{ ORGANISATIONS : within
  COMPLETE_PACKAGING }o..o{ ORGANISATIONS : within
  MULTIPACK }o..o{ ORGANISATIONS : within
  LOAD }o..o{ ORGANISATIONS : within
  ORGANISATIONS {
    organisationIdentifier String [*]
    organisationName String
    postcode String
  }
```

## Example

=== "JSON"

    ``` json linenums="1"
    --The organisation information for Open Data Manchester.
    {
      "organisationIdentifier": "GB-COH-10906273",
      "organisationName": "OPEN DATA MANCHESTER CIC",
      "postcode": "M21 9NU"
    }
    ```