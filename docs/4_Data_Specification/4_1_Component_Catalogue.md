# Component Catalogue

## Standard Spreadsheet Format

The spreadsheet format is the simplest way to provide information about recycling and waste sites (RWS).

The following table lists the column headings that should be used. When providing this information, you can either build your spreadsheet from scratch, or use the template provided.

[open3R_main.csv](https://github.com/OpenDataManchester/Open3R/blob/V2/docs/8_Supporting_Files/8_1_1_RWS_Main_Template.csv){target=_blank}


|Column|Status|Format|Notes|
|:-|:-|:-|:-|
|identifier|`required`|String|A globally unique identifier. See identifiers section for information on how to construct this identifier|
|name|`required`|String|The name of this component.|
|description|`recommended`|String|A brief description of this component.|
|tags|`recommended`|String|A list of identifiers that might be used to identify the component in other systems. For example: bar codes or global trade item number (gtin). To provide tags please follow this format. `tagName1: identifier1; tagName2: identifier2`|
|imageURL|`recommended`|URL|A URL that links to a picture of the component. Please see the guidelines below on how to capture the image and name the URL.|
|LOWcode|`recommended`|String|The list of waste code for **only** the component, by itself. LOW code is synonymous with European Waste Catelogue Code (EWC). For example: an empty bottle would have a LOWcode of `15 01 02`. Please use [Dsposal](https://dsposal.uk/browse/ewc) or [legislation.gov](https://www.legislation.gov.uk/uksi/2005/895/schedule/1/made) to find the LOWcode. **Note**: The LOWcode can based on its combination with other components and the actual product contained in the completePackaging. Be sure to only include the component LOWcode. If you cannot find the code or are uncertain please enter `Uncertain`.|
|height|`required`|String|The height of the component. Please see the guidelines below on how to properly measure and report the height.|
|heightDate|`required`|String|The date that the height was last verified/measured. Use the format `dd/mm/yyyy`.|
|width|`required`|String|The width of the component. Please see the guidelines below on how to properly measure and report the width.|
|widthDate|`required`|String|The date that the width was last verified/measured. Use the format `dd/mm/yyyy`.|
|depth|`required`|String|The depth of the component. Please see the guidelines below on how to properly measure and report the depth.|
|depthDate|`required`|String|The date that the depth was last verified/measured. Use the format `dd/mm/yyyy`.|
|volume|`required`|String|Using the height, width, and depth found using the measurement guidelines, calculate the component's volume using: `height x width x depth`. Report the volume as a string with mm3 and a space between the measurement. For example: the volume is `20 mm3`.|
|volumeDate|`required`|String|The date that the volume was last verified/measured. Use the format `dd/mm/yyyy`.|
|weight|`required`|String|The weight of the component. TBD|
|weightDate|`required`|String|The date that the weight was last verified/measured. Use the format `dd/mm/yyyy`.|
|thickness|`required`|String|The thickness of the component. TBD|
|thicknessDate|`required`|String|The date that the thickness was last verified/measured. Use the format `dd/mm/yyyy`.|
|format|`required`|String|What is the format or shape of the component? The entry should contain the format controlled list identifier for the component.|
|flexibility|`required`|String|Whether the component is considered flexible or rigid. The entry should be the flexibility controlled list identifier.|
|componentRecyclingDisruptors|`required`|String|What challenges the component has for recycling. The entry should be the componentRecyclingDisruptors controlled list identifier.|
|colour|`required`|String|TBD.|
|recycledContent|`required`|Percent|A percent of how much recycled content is included in the makeup of the component.|
|recycledContentEvidenceType|`required`|String|What evidence type supports the recycledContent claim. The entry should be the recycledContentEvidenceType controlled list identifier.|
|recycledContentEvidenceReference|`required`|String|An accompanying reference number associated with the recycledContentEvidenceType for the component.|
|recyclability|`recommended`|Boolean|Is the component recyclable?|
|recyclabilitySource|`required`|String|What source provided the recyclability claim? The entry should be the recyclabilitySource controlled list identifier.|
|recyclabilityDate|`required`|String|The date that the recyclability was provided/last updated. Use the format `dd/mm/yyyy`.|
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
- Thickness: micrometre (um)

Numbers should be entered with a decimal place, a space between the number, and the unit as specified above. Use the decimal / full stop / period character as a separator. For example: volume = 20.000 mm3. Do not exceed 3 decimal places.

**Important**: When converting between systems of measurement, perform the conversion first and then apply rounding. This will give more accuracy and consistency.

### Default Front of a component
Prior caputuring measurements, first determine the default front of the component, this is similar to[gs1](https://www.gs1.org/). In this standard, the default front is the face with the largest area, where area is equal to the width times the height.

**Important**: Determining of default front provides a consistent, repeatable process to find measurements for a given component.

Figure 1: An example for finding the default front of a component. The default front is the face of the with the largest area (A = width X height)
<image>

Some components have the same area, thus more than one possible front. These components can be presented both vertically and horizontally. If a component has more than one possible front, the highest side is considered to be the default front.

Figure 2: An example of when the area is the same for more than one face. The default front becomes the side with the maximum height.
<image>

**Note**: Calculating the area for a rectangular component is simple. However, for non-rectangular components (for example, components with a cylindrical or irregular form), the method to calculate the area is:
- First break the component into multiple sides. Then, for:
- a round component, do not use (=pi*r^2) to calculate the area. Instead, draw "two dimensional" rectangles around the round component's sides and then calculate the area for each side.

Figure 3: Example of a round component, breaking down the sides and drawing rectangles around them.
<image>

- any other shape component, draw a "two dimensional" rectangle around the sides of the component, and then calculate the area for each side.

Figure 4: Example of an irregular shaped component placed inside a rectangle to determine the area for a single side. 
<image>

- The side with the maximum area then becomes the default front of that component.

### Measuring the height, width, and depth of a component
After the default front has been determined, it is possible to determine the height, width, and depth of a component. 

1. For rectangular components: 
- Height: from the base to the top
- Width: from the left to the right
- Depth: from the front to the back
If there are two different measurements for the height, width, or depth, always report the maximum measurement.

Figure 5: Example of measuring the height, width, and depth for a rectangular component. 
<image> 

Figure 6: Example of reporting the maximum width, when there are two different size widths.
<image>

2. For irregular shaped components:
Similar to finding the default front of an irregularly shaped component, draw a "three dimensional" rectangle around the component.
- Height: from the base to the top
- Width: from the left to the right
- Depth: from the front to the back
<image>(include example with hanger)

3. For unformed, flexible components:
Take the measurements as if the component was fully formed and filled.
- Height:
- Width:
- Depth: 
<image>

4. For standing components:
- Height: from the flat surface to the top most point
- Width: from the left-most point to the right-most point
- Depth: from the default front to the farthest opposite surface
<image>

5. For components with leaning or irregular verticlas:
- Height: from the flat surface to the top most point (parallel to the vertex)
- Width: from the left most point to the right most point 
- Depth: from the default front to the farthest opposite surface
<image>

6. For components that are cylindrical:
For cylindrical items two dimensions will be nominally equal. Which dimensions are equal is
determined by the result of determination of the default front.
<image>

### Measuring the thickness of a component
provide the measurement for the thickest point

### Measuring the volume and weight of a component



(https://www.gs1.org/standards/gs1-package-and-product-measurement-standard/current-standard#4-Consumer-(End-user)-trade-items+4-2-Determining-the-default-front-of-an-item)

## Guide for component images
As with providing measurements, please first find the default front of the component. The image capturing process and naming convention is similar to [gs1](https://www.gs1.org/standards/gs1-product-image-specification-standard/current-standard#1-Introduction). As with measurements, we altered the gs1 standard for capturing the component.

### Type of Image
For the purposes of this standard, we define the differences between photographic and rendered images. Note: both types are accepted but the naming convention will differ based on image type so that images have unique names and do not having naming conflicts.
- **Photographic image**: the result of the electronic or chemical capture of a likeness of a physical object with the use of a camera.
- **Rendered image**: the result of the creation of a digital likeness of a physical object with the use of a computer and software.

### Image Recommendations
- Provide coloured images. However, do not provide colour casts. Colour should be as rich, vibrant and eye-catching as possible
- Contrast and exposure should be balanced; avoid high contrast effects and "blown-out" highlights
- Images should not be overly sharpened
- Components should be centred in Margins to cover 95% on the canvas.
- Graphic rendering of a component should be realistic.
- Do not provide layers, guides or rulers in the images.
- Background layer should be white (RGB 255,255,255).
- Remove signatures, "finger printing" or visible watermarks. No compression artifacts. No interpolation ("resizing up").

### File size
- 900x900 to 2400x2400 pixels

### Component faces
After determining the default front, the possible faces, in relation to the default front, are:
1. Default Front
2. Left
3. Top
7. Back
8. Right
9. Bottom

### Naming convention for URL
Please follow this naming convention: 
- component identifier
- underscore `_`
- type of image (`photographic` or `rendered`)
- underscore `_`
- component face (`1`: Default front, `2`: Left, `3`: Top, `7`: Back, `8`: Right, `9`: Bottom)
- orientation (`C`: Centre, `L`: left, `R`: right, `N`: No plunge angle)

**Example**: An image for a component that is rendered with a default front facing image and centred orientation. `identifier123_rendered_1C.jpg`


