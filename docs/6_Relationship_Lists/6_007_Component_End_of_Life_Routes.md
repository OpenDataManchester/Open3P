---
title: Component End of Life Routes
description: The component end of life routes relationship list.
---

# Component End of Life Routes

The component end of life routes relationship list identifies the purposed and intended destination and process of this component once it has completed its role as packaging. This is only used in [components](../3_Data_Specification/3_3_Components.md).

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|componentEndOfLifeRouteIdentifier|`mandatory`|UUID|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|componentEndOfLifeRoute|`mandatory`|String|What is the intended end of life route for this component? The entry should be the [end of life route controlled list](../5_Controlled_Lists/5_016_End_Of_Life_Route.md) identifier.|
|orderOfPrecedence|`optional`|Integer|The order that end of life routes should be used. The preferred route denoted as 1, and the last best option being the biggest number.|
|componentDisruptors|`optional`|List|What challenges this end of life route for this component has. The entry should be the [component end of life route disruptors controlled list](../5_Controlled_Lists/5_008_Component_Disruptors.md) identifier.|

## Diagram

``` mermaid
erDiagram

  COMPONENTS }o..o{ COMPONENT_END_OF_LIFE_ROUTES : within
  COMPONENT_END_OF_LIFE_ROUTES {
    componentEndOfLifeRouteIdentifier UUID "*"
    componentEndOfLifeRoute String "*"
    orderOfPrecedence Integer
    componentDistruptors List
  }
  COMPONENT_END_OF_LIFE_ROUTES }o--o{ CONTROLLED_LISTS : attributes
  CONTROLLED_LISTS {
    endOfLifeRoute mandatory
    componentDistruptors mandatory
  }
```

## Template

Component end of life routes should be provided as a separate csv file. The specification of this csv file is as follows:

[Component End of Life Routes](https://www.open3p.org/wp-content/uploads/2023/09/componentEOLRoutes20230922.csv)