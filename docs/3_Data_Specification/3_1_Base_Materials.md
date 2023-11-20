---
title: Base Materials
description: Base materials are the building blocks of Open 3P.
---

# Base Materials

The base materials schema contains information regarding the core materials. These are then combined together within the materials table to create more complicated materials.

## Table
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`required`|String|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|baseMaterialName|`required`|String|The name of the base material this row relates to. `e.g., Polypropylene or Aluminium or Silica`|
|baseMaterialType|`recommended`|String|Is the base material 'synthetic' or 'biobased'? Use the identifier of the material type that this row relates to. The entry here should be drawn from the [Material Type Controlled List](../5_Controlled_Lists/5_001_Material_Type.md).|
|materialChemCID|`recommended`|String|The PubChem CID for the exact base material used. The PubChem CID is PubChem's compound identifier, which is a non-zero integer for a unique chemical structure. PubChem CID can be found using their [search](https://pubchem.ncbi.nlm.nih.gov/){target=_blank}. If for some reason the PubChem CID cannot be located, consider contributing to PubChem and create the compound identifier. However, if this cannot be done, please enter `Unknown`.|
|externalIdentifiers|`recommended`|Dictionary|A dictionary of identifiers that might be used to identify the base material in other systems. For example: manufacturer's own internal identifier, bar codes or global trade item number (gtin). To provide external identifiers please follow this format. `{'externalIdentifierName1': 'identifier1', 'externalIdentifierName2': 'identifier2'}`|
|certification|`recommended`|Boolean|Does the base material have a certificate (e.g. FSC, REACH, FSA etc.)? Answer as: `TRUE` for yes and `FALSE` for no.|
|certificationClaims|`recommended`|List|The information regarding the certification. The entries should be the [Certification Claims Relationship List](../6_Relationship_Lists/6_005_Certification_Claims.md) identifiers.|
|manufacturedCountry|`recommended`|Numeric|The country the component was manufactured in. Use the country numeric [ISO codes](https://www.iban.com/country-codes){target=_blank} as described in the ISO 3166 international standard.|
|updateDate|`required`|String|The date that the base material was provided/last updated. Use the format `dd/mm/yyyy`.|

## Diagram

``` mermaid
erDiagram
  BASE_MATERIALS {
    identifier String
    baseMaterialName String
    baseMaterialType String
    materialChemCID String
    externalIdentifiers Dictionary
    certification Boolean
    certificationClaims List
    manufacturedCountry Numeric
    updateDate String
  }
  BASE_MATERIALS }o..o{ CONTROLLED_LISTS : attributes
  BASE_MATERIALS }o--o{ MATERIALS : within
  BASE_MATERIALS }o..o{ RELATIONSHIP_LISTS : attributes
  CONTROLLED_LISTS {
    materialType recommended 
  }
  RELATIONSHIP_LISTS {
    certificationClaims recommended
  }
```

## Template

Base materials should be provided as a separate csv file. The specification of this csv file is as follows:

[Base Materials Template](https://www.open3p.org/wp-content/uploads/2023/09/baseMaterials20230922.csv){target=_blank}

## Example

=== "JSON #1"

    ``` json linenums="1"
    --FSC accredited wood grown in Spain
    {
      "identifier": "a5e6b8bc-ade8-4660-857e-d397243f6b57",
      "baseMaterialName": "Spainish Softwood",
      "baseMaterialType": "",
      "materialChemCID": "",
      "externalIdentifiers": {
        "dbPK":"152314568888",
        },
      "certification": "TRUE",
      "certificationClaims": ["1","35"],
      "certificationDate": "01/08/2022",
      "manufacturedCountry": 724,
      "updateDate": "01/08/2022",
    }
    ```
=== "JSON #2"

    ``` json linenums="1"
    --Food grade synthetic polyethylene terephthalate (PET) made in the UK - verbose data structure
    {
      "identifier": "A4BAE07C-1847-CD8E-C933-6FD30478423B",
      "baseMaterialName": "PET",
      "baseMaterialType": {
        "identifier":"bm-material-type-0002",
        "category":"synthetic",
        "detailed":"derived from crude oil, natural gas or coal."
      },
      "materialChemCID": "223961227",
      "externalIdentifiers": {
        "primaryKey":"9187e576-0dfd-46dd-809e-4af0a35f888d",
        },
      "certification": "TRUE",
      "certificationClaims": [{
        "certificationIdentifier": "2e32b7cc-5fa8-425f-a2c0-784340e43f36",
        "certificationSource": {
          "identifier":"certification-source-0002",
          "category":"FSA",
          "detailed":"The Food Standards Agency (FSA) is the independent government department working to protect public health and consumers’ wider interests in relation to food in England, Wales and Northern Ireland."
        },
        "certificationDate": "01/08/2022",
      }],
      "manufacturedCountry": {
        "Country": "United Kingdom of Great Britain and Northern Ireland (the)",
        "Numeric": 826
      },
      "updateDate": "01/08/2022",
    }
    ```
=== "CSV download"

    * [Material Catalogue example download](https://www.opendatamanchester.org.uk/wp-content/uploads/2023/01/7_1_7_Materials_Catalogue_Example.csv){target=_blank}