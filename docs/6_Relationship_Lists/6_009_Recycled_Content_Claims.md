---
title: Recycled Content Claims
description: The recycled content claims relationship list.
---

# Recycled Content Claims

The recycled content claims relationship list identifies the document that details the recycled content claim. This is only used in [components](../3_Data_Specification/3_3_Components.md).

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|recycledContentIdentifier|`required`|String|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|recycledContentEvidenceType|`recommended`|String|What type of document provides the information regarding the claim? The entry should be the [recycled content evidence type](../5_Controlled_Lists/5_011_Recycled_Content_Evidence_Type.md) identifier.|
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

## Example

=== "JSON"

    ``` json linenums="1"
    --A certificate providing information about a recycled content claim
{
    "recycledContentIdentifier": "23e8251a-4fe6-4b25-9966-b08acac9ba34",
    "recycledContentEvidenceType": "c-recycled-evidence-0001",
    "recycledContentEvidenceReference": "ABC-123-Example",
    "recycledContentIssueDate": "01/08/2022"
}