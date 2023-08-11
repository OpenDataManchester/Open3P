---
title: Key Concepts
description: The key concepts to understanding the open data standard for the packaging value chain.
---

# Key Concepts

The Open 3P data standard is to provide information about what packaging is made out of and how these materials flow through the packaging supply chain. With Open 3P, stakeholders in the packaging supply chain will be able to share information about materials, components and packaging in a standardised format. This will allow for better collaboration between manufacturers, brands, retailers, consumers, recyclers, compliance schemes and regulators.

## Packaging Ecosystem Data, Products, Waste Flows
The diagram below can help you to visualise how information might flow across the packaging supply chain using Open 3P. The standard supports data exchange between necessary parties whilst preserving a single source of truth across the industry.
``` mermaid
sequenceDiagram
    participant manufacturers
    participant brands
    participant retailers
    participant consumers
    participant recyclers
    participant complianceSchemes
    participant regulators
    manufacturers->>brands: products
    manufacturers->>retailers: products
    manufacturers->>complianceSchemes: data
    manufacturers->>regulators: data
    brands->>retailers: products
    brands->>consumers: products
    brands->>recyclers: waste
    brands->>complianceSchemes: data
    brands->>regulators: data
    retailers->>consumers: products
    retailers->>recyclers: waste
    retailers->>complianceSchemes: data
    retailers->>regulators: data
    consumers->>recyclers: waste
    recyclers->>manufacturers: material
    complianceSchemes->>regulators: data
```
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

## Controlled List
- Controlled Lists serve as reference points for key terms and phrases that are commonly used in the packaging industry, which are maintained and administred by the Standard Custodian Board (SCB)

## Relationship List
- Relationship lists are user-defined lists used in data standards to specify the relationships between different data elements. Unlike controlled lists relationship lists are populated by the user to provide context and clarity to the data being recorded

## UUID
- A machine readable unique identifier generated for an entry conforming to the standard
- UUIDs improve data flow by assigning an unambiguous tag to your data
- These IDs are then used to link between layers of the standard e.g. to link components to complete packaging

## Single Source of Truth
- In information science and information technology, single source of truth (SSOT) architecture, or single point of truth (SPOT) architecture, for information systems is the practice of structuring information models and associated data schemas such that every data element is mastered (or edited) in only one place.
- [Singe source of truth wikipedia article](https://en.wikipedia.org/wiki/Single_source_of_truth){target=_blank}