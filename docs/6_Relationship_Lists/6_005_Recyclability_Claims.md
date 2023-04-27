---
title: Recyclability Claims
description: The recyclability claims relationship list.
---

# Recyclability Claims

The recyclability claims relationship list identifies the materials that are combined to create components. This is used in the following schemas:

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