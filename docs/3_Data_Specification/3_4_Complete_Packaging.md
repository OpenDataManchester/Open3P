---
title: Complete Packaging
---

# Complete Packaging

The complete packaging schema contains information regarding the complete packages that are used to create loads. These maybe created from a single component or a combination of components from the component catalogue schema.

## Table
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`required`|String|A globally unique identifier. See identifiers section for information on how to construct this identifier|
|name|`recommended`|String|The name of this complete packaging.|
|description|`recommended`|String|A brief description of this complete packaging.|
|tags|`recommended`|Dictionary|A dictionary of identifiers that might be used to identify the complete packaging in other systems. For example: bar codes or global trade item number (gtin). To provide tags please follow this format. `{'tagName1': 'identifier1', 'tagName2': 'identifier2'}`|
|imageURL|`recommended`|URL|A URL that links to a picture of the complete packaging. Please see the guidelines below on how to capture the image and name the URL.|
|componentItems|`required`|String|The component catalogue identifiers used to create the complete packaging. There must be an equivalent record in the `component_catalogue` data.|
|LOWcodeWOproduct|`recommended`|String|The list of waste code for **only** the complete packaging, by itself (excluding the product). LOW code is synonymous with European Waste Catelogue Code (EWC). For example: an empty bottle would have a LOWcode of `15 01 02`. Please use [Dsposal](https://dsposal.uk/browse/ewc){target=_blank} or [legislation.gov](https://www.legislation.gov.uk/uksi/2005/895/schedule/1/made){target=_blank} to find the LOWcode. **Note**: The LOWcode can based on its combination with other components and the actual product contained in the complete packaging. Be sure to only include the complete packaging LOWcode and not the complete packaging with the product. If you cannot find the code or are uncertain please enter `Uncertain`.|
|productType|`recommended`|String|Information about the product contained in the complete packaging. The entry here should be drawn from the product type controlled list.|
|componentContactWithProduct|`required`|String|What components (if any) come into direct contact with the product before purchased by a consumer? If none of the components come into contact with the product use `NA`. If there are multiple components, separate with a comma. `e.g. 'component1', 'component2'`|
|LOWcodeWproduct|`recommended`|String|The list of waste code for **everything** in the complete packaging. LOW code is synonymous with European Waste Catelogue Code (EWC). For example: an empty bottle would have a LOWcode of `15 01 02`. Please use [Dsposal](https://dsposal.uk/browse/ewc){target=_blank} or [legislation.gov](https://www.legislation.gov.uk/uksi/2005/895/schedule/1/made){target=_blank} to find the LOWcode. **Note**: The LOWcode can based on its combination with other components and the actual product contained in the complete packaging. Be sure to include the complete packaging LOWcode with the product. If you cannot find the code or are uncertain please enter `Uncertain`.|
|onTheGo|`required`|Boolean|Is the complete packaging often classed as packaging that will end up in street bins?|
|householdWaste|`required`|Boolean|Is the complete packaging often classed as packaging that will end up in kerbside collections?|
|depositReturnScheme|`required`|String| Which countries in the United Kingdom support a [deposit return scheme](https://www.gov.uk/government/consultations/introduction-of-a-deposit-return-scheme-in-england-wales-and-northern-ireland){target=_blank} for this particular complete packaging? The entry here should be drawn from the deposit return scheme controlled list.|
|recyclingDisruptors|`recommended`|String|What challenges the complete packaging has for recycling. The entry should be the recycling disruptors controlled list identifier.|
|recyclability|`recommended`|Boolean|Is the complete packaging recyclable (as determined by a reputable source)?|
|recyclabilitySource|`recommended`|String|What source provided the recyclability claim? The entry should be the recyclabilitySource controlled list identifier.|
|recyclabilityDate|`recommended`|String|The date that the recyclability was provided/last updated. Use the format `dd/mm/yyyy`.|
|height|`recommended`|Numeric|The height of the complete packaging. Please see the guidelines below on how to properly measure and report the height.|
|heightDate|`recommended`|String|The date that the height was last verified/measured. Use the format `dd/mm/yyyy`.|
|width|`recommended`|Numeric|The width of the complete packaging. Please see the guidelines below on how to properly measure and report the width.|
|widthDate|`recommended`|String|The date that the width was last verified/measured. Use the format `dd/mm/yyyy`.|
|depth|`recommended`|Numeric|The depth of the complete packaging. Please see the guidelines below on how to properly measure and report the depth.|
|depthDate|`recommended`|String|The date that the depth was last verified/measured. Use the format `dd/mm/yyyy`.|
|volume|`recommended`|Numeric|Using the height, width, and depth found using the measurement guidelines, calculate the complete packaging's volume using: `height x width x depth`.|
|volumeDate|`recommended`|String|The date that the volume was last verified/measured. Use the format `dd/mm/yyyy`.|
|weight|`required`|Numeric|The weight of the complete packaging.|
|weightTolerance|`required`|Numeric|The threshold of weight that complete packaging can vary by. This should be given in grams.|
|weightDate|`recommended`|String|The date that the weight was last verified/measured. Use the format `dd/mm/yyyy`.|
|servingCapacity|`recommended`|Numeric|The serving capacity of the complete packaging - how much of a product that can be contained in the complete packaging.|
|servingCapacityDate|`recommended`|String|The date that the serving capacity was last verified/measured. Use the format `dd/mm/yyyy`.|
|partOfMultipack|`required`|Boolean|Is the complete packaging part of a multipack? Answer as: `1` for yes and `0` for no.|
|updateDate|`required`|String|The date that the complete packaging was provided/last updated. Use the format `dd/mm/yyyy`.|
|releaseDate|`recommended`|String|The date that the complete packaging will be available to use. Use the format `dd/mm/yyyy`.|
|discontinueDate|`recommended`|String|The date that the complete packaging will no longer be available to use. Use the format `dd/mm/yyyy`.|

## Diagram

<figure markdown>
![Schema](../img/complete-packaging-v1.0.0-22-12-20.png){ width="800" }
  <figcaption>Data schema</figcaption>
</figure>

## Template

Complete packaging should be provided as a separate csv file, in tidy format. This means that each row of the csv file should be one complete package of a load. An example is provided.

The specification of this csv file is as follows:

[complete_packaging.csv ](https://github.com/OpenDataManchester/PPP/blob/main/docs/7_Supporting_Files/7_1_3_Complete_Packaging_Template.csv){target=_blank}

## Example

=== "JSON"

    ``` json linenums="1"
    {
      "identifier": "C29B4703-121C-7552-D905-FD5AB263D611",
      "name": "2022 P06 2 Star Summer CHL Salad And Dips Guacamole Dip",
      "description": "A clear pot, film and lid in a decorative sleeve packed into an outercase.",
      "tags": {
          "GTIN":"00123456789012"
          },
      "imageURL": [
          "https://dsposal-my.sharepoint.com/:i:/g/personal/tom_yourdsposal_uk/Eblhs6hbkTFAo6SNdYh1ew8BfRwTFna21RyzaKJSq6xX9g?e=0BJKsf",
          "https://dsposal-my.sharepoint.com/:i:/g/personal/tom_yourdsposal_uk/ERs2KgXOTh1Ep6fqci0wqBIBVjOCe4uLJMrySoLm5P3Stg?e=C07ga9",
          "https://dsposal-my.sharepoint.com/:i:/g/personal/tom_yourdsposal_uk/ETQTTA8p1Y5Aj-eIThf6M4wBdunvvSVdVoV0bFqK6Nyfhw?e=DKRcHq"

      ],
      "componentItems": [
          "278EFE8A-720A-06C1-A411-CB94878AD3E2",
          "4CF8CE85-BA1A-BACB-670E-FAAB71D97D95",
          "661C7790-94D1-147D-7BF4-D518EAF5FA32",
          "7AA5DDF9-0FE1-110C-26C0-ECED9D05F6F1"
          ],
      "LOWcodeWOproduct": "15 01 06",
      "productType": {
          "identifier":"complete-packaging-product-type-0001",
          "category":"food",
          "detailed":""
          },
      "componentContactWithProduct": [
          "278EFE8A-720A-06C1-A411-CB94878AD3E2",
          "4CF8CE85-BA1A-BACB-670E-FAAB71D97D95"
          ],
      "LOWcodeWproduct": "20 01 08",
      "onTheGo": "FALSE",
      "householdWaste": "TRUE",
      "depositReturnScheme": {
          "identifier":"complete-packaging-drs-0005",
          "name":"none",
          "description":""
          },
      "recyclingDisruptors": "",
      "recyclability": 0,
      "recyclabilitySource": {
          "identifier":"complete-packaging-recyclability-source-0001",
          "category":"OPRL",
          "detailed":""
          },
      "recyclabilityDate": "01/08/2022",
      "height": 51.5,
      "heightDate": "01/08/2022",
      "width": 104,
      "widthDate": "01/08/2022",
      "depth": 104,
      "depthDate": "01/08/2022",
      "volume": 245,
      "volumeDate": "01/08/2022",
      "weight": 16.92,
      "weightTolerance": 0.74,
      "weightDate": "01/08/2022",
      "servingCapacity": 4,
      "servingCapacityDate": "01/08/2022",
      "partOfMultipack": "FALSE",
      "updateDate": "01/08/2022",
      "releaseDate": "01/08/2022",
      "discontinueDate": ""
    }
    ```

=== "CSV"

    [Coming soon](https://opendatamanchester.org.uk)

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
