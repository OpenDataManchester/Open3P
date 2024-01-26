---
title: Core Schema
description: The Core schema section of Open 3P contains the main structure of the standard.
---

# Core Schema

The core schemas in Open 3P serve as the functional backbone, streamlining the flow of data from the foundational material to the ultimate combined load of product and packaging. Open 3P deliberately emphasises essential elements to facilitate seamless data exchange across the supply chain. Whenever feasible fields are kept optional ensuring flexibility. Only fields necessary for efficient data exchange and compliance with current regulations are mandatory.

## The schemas

There are six core schemas that are the foundations of Open 3P.

<div class="grid cards" markdown>

-   __Base Materials__

    ---

    Contains information regarding the materials at the very start of the process of creating packaging.

    [:octicons-arrow-right-24: Base materials](./3_1_Base_Materials.md)

-   __Materials__

    ---

    Contains information about how base materials are combined to create more complex materials.

    [:octicons-arrow-right-24: Materials](./3_2_Materials.md)

-   __Components__

    ---

    Contains the information about how materials are formed into indivudal components. This schema is where packaging starts taking form.

    [:octicons-arrow-right-24: Components](./3_3_Components.md)

-   __Complete Packages__

    ---

    Contains the information on how components are combined together to protect or market a product. This schema is where packaging is fulfilling its role.

    [:octicons-arrow-right-24: Complete Packages](./3_4_Complete_Packaging.md)

-   __Multipacks (optional)__

    ---

    Contains the information on the packaging used to protect multipacks of products.

    [:octicons-arrow-right-24: Multipacks](./3_5_Multipack.md)

-   __Loads__

    ---

    Contains the information regard all the packaging used to transport product(s) to a destination.

    [:octicons-arrow-right-24: Loads](./3_7_Load.md)


</div>

## The flow
As mentioned Open 3P has been designed to allow information to flow from base materials all the way through to a load. Below you can see how these are connected.
``` mermaid
flowchart LR
    subgraph baseMaterials[Base Materials]
        bm_example[base material]
    end
    subgraph materials[Materials]
        ma_example[material]
    end
    subgraph components[Components]
        co_example[component]
    end
    subgraph completePackages[Complete Packages]
        cp_example[complete package]
    end
    subgraph multipacks[Multipacks]
        mp_example[multipack]
    end
    subgraph loads[Loads]
        lo_example[load]
    end
    bm_example --> ma_example
    ma_example --> co_example
    co_example --> cp_example
    cp_example --> lo_example
    cp_example -.-> mp_example
    mp_example -.-> lo_example
```
Each schema (excluding base material) is linked and has a defined relationship with the schema to it's left. This join is important to faciliate the data exchange and to maintain the structure of the data.

## Diagram

``` mermaid
erDiagram
  BASE_MATERIALS }o--o{ MATERIALS : material_constituents
  MATERIALS }o--o{ COMPONENTS : component_constituents
  COMPONENTS }o--o{ COMPLETE_PACKAGING : complete_packaging_constituents
  COMPLETE_PACKAGING }o..o{ MULTIPACK : multipack_constituents
  COMPONENTS }o..o{ MULTIPACK : multipack_constituents
  BASE_MATERIALS }o..o{ LOADS : load_constituents
  MATERIALS }o..o{ LOADS : load_constituents
  COMPLETE_PACKAGING }o..o{ LOADS : load_constituents
  MULTIPACK }o..o{ LOADS : load_constituents
  COMPONENTS }o..o{ LOADS : load_constituents
```

The diagram above shows how the six core schemas interact with each other including their [relationship lists](../6_Relationship_Lists/6_000_Relationship_Lists.md) as these additional entities allow for additional functionality within Open 3P.

The following pages detail the information in each of the schemas, and further show how the core schema work with both the controlled lists and the relationship lists.

