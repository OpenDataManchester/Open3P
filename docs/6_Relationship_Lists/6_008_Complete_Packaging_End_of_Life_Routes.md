---
title: Complete Packaging End of Life Routes
description: The complete packaging end of life routes relationship list.
---

# Complete Packaging End of Life Routes

The complete packaging end of life routes relationship list identifies the purposed and intented destination and process of this complete packaging once it has completed its role as packaging. This is only used in [complete packaging](../3_Data_Specification/3_4_Complete_Packaging.md).

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|completePackagingEndOfLifeRouteIdentifier|`required`|String|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|completePackagingEndOfLifeRoute|`recommended`|String|What is the entended end of life route for this complete packaging. The entry should be the [end of life route controlled list](../5_Controlled_Lists/5_016_End_Of_Life_Route.md) identifier.|
|orderOfPrecedence|`recommended`|String|The order that end of life routes should be used. The preferred route denoted as 1, and the last best option being the biggest number.|
|completePackagingDistruptors|`recommended`|List|What challenges this end of life route for this complete packaging has. The entry should be the [complete packaging recycling disruptors controlled list](../5_Controlled_Lists/5_014_Complete_Packaging_Recycling_Disruptors.md) identifier.|

## Diagram

``` mermaid
erDiagram

  COMPLETE_PACKAGING }o..o{ COMPLETE_PACKAGING_END_OF_LIFE_ROUTES : within
  COMPLETE_PACKAGING_END_OF_LIFE_ROUTES {
    completePackagingEndOfLifeRouteIdentifier String
    completePackagingEndOfLifeRoute String
    orderOfPrecedence String
    completePackagingDistruptors List
  }
  COMPLETE_PACKAGING_END_OF_LIFE_ROUTES }o--o{ CONTROLLED_LISTS : attributes
      CONTROLLED_LISTS {
    endOfLifeRoute required
    completePackagingDistruptors required }
  }
```