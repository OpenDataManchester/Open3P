---
title: Materials
description: Materials are a combination of base materials within Open 3P.
---

# Materials

The materials schema contains information regarding the materials that are used within components. These maybe a single material from the base materials catalogue, a combination of base materials and/or a material from the materials schema itself.

## Table
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`required`|String|The globally unique identifier for the created material unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|materialName|`required`|String|The name of the material this row relates to. (e.g., Aluminium 3000 Series or Borosilicate glass)|
|externalIdentifiers|`recommended`|Dictionary|A dictionary of identifiers that might be used to identify the material in other systems. For example: manufacturer's own internal identifier, bar codes or global trade item number (gtin). To provide external identifiers please follow this format. `{'externalIdentifierName1': 'identifier1', 'externalIdentifierName2': 'identifier2'}`|
|materialConstituents|`required`|List|The information regarding the consituents that are combined to create this material. The entries should be from the [Material Constituents Relationship List](../6_Relationship_Lists/6_001_Material_Constituents.md) identifier.|
|combinationPurpose|`recommended`|String|Why is this material being used? Use the identifier of the function that this row relates to. The entry here should be drawn from the [Function Controlled List](../5_Controlled_Lists/5_004_Function.md).|
|areaDensity|`recommended`|Numeric|The area density of the material. Where area density is the measure of how much mass is packed into a given area of a two-dimensional object. Provided in grams per square metre (gsm).|
|areaDensityUnit|`recommended`|String|Either `gsm` or `m^2/kg` to describe the area unit of measure.|
|areaDensityTolerance|`recommended`|Numeric|The threshold of area density that the material can vary by. This is given as a +/- value.|
|areaDensityToleranceType|`recommended`|String|Either `unit` or `percentage` based on the value provided in `areaDensityTolerance`. Where `unit` is equal to the value provided in `areaDensityUnit`.|
|areaDensityDate|`recommended`|String|The date that the area density was last verified/measured. Use the format `dd/mm/yyyy`.|
|certification|`recommended`|Boolean|Does the material have a certificate (e.g. FSC, REACH, FSA etc.)? Answer as: `TRUE` for yes and `FALSE` for no.|
|certificationClaims|`recommended`|List|The information regarding the certification. The entries should be the [Certification Claims Relationship List](../6_Relationship_Lists/6_005_Certification_Claims.md) identifiers.|
|manufacturers|`recommended`|List|The information regarding the manufacturer(s). The entries should be the [Organisations Relationship List](../6_Relationship_Lists/6_010_Organisations.md) identifiers.|
|manufacturedCountry|`recommended`|Numeric|The country the component was manufactured in. Use the country numeric [ISO codes](https://www.iban.com/country-codes){target=_blank} as described in the ISO 3166 international standard.|
|updateDate|`required`|String|The date that the material was provided/last updated. Use the format `dd/mm/yyyy`.|

## Diagram

``` mermaid
erDiagram
BASE_MATERIALS }o--o{ MATERIALS : within
  MATERIALS {
    identifier String
    materialName String
    externalIdentifiers Dictionary
    materialConstituents List
    combinationPurpose String
    areaDensity Numeric
    areaDensityUnit String
    areaDensityTolerance Numeric
    areaDensityToleranceType String
    areaDensityDate String
    certification Boolean
    certificationClaims List
    manufacturers List
    manufacturedCountry Numeric
    updateDate String
  }
  MATERIALS }o..o{ CONTROLLED_LISTS : attributes
  MATERIALS }o--o{ COMPONENTS : within
  MATERIALS }o..o{ RELATIONSHIP_LISTS : attributes
        CONTROLLED_LISTS {
    function recommended
    }
        RELATIONSHIP_LISTS {
    materialConstituents required
    certificationClaims recommended
    organisations recommended
      }
```

## Template
Materials should be provided as a separate csv file. The specification of this csv file is as follows:

[Materials Template](https://www.open3p.org/wp-content/uploads/2023/09/materials20230922.csv){target=_blank}

## Example

=== "JSON #1"

    ``` json linenums="1"
    --Food grade synthetic polyethylene terephthalate (PET) made in the UK. Only one base material.
    {
      "identifier": "DCEE1F88-A83B-5BBC-D2D9-6A862B344977",
      "materialName":"PET",
      "externalIdentifiers": {
        "GTIN":"123456789101",
        },
      "materialConstituents":["DCEE1F88-A83B-5BBC-D2D9-6A862B344977"],
      "combinationPurpose": "",
      "areaDensity": "138",
      "areaDensityUnit": "gsm",
      "areaDensityTolerance": "3.3",
      "areaDensityToleranceType": "percentage",
      "areaDensityDate": "01/08/2022",
      "certification": "TRUE",
      "certificationClaims": ["1"],
      "manufacturers": [""],
      "manufacturedCountry": 826,
      "updateDate": "01/08/2022",
    }
    ```
=== "JSON #2"

    ``` json linenums="1"
    --Fibre based composite material to be used for a carton - semi verbose
    {
      "identifier": "f87b9bb3-f141-41cf-986e-e3a32b223f09",
      "materialName": "Classic Carton Board - EVOH",
      "externalIdentifiers": {
        "EAN": "0123456789101",
        "BatchNumber": "2145-23-po"
        },
      "materialConstituents": [
        {
          "materialConstituentsIdentifier": "f87b9bb3-f141-41cf-986e-e3a32b223f09",
          "materialCombinationIdentifier": {
            "identifier": "3ca24db2-84d5-4681-aa16-136fbdba101f",
            "baseMaterialName": "Polyethylene",
            "baseMaterialType": {
              "identifier":"bm-material-type-0002",
              "category":"synthetic",
              "detailed":"derived from crude oil, natural gas or coal."
            },
            "materialChemCID": null,
            "externalIdentifiers": {
              "pk":"12",
              },
            "certification": "FALSE",
            "certificationClaims": null,
            "manufacturers": [""],
            "manufacturedCountry": {
              "Country": "United Kingdom of Great Britain and Northern Ireland (the)",
              "Numeric": 826
            },
            "updateDate": "01/08/2022",
          },
          "materialPurpose": {
            "identifier": "m-material-purpose-0005",
            "category": "barrier",
            "detailed": "Used to reduce water and gas diffusion into and/or out of the material."
          },
          "virginMaterial": 100,
          "layer": 1,
          "materialPercentage": 7
        },
        {
          "materialConstituentsIdentifier": "f87b9bb3-f141-41cf-986e-e3a32b223f09",
          "materialCombinationIdentifier": "96245c85-5671-4f3d-875f-82665005e9e8",
          "materialPurpose": {
            "identifier": "m-material-purpose-0015",
            "category": "structure",
            "detailed": "Providing strength and stability."
          },
          "virginMaterial": 100,
          "layer": 2,
          "materialPercentage": 27
        },
        {
          "materialConstituentsIdentifier": "f87b9bb3-f141-41cf-986e-e3a32b223f09",
          "materialCombinationIdentifier": {
            "identifier": "3ca24db2-84d5-4681-aa16-136fbdba101f",
            "baseMaterialName": "Polyethylene",
            "baseMaterialType": {
              "identifier":"bm-material-type-0002",
              "category":"synthetic",
              "detailed":"derived from crude oil, natural gas or coal."
            },
            "materialChemCID": null,
            "externalIdentifiers": {
              "pk":"12",
              },
            "certification": "FALSE",
            "certificationClaims": null,
            "manufacturers": [""],
            "manufacturedCountry": {
              "Country": "United Kingdom of Great Britain and Northern Ireland (the)",
              "Numeric": 826
            },
            "updateDate": "01/08/2022",
          },
          "materialPurpose": {
            "identifier": "m-material-purpose-0002",
            "category": "adhesive",
            "detailed": "Applied to one or both surfaces of two separate items that binds them together and resists their separation."
          },
          "virginMaterial": 100,
          "layer": 3,
          "materialPercentage": 7
        },
        {
          "materialConstituentsIdentifier": "f87b9bb3-f141-41cf-986e-e3a32b223f09",
          "materialCombinationIdentifier": "ff249e1f-5015-46b8-8655-6c920fbf2606",
          "materialPurpose": {
            "identifier": "m-material-purpose-0003",
            "category": "antioxidant",
            "detailed": "Used to inhibit oxidation."
          },
          "virginMaterial": 100,
          "layer": 4,
          "materialPercentage": 18
        },
        {
          "materialConstituentsIdentifier": "f87b9bb3-f141-41cf-986e-e3a32b223f09",
          "materialCombinationIdentifier": {
            "identifier": "3ca24db2-84d5-4681-aa16-136fbdba101f",
            "baseMaterialName": "Polyethylene",
            "baseMaterialType": {
              "identifier":"bm-material-type-0002",
              "category":"synthetic",
              "detailed":"derived from crude oil, natural gas or coal."
            },
            "materialChemCID": null,
            "externalIdentifiers": {
              "pk":"12",
              },
            "certification": "FALSE",
            "certificationClaims": null,
            "manufacturers": [""],
            "manufacturedCountry": {
              "Country": "United Kingdom of Great Britain and Northern Ireland (the)",
              "Numeric": 826
            },
            "updateDate": "01/08/2022",
          },
          "materialPurpose": {
            "identifier": "m-material-purpose-0002",
            "category": "adhesive",
            "detailed": "Applied to one or both surfaces of two separate items that binds them together and resists their separation."
          },
          "virginMaterial": 100,
          "layer": 5,
          "materialPercentage": 7
        },
        {
          "materialConstituentsIdentifier": "f87b9bb3-f141-41cf-986e-e3a32b223f09",
          "materialCombinationIdentifier": "96245c85-5671-4f3d-875f-82665005e9e8",
          "materialPurpose": {
            "identifier": "m-material-purpose-0015",
            "category": "structure",
            "detailed": "Providing strength and stability."
          },
          "virginMaterial": 100,
          "layer": 6,
          "materialPercentage": 27
        },
        {
          "materialConstituentsIdentifier": "f87b9bb3-f141-41cf-986e-e3a32b223f09",
          "materialCombinationIdentifier": {
            "identifier": "3ca24db2-84d5-4681-aa16-136fbdba101f",
            "baseMaterialName": "Polyethylene",
            "baseMaterialType": {
              "identifier":"bm-material-type-0002",
              "category":"synthetic",
              "detailed":"derived from crude oil, natural gas or coal."
            },
            "materialChemCID": null,
            "externalIdentifiers": {
              "pk":"12",
              },
            "certification": "FALSE",
            "certificationClaims": null,
            "manufacturers": [""],
            "manufacturedCountry": {
              "Country": "United Kingdom of Great Britain and Northern Ireland (the)",
              "Numeric": 826
            },
            "updateDate": "01/08/2022",
          },
          "materialPurpose": {
            "identifier": "m-material-purpose-0005",
            "category": "barrier",
            "detailed": "Used to reduce water and gas diffusion into and/or out of the material."
          },
          "virginMaterial": 100,
          "layer": 7,
          "materialPercentage": 7
        },
      ],
      "combinationPurpose": {
        "identifier": "function-0012",
        "category": "carton",
        "detailed": "Box or container used for transporting and storaging goods."
      },
      "areaDensity": "543.5",
      "areaDensity": "gsm",
      "areaDensityTolerance": "6",
      "areaDensityToleranceType": "unit",
      "areaDensityDate": "01/08/2022",
      "certification": "FALSE",
      "certificationClaims": null,
      "manufacturers": [""],
      "manufacturedCountry": {
        "Country": "United Kingdom of Great Britain and Northern Ireland (the)",
        "Numeric": 826
      },
      "updateDate": "01/08/2022"
    }
    ```
=== "CSV download"

    * [Materials example download](https://www.opendatamanchester.org.uk/wp-content/uploads/2023/01/7_1_2_Materials_Example.csv){target=_blank}

## Guide for how to take measurements

### Units

All measurements should be given using the metric system.

- Weight: grams (g)
- Area Density: grams per square metre (gsm) or square metres per kilogram (m^2/kg)

Numbers should be entered with a decimal place. Use the decimal / full stop / period character as a separator. Do not exceed 3 decimal places. When rounding, use convential rounding methods: for 5 and above round up, 4 and below round down. For example: volume = 0.67952 rounded to 0.68. 

**Important**: When converting between systems of measurement, perform the conversion first and then apply the convential rounding. This will give more accuracy and consistency.
