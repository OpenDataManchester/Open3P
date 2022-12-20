# Complete Packaging

We can now use the unique components, to create a complete packaging. Each row refers to the complete package.

The specification of this csv file is as follows:

[complete_packaging.csv ](https://github.com/OpenDataManchester/PPP/blob/main/docs/7_Supporting_Files/7_1_3_Complete_Packaging_Template.csv){target=_blank}

|Column|Status|Format|Notes|
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
