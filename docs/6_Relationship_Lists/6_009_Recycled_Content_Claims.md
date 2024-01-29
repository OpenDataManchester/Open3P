---
title: Recycled Content Claims
description: The recycled content claims relationship list.
---

# Recycled Content Claims

The recycled content claims relationship list identifies the document that details the recycled content claim. This is only used in [components](../3_Data_Specification/3_3_Components.md).

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|recycledContentIdentifier|`mandatory`|UUID|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|recycledContentEvidenceType|`optional`|String|What type of document provides the information regarding the claim? The entry should be the [recycled content evidence type](../5_Controlled_Lists/5_011_Recycled_Content_Evidence_Type.md) identifier.|
|recycledContentEvidenceReference|`optional`|String|An accompanying reference number associated with the recycled content evidence type for the component.|
|recycledContentIssueDate|`optional`|Date|The date that the recycled content evidence was issued. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|

## Diagram

``` mermaid
erDiagram

  COMPONENTS }o..o{ RECYCLED_CONTENT_CLAIMS : within
  RECYCLED_CONTENT_CLAIMS {
    recycledContentIdentifier UUID "*"
    recycledContentEvidenceType String
    recycledContentEvidenceReference String
    recycledContentIssueDate Date
  }
  RECYCLED_CONTENT_CLAIMS }o--o{ CONTROLLED_LISTS : attributes
  CONTROLLED_LISTS {
    recycledContentEvidenceType mandatory
  }
```

## Template

Recycled content claims should be provided as a separate csv file. The specification of this csv file is as follows:

[Recycled Content Claims](https://www.open3p.org/wp-content/uploads/2023/09/recycledContentClaims20230922.csv)

## Example

=== "JSON"

    ``` json linenums="1"
    --A certificate providing information about a recycled content claim.
    {
      "recycledContentIdentifier": "23e8251a-4fe6-4b25-9966-b08acac9ba34",
      "recycledContentEvidenceType": "c-recycled-evidence-0001",
      "recycledContentEvidenceReference": "ABC-123-Example",
      "recycledContentIssueDate": "2022-08-01"
    }
    ```