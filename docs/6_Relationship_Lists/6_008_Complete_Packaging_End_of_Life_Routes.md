---
title: Complete Packaging End of Life Routes
description: The complete packaging end of life routes relationship list.
---

# Complete Packaging End of Life Routes

The complete packaging end of life routes relationship list identifies the purposed and intended destination and process of this complete packaging once it has completed its role as packaging. This is only used in [complete packaging](../3_Data_Specification/3_4_Complete_Packaging.md).

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|completePackagingEndOfLifeRouteIdentifier|`required`|String|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|completePackagingEndOfLifeRoute|`recommended`|String|What is the intended end of life route for this complete packaging. The entry should be the [end of life route controlled list](../5_Controlled_Lists/5_016_End_Of_Life_Route.md) identifier. To be filled in when complete packaging has an intended end of life route AS complete packaging, otherwise only fill out at component level.|
|orderOfPrecedence|`recommended`|Numeric|The order that end of life routes should be used. The preferred route denoted as 1, and the last best option being the biggest number.|
|completePackagingDisruptors|`recommended`|List|What challenges this end of life route for this complete packaging has. The entry should be the [complete packaging end of life route disruptors controlled list](../5_Controlled_Lists/5_014_Complete_Packaging_Disruptors.md) identifier.|

## Diagram

``` mermaid
erDiagram

  COMPLETE_PACKAGING }o..o{ COMPLETE_PACKAGING_END_OF_LIFE_ROUTES : within
  COMPLETE_PACKAGING_END_OF_LIFE_ROUTES {
    completePackagingEndOfLifeRouteIdentifier String
    completePackagingEndOfLifeRoute String
    orderOfPrecedence Numeric
    completePackagingDistruptors List
  }
  COMPLETE_PACKAGING_END_OF_LIFE_ROUTES }o--o{ CONTROLLED_LISTS : attributes
      CONTROLLED_LISTS {
    endOfLifeRoute required
    completePackagingDistruptors required }
  }
```

## Template

Complete packaging end of life routes should be provided as a separate csv file. The specification of this csv file is as follows:

[Complete Packaging End of Life Routes Template](https://www.open3p.org/wp-content/uploads/2023/09/completePackagingEOLRoutes20230922.csv)

## Example

=== "JSON"

    ``` json linenums="1"
    --A complete packaging end of life route for recycling with food residue and a paper label being a disruptor.
    {
      "completePackagingEndOfLifeRouteIdentifier": "1229f395-3065-4236-bc1e-2aa500f58a79",
      "completePackagingEndOfLifeRoute": "end-of-life-route-0001",
      "orderOfPrecedence": 1,
      "completePackagingDistruptors": [
          "cp-disruptors-0029", "cp-disruptors-0022"
      ]
    }
    ```