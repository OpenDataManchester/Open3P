---
title: Key Concepts
description: The key concepts to understanding the open data standard for the packaging value chain.
---

# Key Concepts

The Open 3P data standard is to provide information about what packaging is made out of and how these materials flow through the packaging supply chain. With Open 3P, stakeholders in the packaging supply chain will be able to share information about materials, components and packaging in a standardised format. This will allow for better collaboration between manufacturers, brands, retailers, consumers, recyclers, compliance schemes and regulators.

sequenceDiagram
    participant manufacturers
    participant brands
    participant retailers
    participant consumers
    participant recyclers
    participant compliance
    participant regulators
    manufacturers->>brands movement
    manufacturers->>retailers movement
    manufacturers->>compliance movement
    manufacturers->>regulators movement
    brands->>retailers movement
    brands->>consumers movement
    brands->>recyclers movement
    brands->>compliance movement
    brands->>regulators movement
    retailers->>consumers movement
    retailers->>recyclers movement
    retailers->>compliance movement
    retailers->>regulators movement
    consumers->>recyclers movement
    recyclers->>manufacturers movement
    compliance->>regulators movement

# Definitions

## Base Materials
- general template used to store information about a base level material

## Materials
- an individual substance (e.g., PET)
- created from the base materials level

## Components
- an individual unit (e.g., a bottle)
- parts made from different materials (e.g., a window on a sandwich box)
- zippers, taps, etc. (even though attached)
- general template used for packaging manufacturers to store information.
- these components can be used by multiple users and combined with other components in different ways

## Product
- That which is contained inside of the packaging

## Complete Packaging
- Components are combined to make complete packaging
- for example, a lid, a bottle and a label are all individual components. These would be combined to form a complete packaging item

## Multipack
- Sometimes, multiple units of complete packaging are combined, and sold as a single unit
- This is a multipack

## Load Catalogue
- Complete packaging units are combined into a delivery load
- Usually wrapped in secondary and tertiary packaging 

## Load
- Collection of load catalogue broken into destinations and on-the-market packaging for specified reporting periods

## Packaging Item
- A component, complete packaging, or multipack 

## Reuse
- The packaging item remains as created and is repurposed without reconstruction

## Recycle
- The packaging item is broken down and created into something new


