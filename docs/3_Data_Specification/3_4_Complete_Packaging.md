---
title: Complete Packaging
description: Complete packaging items are the finished packaging within Open 3P.
---

# Complete Packaging

The complete packaging schema contains information regarding the complete packages that are used to create loads. These maybe created from a single component or a combination of components from the components schema.

## Table
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`mandatory`|UUID|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|name|`optional`|String|The name of this complete packaging.|
|description|`optional`|String|A brief description of this complete packaging.|
|externalIdentifiers|`optional`|Dictionary|A dictionary of identifiers that might be used to identify the complete packaging in other systems. For example: manufacturer's own internal identifier, bar codes or global trade item number (gtin). To provide external identifiers please follow this format. `{'externalIdentifierName1': 'identifier1', 'externalIdentifierName2': 'identifier2'}`|
|imageURLs|`optional`|List|URL(s) that links to a picture of the complete packaging. Please see the guidelines below on how to capture the image and name the URL.|
|completePackagingConstituentsIdentifier|`mandatory`|List|The information regarding the consituents that are combined to create this complete packaging. The entries should be from the [Complete Packaging Constituents Relationship List](../6_Relationship_Lists/6_003_Complete_Packaging_Constituents.md) identifier.|
|LOWcodeWOproduct|`optional`|String|The list of waste code for **only** the complete packaging, by itself (excluding the product). LOW code is synonymous with European Waste Catalogue Code (EWC). For example: an empty bottle would have a LOWcode of `15 01 02`. Please use [Dsposal](https://dsposal.uk/browse/ewc){target=_blank} or [legislation.gov](https://www.legislation.gov.uk/uksi/2005/895/schedule/1/made){target=_blank} to find the LOWcode. **Note**: The LOWcode can based on its combination with other components and the actual product contained in the complete packaging. Be sure to only include the complete packaging LOWcode and not the complete packaging with the product. If you cannot find the code or are uncertain please enter `Uncertain`.|
|productType|`optional`|String|Information about the product contained in the complete packaging. The entry here should be drawn from the [product type controlled list](../5_Controlled_Lists/5_012_Product_Type.md).|
|LOWcodeWproduct|`optional`|String|The list of waste code for **everything** in the complete packaging. LOW code is synonymous with European Waste Catalogue Code (EWC). For example: an empty bottle would have a LOWcode of `15 01 02`. Please use [Dsposal](https://dsposal.uk/browse/ewc){target=_blank} or [legislation.gov](https://www.legislation.gov.uk/uksi/2005/895/schedule/1/made){target=_blank} to find the LOWcode. **Note**: The LOWcode can based on its combination with other components and the actual product contained in the complete packaging. Be sure to include the complete packaging LOWcode with the product. If you cannot find the code or are uncertain please enter `Uncertain`.|
|onTheGo|`mandatory`|Boolean|Is the complete packaging often classed as packaging that will end up in street bins? Answer as: `TRUE` for yes and `FALSE` for no.|
|householdWaste|`mandatory`|Boolean|Is the complete packaging often classed as packaging that will end up in kerbside collections? Answer as: `TRUE` for yes and `FALSE` for no.|
|depositReturnSchemes|`mandatory`|List|Which countries support a deposit return scheme for this particular complete packaging? The entries here should be drawn from the [deposit return scheme controlled list](../5_Controlled_Lists/5_013_Deposit_Return_Scheme.md).|
|completePackagingEndOfLifeRoutes|`optional`|List|The information regarding this complete packaging's proposed end of life routes. The entries should be the [complete packaging end of life routes](../6_Relationship_Lists/6_008_Complete_Packaging_End_of_Life_Routes.md) identifiers.|
|recyclability|`optional`|Boolean|Is the complete packaging recyclable (as determined by a reputable source)? Answer as: `TRUE` for yes and `FALSE` for no.|
|recyclabilityClaims|`optional`|List|The information regarding this recyclability claims. The entries should be the [recyclability claims relationship list](../6_Relationship_Lists/6_006_Recyclability_Claims.md) identifiers.|
|height|`optional`|Decimal|The height of the complete packaging. Please see the guidelines below on how to properly measure and report the height.|
|heightDate|`optional`|Date|The date that the height was last verified/measured. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|
|width|`optional`|Decimal|The width of the complete packaging. Please see the guidelines below on how to properly measure and report the width.|
|widthDate|`optional`|Date|The date that the width was last verified/measured. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|
|depth|`optional`|Decimal|The depth of the complete packaging. Please see the guidelines below on how to properly measure and report the depth.|
|depthDate|`optional`|Date|The date that the depth was last verified/measured. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|
|volume|`optional`|Decimal|Using the height, width, and depth found using the measurement guidelines, calculate the complete packaging's volume using: `height x width x depth`.|
|volumeDate|`optional`|Date|The date that the volume was last verified/measured. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|
|weight|`mandatory`|Decimal|The weight of the complete packaging.|
|weightTolerance|`mandatory`|Decimal|The threshold of weight that complete packaging can vary by. This can be given in grams or percentage.|
|weightToleranceType|`mandatory`|String|Either `grams` or `percentage` based on the value provided in `weightTolerance`|
|weightDate|`optional`|Date|The date that the weight was last verified/measured. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|
|servingCapacity|`optional`|Integer|The serving capacity of the complete packaging - how much of a product that can be contained in the complete packaging.|
|servingCapacityDate|`optional`|Date|The date that the serving capacity was last verified/measured. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|
|partOfMultipack|`mandatory`|Boolean|Is the complete packaging part of a multipack? Answer as: `TRUE` for yes and `FALSE` for no.|
|certification|`optional`|Boolean|Does the complete packaging have a certificate (e.g. FSC, REACH, FSA etc.)? Answer as: `TRUE` for yes and `FALSE` for no.|
|certificationClaims|`optional`|List|The information regarding the certifications. The entries should be the [certification claims relationship list](../6_Relationship_Lists/6_005_Certification_Claims.md) identifiers.|
|manufacturers|`optional`|List|The information regarding the manufacturer(s). The entries should be the [Organisations Relationship List](../6_Relationship_Lists/6_010_Organisations.md) identifiers.|
|manufacturedCountry|`optional`|String|The country the component was manufactured in. Use the country numeric [ISO codes](https://www.iso.org/obp/ui/#search){target=_blank} as described in the [ISO 3166 international standard](https://www.iso.org/iso-3166-country-codes.html){target=_blank}.|
|updateDate|`mandatory`|Date|The date that the complete packaging was provided/last updated. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|
|releaseDate|`optional`|Date|The date that the complete packaging will be available to use. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|
|discontinueDate|`optional`|Date|The date that the complete packaging will no longer be available to use. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|

## Diagram

``` mermaid
erDiagram
COMPONENTS }o--o{ COMPLETE_PACKAGING : complete_packaging_constituents
  COMPLETE_PACKAGING {
    identifier UUID "*"
    name String
    description String
    externalIdentifiers Dictionary
    imageURLs List
    completePackagingConstituentsIdentifier List "*"
    LOWcodeWOproduct String
    productType String
    LOWcodeWproduct String
    onTheGo Boolean "*"
    householdWaste Boolean "*"
    depositReturnSchemes List "*"
    completePackagingEndOfLifeRoutes List
    recyclability Boolean
    recyclabilityClaims List
    height Decimal
    heightDate Date
    width Decimal
    widthDate Date
    depth Decimal
    depthDate Date
    volume Decimal
    volumeDate Date
    weight Decimal "*"
    weightTolerance Decimal "*"
    weightToleranceType String "*"
    weightDate Date
    servingCapacity Integer
    servingCapacityDate Date
    partOfMultipack Boolean "*"
    certification Boolean
    certificationClaims List
    manufacturers List
    manufacturedCountry String
    updateDate Date "*"
    releaseDate Date
    discontinueDate Date
  }
  COMPLETE_PACKAGING }o..o{ CONTROLLED_LISTS : attributes
  COMPLETE_PACKAGING }O..O{ RELATIONSHIP_LISTS : attributes
  COMPLETE_PACKAGING }o..o{ MULTIPACK : multipack_constituents
  COMPONENTS }o..o{ MULTIPACK : multipack_constituents
  COMPLETE_PACKAGING }o..o{ LOADS : load_constituents
  MULTIPACK }o..o{ LOADS : load_constituents
  COMPONENTS }o..o{ LOADS : load_constituents
      CONTROLLED_LISTS {
      productType optional
      depositReturnScheme optional
    }
    RELATIONSHIP_LISTS {
      completePackagingEndOfLifeRoutes required
      recyclabilityClaims optional
      certificationClaims optional
      organisations optional
    }
```

## Template

Complete packaging should be provided as a separate csv file. The specification of this csv file is as follows:

[Complete Packaging Template](https://www.open3p.org/wp-content/uploads/2023/09/completePackaging20230922.csv){target=_blank}

## Example

=== "Wine box - JSON"

    ``` json linenums="1" hl_lines="3 4"
    [
        {
            "identifier": "TBC",
            "name": "Wine box",
            "description": "Sturdy and branded, our cardboard box is crafted to hold 12 bottles securely. Includes inlay for secure transport.",
            "externalIdentifiers": {
                "internalIdentifer": "85467889",
                "GTIN": "00123456789012"
                },
            "completePackagingConstituentsIdentifier": [
                {
                "materialConstituentsIdentifier": "TBC",
                "materialCombinationIdentifier": "9dad67b0-d5a2-4afb-9287-e712fd1ea3e6"
                },
                {
                "materialConstituentsIdentifier": "TBC",
                "materialCombinationIdentifier": "8f87c708-8a6b-4c9d-ae6e-af0393f84a12"
                }
                ],
            "LOWcodeWOproduct": "15 01 01",
            "productType": "cp-product-type-0001",
            "LOWcodeWproduct": "15 01 06",
            "onTheGo": false,
            "householdWaste": true,
            "completePackagingEndOfLifeRoutes": [
                "TBC"
            ],
            "recyclability": false,
            "recyclabilityClaims": [
                "TBC"
            ],
            "height": 382,
            "heightDate": "2024-01-31",
            "width": 388,
            "widthDate": "2024-01-31",
            "depth": 274,
            "depthDate": "2024-01-31",
            "volume": 40611184,
            "volumeDate": "2024-01-31",
            "weight": 450,
            "weightTolerance": 58,
            "weightToleranceType": "percentage",
            "weightDate": "2024-01-31",
            "servingCapacity": 12,
            "servingCapacityDate": "2024-01-31",
            "partOfMultipack": false,
            "certification": true,
            "certificationClaims": [
                "TBC"
            ],
            "manufacturers": ["GB-COH-10906273"],
            "manufacturedCountry": "826",
            "updateDate": "2024-01-31",
            "releaseDate": "2010-01-31",
            "discontinueDate": ""
        }
    ]
    ```
=== "Wine bottle - JSON"

    ``` json linenums="1" hl_lines="3 4"
    [
        {
            "identifier": "123f1eab-f674-4009-862a-7168cd5cf53f",
            "name": "Wine bottle",
            "description": "750ml Bordeaux wine bottle with cork and two labels: Classic design, recyclable glass, sealed with a cork for freshness. Two labels for branding and information.",
            "externalIdentifiers": {
                "gtin": "0123456789012",
                "sku": "5454632",
                "WineMS": "316456"
                },
            "completePackagingConstituentsIdentifier": [
                {
                "materialConstituentsIdentifier": "TBC",
                "materialCombinationIdentifier": "94108707-b914-43f3-bed5-93adbbd208c1"
                },
                {
                "materialConstituentsIdentifier": "TBC",
                "materialCombinationIdentifier": "4b99be14-c89e-4869-abb7-485240ea33c6"
                },
                {
                "materialConstituentsIdentifier": "TBC",
                "materialCombinationIdentifier": "3d77b280-690e-4ccb-84f5-584c4cbcea36"
                },
                {
                "materialConstituentsIdentifier": "TBC",
                "materialCombinationIdentifier": "4b50247a-b2d1-4438-ac8a-fb6768180136"
                }
                ],
            "productType": "cp-product-type-0001",
            "onTheGo": false,
            "householdWaste": true,
            "completePackagingEndOfLifeRoutes": [
                "TBC"
            ],
            "recyclability": true,
            "recyclabilityClaims": [
                "TBC"
            ],
            "height": 305,
            "heightDate": "2024-01-31",
            "width": 72.4,
            "widthDate": "2024-01-31",
            "depth": 72.5,
            "depthDate": "2024-01-31",
            "weight": 710,
            "weightTolerance": 6,
            "weightToleranceType": "percentage",
            "servingCapacity": 750,
            "partOfMultipack": true,
            "certification": true,
            "certificationClaims": [
                "1407ca7b-ebaf-472c-85c5-a7965a21f280"
            ],
            "manufacturers": ["GB-COH-10906273"],
            "manufacturedCountry": "826",
            "updateDate": "2024-01-31",
            "releaseDate": "2010-01-31",
            "discontinueDate": ""
        }
    ]
    ```
## Data flow

``` mermaid
flowchart LR
    subgraph materials[Materials]
        bm_example["example base materials"]
    end
        subgraph components[Components]
        co_cardboardBox[Cardboard box
        - 
        9dad67b0-d5a2-4afb-9287-e712fd1ea3e]
        co_tape[Tape
        - 
        8f87c708-8a6b-4c9d-ae6e-af0393f84a12]
        co_wineBottle["Wine bottle
        - 
        94108707-b914-43f3-bed5-93adbbd208c1"]
        co_cork["Cork
        - 
        4b99be14-c89e-4869-abb7-485240ea33c6"]
        co_backLabel["Back label
        - 
        3d77b280-690e-4ccb-84f5-584c4cbcea36"]
        co_frontLabel["Front label
        - 
        4b50247a-b2d1-4438-ac8a-fb6768180136"]
    end
    subgraph completePackages["`**Complete Packages**`"]
        cp_wineBox["`**Wine Box
        -
        complete pakages**`"]
        cp_wineBottle["`**Wine Bottle
        -
        123f1eab-f674-4009-862a-7168cd5cf53f**`"]
    end
    subgraph multipacks[Multipacks]
        mp_example[example multipacks]
    end
    materials --> components
    co_cardboardBox --> cp_wineBox
    co_tape --> cp_wineBox
    co_wineBottle --> cp_wineBottle
    co_cork --> cp_wineBottle
    co_backLabel --> cp_wineBottle
    co_frontLabel --> cp_wineBottle
    cp_wineBox -.-> multipacks
    cp_wineBottle -.-> multipacks
```

## Guide for how to take measurements

### Units

All measurements should be given using the metric system.

- Height: millimetre (mm)
- Width: millimetre (mm)
- Length: millimetre (mm)
- Volume: cubic metre (m3)
- Weight: grams (g)
- servingCapacity: grams (g)

Numbers should be entered with a decimal place, a space between the number, and the unit as specified above. Use the decimal / full stop / period character as a separator. For example: volume = 20.000 mm3. Do not exceed 3 decimal places.

**Important**: When converting between systems of measurement, perform the conversion first and then apply rounding. This will give more accuracy and consistency.

### Default Front of a complete packaging
As with taking and reporting measurements for components, we use the [GS1](https://www.gs1.org/){target=_blank} method for taking measurements. Now, with all the components put together to form the complete packaging, first find the default front, the the face with the largest area, where area is equal to the width times the height.

- The side with the maximum area then becomes the default front of that complete packaging.

### Measuring the height, width, and depth of a complete packaging
After the default front has been determined, it is possible to determine the height, width, and depth of the complete packaging. Please follow the measurement guidelines provided by [GS1](https://www.gs1.org/standards/gs1-package-and-product-measurement-standard/current-standard#4-Consumer-(end-user)-trade-items+4-3-Determining-the-height,-width-and-depth){target=_blank}


## Guide for complete packaging images
As with providing measurements, please first find the default front of the complete packaging. The image capturing process and naming convention is similar to [GS1](https://www.gs1.org/standards/gs1-product-image-specification-standard/current-standard#1-Introduction){target=_blank}. 
