---
title: Recyclability Claims
description: The recyclability claims relationship list.
---

# Recyclability Claims

The recyclability claims relationship list identifies organisations and schemes that provide the recyclability claims. This is used in the following schemas:

* [Components](../3_Data_Specification/3_3_Components.md)
* [Complete Packaging](../3_Data_Specification/3_4_Complete_Packaging.md)

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|recyclabilityIdentifier|`required`|String|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|recyclabilitySource|`recommended`|String|What source provided the certificate? The entry should be the [recyclability source controlled list](../5_Controlled_Lists/5_005_Recyclability_Source.md) identifier.|
|recyclabilityIssueDate|`recommended`|String|The date that the certificate was provided/last updated. Use the format `dd/mm/yyyy`.|

## Diagram

``` mermaid
erDiagram

  COMPONENTS }o..o{ RECYCLABILITY_CLAIMS : within
  COMPLETE_PACKAGING }o..o{ RECYCLABILITY_CLAIMS : within
  RECYCLABILITY_CLAIMS {
    recyclabilityIdentifier String
    recyclabilitySource String
    recyclabilityIssueDate String
  }
  RECYCLABILITY_CLAIMS }o--o{ CONTROLLED_LISTS : attributes
      CONTROLLED_LISTS {
    recyclabilitySource required }
  }
```

## Template

Recyclability claims should be provided as a separate csv file. The specification of this csv file is as follows:

[Recyclability Claims Template](https://www.open3p.org/wp-content/uploads/2023/09/recyclabilityClaims20230922.csv)

## Example

=== "JSON"

    ``` json linenums="1"
    --Claim provided by OPRL.
    {
      "recyclabilityIdentifier": "b101889f-87e5-4c42-abb7-0df5fc3d1a26",
      "recyclabilitySource": "recyclability-source-0001",
      "recyclabilityIssueDate": "01/08/2022"
    }
    ```