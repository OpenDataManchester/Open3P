# Complete Packaging

We can now use the unique components, to create a complete packaging.

The specification of this csv file is as follows:

[complete_packaging.csv ](https://github.com/OpenDataManchester/PPP/blob/main/docs/8_Supporting_Files/8_1_4_Complete_Packaging_Template.csv){target=_blank}

|Column|Status|Format|Notes|
|:-|:-|:-|:-|
|identifier|`required`|String|A globally unique identifier. See identifiers section for information on how to construct this identifier|
|name|`required`|String|The name of this complete packaging.|
|description|`recommended`|String|A brief description of this complete packaging.|
|tags|`recommended`|String|A list of identifiers that might be used to identify the complete packaging in other systems. For example: bar codes or global trade item number (gtin). To provide tags please follow this format. `tagName1: identifier1; tagName2: identifier2`|
|imageURL|`recommended`|URL|A URL that links to a picture of the complete packaging. Please see the guidelines below on how to capture the image and name the URL.|
|independentComponent|`required`|String|The component identifier from the unique component that is independently created. There must be an equivalent record in the `unique_Component` data. If all the components were created together use `NA`. If there are multiple components, separate with a semicolon. `e.g. component1; component2`|
|previouslyAssembledComponent|`required`|String|The component identifier from the unique component that was combined with other components when created. There must be an equivalent record in the `unique_Component` data. If all the components were independently created use `NA`. If there are multiple components, separate with a semicolon. `e.g. component1; component2`|
|allComponent|`required`|String|All of the component identifiers from the unique component that are combined to create the complete packaging. There must be an equivalent record in the `unique_Component` data for all component identifiers. If there are multiple components, separate with a semicolon. `e.g. component1; component2`|
|LOWcodeWOproduct|`required`|String|The list of waste code for **only** the complete packaging, by itself (excluding the product). LOW code is synonymous with European Waste Catelogue Code (EWC). For example: an empty bottle would have a LOWcode of `15 01 02`. Please use [Dsposal](https://dsposal.uk/browse/ewc) or [legislation.gov](https://www.legislation.gov.uk/uksi/2005/895/schedule/1/made) to find the LOWcode. **Note**: The LOWcode can based on its combination with other components and the actual product contained in the complete packaging. Be sure to only include the complete packaging LOWcode and not the complete packaging with the product. If you cannot find the code or are uncertain please enter `Uncertain`.|
|productType|`required`|String|Information about the product contained in the complete packaging. The entry here should be drawn from the product type controlled list.|
|LOWcodeWproduct|`required`|String|The list of waste code for **everything** in the complete packaging. LOW code is synonymous with European Waste Catelogue Code (EWC). For example: an empty bottle would have a LOWcode of `15 01 02`. Please use [Dsposal](https://dsposal.uk/browse/ewc) or [legislation.gov](https://www.legislation.gov.uk/uksi/2005/895/schedule/1/made) to find the LOWcode. **Note**: The LOWcode can based on its combination with other components and the actual product contained in the complete packaging. Be sure to include the complete packaging LOWcode with the product. If you cannot find the code or are uncertain please enter `Uncertain`.|
|onTheGo|`required`|Boolean|Is the complete packaging often classed as packaging that will end up in street bins?|
|householdWaste|`required`|Boolean|Is the complete packaging often classed as packaging that will end up in kerbside collections?|
|depositReturnScheme|`required`|String| Which countries in the United Kingdom support a [deposit return scheme](https://www.gov.uk/government/consultations/introduction-of-a-deposit-return-scheme-in-england-wales-and-northern-ireland) for this particular complete packaging? The entry here should be drawn from the deposit return scheme controlled list.|
|recyclingDisruptors|`required`|String|What challenges the complete packaging has for recycling. The entry should be the recycling disruptors controlled list identifier.|
|recyclability|`recommended`|Boolean|Is the complete packaging recyclable?|
|recyclabilitySource|`required`|String|What source provided the recyclability claim? The entry should be the recyclabilitySource controlled list identifier.|
|recyclabilityDate|`required`|String|The date that the recyclability was provided/last updated. Use the format `dd/mm/yyyy`.|
|height|`required`|String|The height of the complete packaging. Please see the guidelines below on how to properly measure and report the height.|
|heightDate|`required`|String|The date that the height was last verified/measured. Use the format `dd/mm/yyyy`.|
|width|`required`|String|The width of the complete packaging. Please see the guidelines below on how to properly measure and report the width.|
|widthDate|`required`|String|The date that the width was last verified/measured. Use the format `dd/mm/yyyy`.|
|depth|`required`|String|The depth of the complete packaging. Please see the guidelines below on how to properly measure and report the depth.|
|depthDate|`required`|String|The date that the depth was last verified/measured. Use the format `dd/mm/yyyy`.|
|volume|`required`|String|Using the height, width, and depth found using the measurement guidelines, calculate the complete packaging's volume using: `height x width x depth`. Report the volume as a string with mm3 and a space between the measurement. For example: the volume is `20 mm3`.|
|volumeDate|`required`|String|The date that the volume was last verified/measured. Use the format `dd/mm/yyyy`.|
|weight|`required`|String|The weight of the complete packaging. TBD|
|weightDate|`required`|String|The date that the weight was last verified/measured. Use the format `dd/mm/yyyy`.|
|servingCapacity|`required`|String|The serving capacity of the complete packaging - how much of a product that can be contained in the complete packaging|
|servingCapacityDate|`required`|String|The date that the serving capacity was last verified/measured. Use the format `dd/mm/yyyy`.|
|partOfMultipack|`required`|Boolean|Is the complete packaging part of a multipack?|
|uploadDate|`required`|String|The date that the component was provided/last updated. Use the format `dd/mm/yyyy`.|
|releaseDate|`required`|String|The date that the component will be available to use. Use the format `dd/mm/yyyy`.|
|discontinuedDate|`required`|String|The date that the component will no longer be available to use. Use the format `dd/mm/yyyy`.|

## Guide for how to take measurements

### Units

All measurements should be given using the metric system.

- Height: millimetre (mm)
- Width: millimetre (mm)
- Length: millimetre (mm)
- Volume: cubic millimetre (mm3)
- Weight: grams (g)
- servingCapacity: grams (g)

Numbers should be entered with a decimal place, a space between the number, and the unit as specified above. Use the decimal / full stop / period character as a separator. For example: volume = 20.000 mm3. Do not exceed 3 decimal places.

**Important**: When converting between systems of measurement, perform the conversion first and then apply rounding. This will give more accuracy and consistency.

### Default Front of a complete packaging
Prior caputuring measurements, first determine the default front of the complete packaging, this is similar to [gs1](https://www.gs1.org/). In this standard, the default front is the face with the largest area, where area is equal to the width times the height.

**Important**: Determining of default front provides a consistent, repeatable process to find measurements for a given complete packaging.

Figure 1: An example for finding the default front of a complete packaging. The default front is the face of the with the largest area (A = width X height)
<image>

Some complete packaging have the same area, thus more than one possible front. These complete packaging can be presented both vertically and horizontally. If a complete packaging has more than one possible front, the highest side is considered to be the default front.

Figure 2: An example of when the area is the same for more than one face. The default front becomes the side with the maximum height.
<image>

**Note**: Calculating the area for a rectangular complete packaging is simple. However, for non-rectangular complete packaging (for example, complete packaging with a cylindrical or irregular form), the method to calculate the area is:
- First break the complete packaging into multiple sides. Then, for:
- a round complete packaging, do not use (=pi*r^2) to calculate the area. Instead, draw "two dimensional" rectangles around the round complete packaging's sides and then calculate the area for each side.

Figure 3: Example of a round complete packaging, breaking down the sides and drawing rectangles around them.
<image>

- any other shape complete packaging, draw a "two dimensional" rectangle around the sides of the complete packaging, and then calculate the area for each side.

Figure 4: Example of an irregular shaped complete packaging placed inside a rectangle to determine the area for a single side. 
<image>

- The side with the maximum area then becomes the default front of that complete packaging.

### Measuring the height, width, and depth of a complete packaging
After the default front has been determined, it is possible to determine the height, width, and depth of the complete packaging. 

1. For rectangular complete packaging: 
- Height: from the base to the top
- Width: from the left to the right
- Depth: from the front to the back
If there are two different measurements for the height, width, or depth, always report the maximum measurement.

Figure 5: Example of measuring the height, width, and depth for a rectangular complete packaging. 
<image> 

Figure 6: Example of reporting the maximum width, when there are two different size widths.
<image>

2. For irregular shaped complete packaging:
Similar to finding the default front of an irregularly shaped complete packaging, draw a "three dimensional" rectangle around the complete packaging.
- Height: from the base to the top
- Width: from the left to the right
- Depth: from the front to the back
<image>(include example with hanger)

3. For unformed, flexible complete packaging:
Take the measurements as if the complete packaging was fully formed and filled.
- Height:
- Width:
- Depth: 
<image>

4. For standing complete packaging:
- Height: from the flat surface to the top most point
- Width: from the left-most point to the right-most point
- Depth: from the default front to the farthest opposite surface
<image>

5. For complete packaging with leaning or irregular verticlas:
- Height: from the flat surface to the top most point (parallel to the vertex)
- Width: from the left most point to the right most point 
- Depth: from the default front to the farthest opposite surface
<image>

6. For complete packaging that are cylindrical:
For cylindrical items two dimensions will be nominally equal. Which dimensions are equal is determined by the result of determination of the default front.
<image>




(https://www.gs1.org/standards/gs1-package-and-product-measurement-standard/current-standard#4-Consumer-(End-user)-trade-items+4-2-Determining-the-default-front-of-an-item)

## Guide for complete packaging images
As with providing measurements, please first find the default front of the complete packaging. The image capturing process and naming convention is similar to [gs1](https://www.gs1.org/standards/gs1-product-image-specification-standard/current-standard#1-Introduction). 

### Type of Image
For the purposes of this standard, we define the differences between photographic and rendered images. Note: both types are accepted but the naming convention will differ based on image type so that images have unique names and do not have naming conflicts.
- **Photographic image**: the result of the electronic or chemical capture of a likeness of a physical object with the use of a camera.
- **Rendered image**: the result of the creation of a digital likeness of a physical object with the use of a computer and software.

### Image Recommendations
- Provide coloured images. However, do not provide colour casts. Colour should be as rich, vibrant and eye-catching as possible
- Contrast and exposure should be balanced; avoid high contrast effects and "blown-out" highlights
- Images should not be overly sharpened
- Complete Packaging should be centred in Margins to cover 95% on the canvas.
- Graphic rendering of a complete packaging should be realistic.
- Do not provide layers, guides or rulers in the images.
- Background layer should be white (RGB 255,255,255).
- Remove signatures, "finger printing" or visible watermarks. No compression artifacts. No interpolation ("resizing up").

### File size
- 900x900 to 2400x2400 pixels

### Complete Packaging faces
After determining the default front, the possible faces, in relation to the default front, are:
1. Default Front
2. Left
3. Top
7. Back
8. Right
9. Bottom

### Naming convention for URL
Please follow this naming convention: 
- complete packaging identifier
- underscore `_`
- type of image (`photographic` or `rendered`)
- underscore `_`
- component face (`1`: Default front, `2`: Left, `3`: Top, `7`: Back, `8`: Right, `9`: Bottom)
- orientation (`C`: Centre, `L`: left, `R`: right, `N`: No plunge angle)

**Example**: An image for a complete packaging that is rendered with a default front facing image and centred orientation. `123_rendered_1C.jpg`
