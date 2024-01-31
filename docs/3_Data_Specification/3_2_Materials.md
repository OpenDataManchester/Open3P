---
title: Materials
description: Materials are a combination of base materials within Open 3P.
---

# Materials

The materials schema contains information regarding the materials that are used within components. These maybe a single material from base materials, a combination of base materials and/or a material from the materials schema itself.

## Table
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`mandatory`|UUID|The globally unique identifier for the created material unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|name|`optional`|String|The name of the material this row relates to. (e.g., Aluminium 3000 Series or Borosilicate glass)|
|externalIdentifiers|`optional`|Dictionary|A dictionary of identifiers that might be used to identify the material in other systems. For example: manufacturer's own internal identifier, bar codes or global trade item number (gtin). To provide external identifiers please follow this format. `{'externalIdentifierName1': 'identifier1', 'externalIdentifierName2': 'identifier2'}`|
|materialConstituents|`mandatory`|List|The information regarding the consituents that are combined to create this material. The entries should be from the [Material Constituents Relationship List](../6_Relationship_Lists/6_001_Material_Constituents.md) identifier.|
|combinationPurpose|`optional`|String|Why is this material being used? Use the identifier of the function that this row relates to. The entry here should be drawn from the [Function Controlled List](../5_Controlled_Lists/5_004_Function.md).|
|areaDensity|`optional`|Decimal|The area density of the material. Where area density is the measure of how much mass is packed into a given area of a two-dimensional object. Provided in grams per square metre (gsm).|
|areaDensityUnit|`optional`|String|Either `gsm` or `m^2/kg` to describe the area density unit of measure.|
|areaDensityTolerance|`optional`|Decimal|The threshold of area density that the material can vary by. This is given as a +/- value.|
|areaDensityToleranceType|`optional`|String|Either `unit` or `percentage` based on the value provided in `areaDensityTolerance`. Where `unit` is equal to the value provided in `areaDensityUnit`.|
|areaDensityDate|`optional`|Date|The date that the area density was last verified/measured. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|
|certification|`optional`|Boolean|Does the material have a certificate (e.g. FSC, REACH, FSA etc.)? Answer as: `TRUE` for yes and `FALSE` for no.|
|certificationClaims|`optional`|List|The information regarding the certification. The entries should be the [Certification Claims Relationship List](../6_Relationship_Lists/6_005_Certification_Claims.md) identifiers.|
|manufacturers|`optional`|List|The information regarding the manufacturer(s). The entries should be the [Organisations Relationship List](../6_Relationship_Lists/6_010_Organisations.md) identifiers.|
|manufacturedCountry|`optional`|String|The country the component was manufactured in. Use the country numeric [ISO codes](https://www.iso.org/obp/ui/#search){target=_blank} as described in the [ISO 3166 international standard](https://www.iso.org/iso-3166-country-codes.html){target=_blank}.|
|updateDate|`mandatory`|Date|The date that the material was provided/last updated. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|

## Diagram

``` mermaid
erDiagram
BASE_MATERIALS }o--o{ MATERIALS : material_constituents
  MATERIALS {
    identifier UUID "*"
    name String
    externalIdentifiers Dictionary
    materialConstituents List "*"
    combinationPurpose String
    areaDensity Decimal
    areaDensityUnit String
    areaDensityTolerance Decimal
    areaDensityToleranceType String
    areaDensityDate Date
    certification Boolean
    certificationClaims List
    manufacturers List
    manufacturedCountry String
    updateDate Date "*"
  }
  MATERIALS }o..o{ CONTROLLED_LISTS : attributes
  MATERIALS }o--o{ COMPONENTS : component_constituents
  MATERIALS }o..o{ RELATIONSHIP_LISTS : attributes
        CONTROLLED_LISTS {
    function optional
    }
        RELATIONSHIP_LISTS {
    certificationClaims optional
    organisations optional
      }
```

## Template
Materials should be provided as a separate csv file. The specification of this csv file is as follows:

[Materials Template](https://www.open3p.org/wp-content/uploads/2023/09/materials20230922.csv){target=_blank}

## Example

=== "Cardboard - JSON"

    ``` json linenums="1" hl_lines="3 4"
    [
      {
        "identifier": "16f41cca-1a77-4e31-8b0f-2723f752317b",
        "name":"Cardboard",
        "externalIdentifiers": {
          "sapPK":"153517",
          "SKU":"34-56bg"
          },
          "materialConstituents": [
            {
              "materialConstituentsIdentifier": "95b95bf7-80c0-49bc-9367-ae48d6c107d3",
              "materialCombinationIdentifier": "222494f7-6703-49bc-a993-8dd2675709fb"
            }
          ],
        "combinationPurpose": "function-0048",
        "areaDensity": "300",
        "areaDensityUnit": "gsm",
        "areaDensityTolerance": "3.3",
        "areaDensityToleranceType": "percentage",
        "areaDensityDate": "2023-12-07",
        "certification": true,
        "certificationClaims": ["307801c3-f6f7-4ca6-8553-6f367b37fd1e"],
        "manufacturers": ["GB-COH-10906273"],
        "manufacturedCountry": "826",
        "updateDate": "2023-12-07",
      }
    ]
    ```
=== "Glass - JSON"

    ``` json linenums="1" hl_lines="3 4"
    [
      {
        "identifier": "b050ab75-4bcb-4c7f-b8f5-8a1f9e5ba7d3",
        "name": "Glass",
        "externalIdentifiers": {
          "internal id": "70-wine-glass"
          },
        "materialConstituents": [
          {
            "materialConstituentsIdentifier": "11eb7b61-05f1-4894-a57b-80e5082f944a",
            "materialCombinationIdentifier": "ff39892f-0a88-4085-9942-4522cecc8337"
          },
          {
            "materialConstituentsIdentifier": "11eb7b61-05f1-4894-a57b-80e5082f944a",
            "materialCombinationIdentifier": "1bdca07b-ed6a-4799-a027-654322cb302f"
          },
          {
            "materialConstituentsIdentifier": "11eb7b61-05f1-4894-a57b-80e5082f944a",
            "materialCombinationIdentifier": "ff39892f-0a88-4085-9942-4522cecc8337"
          },
          {
            "materialConstituentsIdentifier": "11eb7b61-05f1-4894-a57b-80e5082f944a",
            "materialCombinationIdentifier": "42b19543-7138-43ff-a867-a1e551ccba14"
          }
        ],
        "combinationPurpose": "function-0005",
        "certification": false,
        "manufacturers": ["GB-COH-10906273"],
        "manufacturedCountry": "826",
        "updateDate": "2022-08-01"
      }
    ]
    ```

## Data flow

``` mermaid
flowchart LR
    subgraph baseMaterials[Base Materials]
        bm_cardboard["Cardboard
        -
        222494f7-6703-49bc-a993-8dd2675709fb"]
        bm_sodaAsh["Soda ash
        -
        ff39892f-0a88-4085-9942-4522cecc8337"]
        bm_cullet["Cullet
        -
        db481bb7-e57a-4af7-8821-2258338ddd11"]
        bm_sand["Sand
        -
        1bdca07b-ed6a-4799-a027-654322cb302f"]
        bm_limestone["Limestone
        -
        42b19543-7138-43ff-a867-a1e551ccba14"]
    end
    subgraph materials[Materials]
        ma_cardboard["`**Cardboard
        -
        16f41cca-1a77-4e31-8b0f-2723f752317b**`"]
        ma_glass["`**Glass
        -
        b050ab75-4bcb-4c7f-b8f5-8a1f9e5ba7d3**`"]
    end
        subgraph components[Components]
        co_example[example components]
    end
    bm_cardboard --> ma_cardboard
    bm_sodaAsh --> ma_glass
    bm_cullet --> ma_glass
    bm_sand --> ma_glass
    bm_limestone --> ma_glass
    ma_cardboard --> components
    ma_glass --> components
```

## Guide for how to take measurements

### Units

All measurements should be given using the metric system.

- Weight: grams (g)
- Area Density: grams per square metre (gsm) or square metres per kilogram (m^2/kg)

Numbers should be entered with a decimal place. Use the decimal / full stop / period character as a separator. Do not exceed 3 decimal places. When rounding, use convential rounding methods: for 5 and above round up, 4 and below round down. For example: volume = 0.67952 rounded to 0.68. 

**Important**: When converting between systems of measurement, perform the conversion first and then apply the convential rounding. This will give more accuracy and consistency.
