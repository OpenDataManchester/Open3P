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