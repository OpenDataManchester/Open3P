---
title: Component End of Life Routes
description: The component end of life routes relationship list.
---

# Component End of Life Routes

The component end of life routes relationship list identifies the purposed and intented destination and process of this component once it has completed its role as packaging. This is only used in [components](../3_Data_Specification/3_3_Components.md).

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|componentEndOfLifeRouteIdentifier|`required`|String|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|componentEndOfLifeRoute|`required`|String|What is the entended provided the certificate? The entry should be the [end of life route controlled list](../5_Controlled_Lists/5_016_End_Of_Life_Route.md) identifier.|
|orderOfPrecedence|`recommended`|Numeric|The order that end of life routes should be used. The preferred route denoted as 1, and the last best option being the biggest number.|
|componentDistruptors|`required`|List|What challenges this end of life route for this component has. The entry should be the [component recycling disruptors controlled list](../5_Controlled_Lists/5_008_Component_Recycling_Disruptors.md) identifier.|

## Diagram

``` mermaid
erDiagram

  COMPONENTS }o..o{ COMPONENT_END_OF_LIFE_ROUTES : within
  COMPONENT_END_OF_LIFE_ROUTES {
    componentEndOfLifeRouteIdentifier String
    componentEndOfLifeRoute String
    orderOfPrecedence String
    componentDistruptors List
  }
  COMPONENT_END_OF_LIFE_ROUTES }o--o{ CONTROLLED_LISTS : attributes
      CONTROLLED_LISTS {
    endOfLifeRoute required
    componentDistruptors required }
  }
```