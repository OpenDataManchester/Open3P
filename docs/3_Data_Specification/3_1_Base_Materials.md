---
title: Base Materials
description: Base materials are the building blocks of Open 3P.
---

# Base Materials

The base materials schema contains information regarding the materials at the very start of the process of creating packaging. These are then combined together within the materials table to create more complicated materials.

!!! question "Frequently Asked Question"

    Do all packaging items need to contain a `Base Material`?  
    Yes, every packaging item must include a Base Material. This foundational component serves as the building block for all packaging materials. The level of detail in specifying base material(s) can vary based on requirements. For more in-depth insights, refer to the Data Flow section.

## Table
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`mandatory`|UUID|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier.|
|name|`mandatory`|String|The name of the base material this row relates to. `e.g., Polypropylene or Aluminium or Silica`.|
|type|`optional`|String|What type of base material is this? The entry here should be drawn from the [Material Type Controlled List](../5_Controlled_Lists/5_001_Material_Type.md).|
|materialChemCID|`optional`|String|The PubChem CID for the exact base material used. The PubChem CID is PubChem's compound identifier, which is a non-zero integer for a unique chemical structure. PubChem CID can be found using their [search](https://pubchem.ncbi.nlm.nih.gov/){target=_blank}. If for some reason the PubChem CID cannot be located, consider contributing to PubChem and create the compound identifier. However, if this cannot be done, please enter `Unknown`.|
|externalIdentifiers|`optional`|Dictionary|A dictionary of identifiers that might be used to identify the base material in other systems. For example: manufacturer's own internal identifier, bar codes or global trade item number (gtin). To provide external identifiers please follow this format. `{'externalIdentifierName1': 'identifier1', 'externalIdentifierName2': 'identifier2'}`|
|measurements|`optional`|List|The information regarding the measurements of the base material. The entries should be from the [Measurements Relationship List](../6_Relationship_Lists/6_012_Measurements.md).|
|certification|`optional`|Boolean|Does the base material have a certificate (e.g. FSC, REACH, FSA etc.)? Answer as: `TRUE` for yes and `FALSE` for no.|
|certificationClaims|`optional`|List|The information regarding the certification. The entries should be the [Certification Claims Relationship List](../6_Relationship_Lists/6_005_Certification_Claims.md) identifiers.|
|manufacturers|`optional`|List|The information regarding the manufacturer(s). The entries should be the [Organisations Relationship List](../6_Relationship_Lists/6_010_Organisations.md) identifiers.|
|manufacturedCountry|`optional`|String|The country the component was manufactured in. Use the country numeric [ISO codes](https://www.iso.org/obp/ui/#search){target=_blank} as described in the [ISO 3166 international standard](https://www.iso.org/iso-3166-country-codes.html){target=_blank}.|
|updateDate|`mandatory`|Date|The date that the base material was provided/last updated. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html){target=_blank}.|

## Diagram

``` mermaid
erDiagram
  BASE_MATERIALS {
    identifier UUID "*"
    name String "*"
    type String
    materialChemCID String
    externalIdentifiers Dictionary
    measurements List
    certification Boolean
    certificationClaims List
    manufacturers List
    manufacturedCountry String
    updateDate Date "*"
  }
  BASE_MATERIALS }o..o{ CONTROLLED_LISTS : attributes
  BASE_MATERIALS }o--o{ MATERIALS : material_constituents
  BASE_MATERIALS }o..o{ RELATIONSHIP_LISTS : attributes
  CONTROLLED_LISTS {
    materialType optional
  }
  RELATIONSHIP_LISTS {
    certificationClaims optional
    organisations optional
    measurements optional
  }
```

## Example

=== "Cardboard - JSON"

    ``` json linenums="1" hl_lines="3 4"
    [
      {
        "identifier": "222494f7-6703-49bc-a993-8dd2675709fb",
        "name": "Cardboard",
        "type": "bm-material-type-0001",
        "externalIdentifiers": {
          "sapPK":"153516",
          "SKU":"34-56bg"
          },
        "certification": true,
        "certificationClaims":  
          ["352d6f90-139b-429c-9018-2230ff03a40b"],
        "manufacturers": ["GB-COH-10906273"],
        "manufacturedCountry": "724",
        "updateDate": "2024-02-25"
      }
    ]
    ```
=== "Soda ash - JSON"

    ``` json linenums="1" hl_lines="3 4"
    [
      {
        "identifier": "ff39892f-0a88-4085-9942-4522cecc8337",
        "name": "Soda ash",
        "materialChemCID": "10340",
        "externalIdentifiers": {
          "internal id":"soda-ash-100-100"
          },
        "certification": false,
        "manufacturers": ["GB-COH-10906273"],
        "manufacturedCountry": "826",
        "updateDate": "2023-12-07"
      }
    ]
    ```
=== "Cardboard - XML"

    ``` xml linenums="1" hl_lines="3 4"
    <?xml version="1.0" encoding="UTF-8"?>
    <baseMaterial>
      <identifier>222494f7-6703-49bc-a993-8dd2675709fb</identifier>
      <name>Cardboard</name>
      <type>bm-material-type-0001</type>
      <externalIdentifiers>
        <sapPK>153516</sapPK>
        <SKU>34-56bg</SKU>
      </externalIdentifiers>
      <certification>true</certification>
      <certificationClaims>352d6f90-139b-429c-9018-2230ff03a40b</certificationClaims>
      <manufacturers>GB-COH-10906273</manufacturers>
      <manufacturedCountry>724</manufacturedCountry>
      <updateDate>2024-02-25</updateDate>
    </baseMaterial>
    ```
=== "Soda ash - XML"

    ``` xml linenums="1" hl_lines="3 4"
    <?xml version="1.0" encoding="UTF-8"?>
    <baseMaterial>
      <identifier>ff39892f-0a88-4085-9942-4522cecc8337</identifier>
      <name>Soda ash</name>
      <materialChemCID>10340</materialChemCID>
      <externalIdentifiers>
        <internal_id>soda-ash-100-100</internal_id>
      </externalIdentifiers>
      <certification>false</certification>
      <manufacturers>GB-COH-10906273</manufacturers>
      <manufacturedCountry>826</manufacturedCountry>
      <updateDate>2023-12-07</updateDate>
    </baseMaterial>
    ```
## Data flow

``` mermaid
flowchart LR
    subgraph baseMaterials["`**Base Materials**`"]
        bm_cardboard["`**Cardboard
        -
        222494f7-6703-49bc-a993-8dd2675709fb**`"]
        bm_sodaAsh["`**Soda ash
        -
        b050ab75-4bcb-4c7f-b8f5-8a1f9e5ba7d3**`"]
    end
    subgraph materials[Materials]
        ma_cardboard[example materials]
    end
    bm_cardboard --> materials
    bm_sodaAsh --> materials
```
