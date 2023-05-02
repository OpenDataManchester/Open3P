---
title: Recycled Content Claims
description: The recycled content claims relationship list.
---

# Recycled Content Claims

The recycled content claims relationship list identifies the materials that are combined to create components. This is only used in [components](../3_Data_Specification/3_3_Components.md).

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|recycledContentIdentifier|`required`|String|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|recycledContentEvidenceType|`recommended`|String|What source provided the certificate? The entry should be the [recyclability source controlled list](../5_Controlled_Lists/5_005_Recyclability_Source.md) identifier.|
|recycledContentEvidenceReference|`recommended`|String|An accompanying reference number associated with the recycled content evidence type for the component.|
|recycledContentIssueDate|`recommended`|String|The date that the recycled content evidence was issued. Use the format `dd/mm/yyyy`.|

## Diagram

``` mermaid
erDiagram

  COMPONENTS }o..o{ RECYCLED_CONTENT_CLAIMS : within
  RECYCLED_CONTENT_CLAIMS {
    recycledContentIdentifier String
    recycledContentEvidenceType String
    recycledContentEvidenceReference String
    recycledContentIssueDate String
  }
  RECYCLED_CONTENT_CLAIMS }o--o{ CONTROLLED_LISTS : attributes
      CONTROLLED_LISTS {
    recycledContentEvidenceType required }
  }
```