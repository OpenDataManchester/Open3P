---
title: Components
description: Components are the individaul items of packaging made from materials in Open 3P.
---

# Components

The components schema contains information regarding the individual components that are used to create complete packages. These maybe created from a single material or a combination of materials from the materials schema.

## Table
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`mandatory`|UUID|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|name|`optional`|String|The name of this component.|
|description|`optional`|String|A brief description of this component.|
|externalIdentifiers|`optional`|Dictionary|A dictionary of identifiers that might be used to identify the component in other systems. For example: manufacturer's own internal identifier, bar codes or global trade item number (gtin). To provide external identifiers please follow this format. `{'externalIdentifierName1': 'identifier1', 'externalIdentifierName2': 'identifier2'}`|
|imageURLs|`optional`|List|A list of URLs that links to a picture of the component. Please see the guidelines below on how to capture the image and name the URL.|
|LOWcode|`optional`|String|The list of waste code for **only** the component, by itself. LOW code is synonymous with European Waste Catalogue Code (EWC). For example: an empty bottle would have a LOWcode of `15 01 02`. Please use [Dsposal](https://dsposal.uk/browse/ewc) or [legislation.gov](https://www.legislation.gov.uk/uksi/2005/895/schedule/1/made) to find the LOWcode. **Note**: The LOWcode can based on its combination with other components and the actual product contained in the completePackaging. Be sure to only include the component LOWcode. If you cannot find the code or are uncertain please enter `Uncertain`.|
|componentConstituents|`mandatory`|List|The information regarding the consituents that are combined to create this component. The entries should be from the [Component Constituents Relationship List](../6_Relationship_Lists/6_002_Component_Constituents.md) identifier.|
|height|`optional`|Decimal|The height of the component. Please see the guidelines below on how to properly measure and report the height.|
|heightDate|`optional`|Date|The date that the height was last verified/measured. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|
|width|`optional`|Decimal|The width of the component. Please see the guidelines below on how to properly measure and report the width.|
|widthDate|`optional`|Date|The date that the width was last verified/measured. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|
|depth|`optional`|Decimal|The depth of the component. Please see the guidelines below on how to properly measure and report the depth.|
|depthDate|`optional`|Date|The date that the depth was last verified/measured. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|
|volume|`optional`|Decimal|The amount of space the component takes up. Note: this is related to the size of the component and is different to capacity. Using the height, width, and depth found using the measurement guidelines, calculate the component’s volume using: `height x width x depth`.|
|volumeDate|`optional`|Date|The date that the volume was last verified/measured. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|
|weight|`mandatory`|Decimal|The weight of the component.|
|weightTolerance|`mandatory`|Decimal|The threshold of weight that components can vary by. This is given as +/- value.|
|weightToleranceType|`mandatory`|String|Either `grams` or `percentage` based on the value provided in `weightTolerance`|
|weightDate|`optional`|Date|The date that the weight was last verified/measured. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|
|shape|`optional`|String|What is the shape of the component? The entry should contain the [shape controlled list](../5_Controlled_Lists/5_006_Shape.md) identifier for the component.|
|function|`optional`|String|What is the function of the component? The entry should contain the [function controlled list](../5_Controlled_Lists/5_004_Function.md) identifier for the component.|
|flexibility|`optional`|String|Whether the component is considered flexible or rigid. The entry should be the [flexibility controlled list](../5_Controlled_Lists/5_007_Flexibility.md) identifier.|
|branding|`mandatory`|Boolean|Does the component contain your own brand (logo, trademark, or any distinctive mark)? Answer as: `TRUE` for yes and `FALSE` for no.|
|componentEndOfLifeRoutes|`optional`|List|The information regarding this component's proposed end of life routes. The entries should be the [component end of life routes](../6_Relationship_Lists/6_007_Component_End_of_Life_Routes.md) identifiers.|
|colour|`optional`|String|The actual colour of the component at point of production using CMYK (Cyan-Magenta-Yellow-blacK) values. The format is specified according to cmyk(C%, M%, Y%, K%), where C, M, Y, and K are the percent values for the cyan, magenta, yellow, and black values of the color. For example: black is `cmyk(0%,0%,0%,100%)`. If there are multiple colours input `decorative`.|
|opacity|`optional`|String|The transparency of the colours. The entry should be the [opacity controlled list](../5_Controlled_Lists/5_009_Opacity.md) identifier.|
|loaned|`mandatory`|Boolean|Is the component hired or loaned out as reusable packaging? Answer as: `TRUE` for yes and `FALSE` for no.|
|reuseSystems|`optional`|List|The system(s) that facilitates the reuse of the component  `e.g., Loop`. The entries should be the [reuse system controlled list](../5_Controlled_Lists/5_010_Reuse_System.md) identifier(s).|
|partOfMultipack|`mandatory`|Boolean|Is the component part of a multipack? Answer as: `TRUE` for yes and `FALSE` for no.|
|recycledContent|`optional`|Decimal|Positive decimal only, maximum value is 100.00. Value should equated to a percentage (e.g. 30 = 30%) The minimum allowable percent of how much recycled content is included in the makeup of the component. It is ‘required’ for plastic packaging where for the purposes of this standard we refer to [UK's HM Revenue & Customs](https://www.gov.uk/guidance/work-out-which-packaging-is-subject-to-plastic-packaging-tax){target=_blank} definition of recycled content. "Recycled plastic is plastic that has been reprocessed from recovered material by using a chemical or manufacturing process. This is so it can be used either for its original purpose or for other purposes. This does not include organic recycling. Recovered material is pre-consumer plastic or post-consumer plastic that both: a) is no longer suitable to be used in the process from which it was generated and would otherwise have been used for energy recovery (for example, by incineration) or disposed of as waste (for example, by being sent to landfill); b) has been collected and recovered for use as a material input for a recycling or manufacturing process, instead of new primary material"|
|recycledContentClaims|`optional`|List|The information regarding the recycled contents. The entries should be the [recycled content claims relationship list](../6_Relationship_Lists/6_009_Recycled_Content_Claims.md) indentifiers.|
|recyclability|`optional`|Boolean|Is the component recyclable (as determined by a reputable source)? Answer as: `TRUE` for yes and `FALSE` for no.|
|recyclabilityClaims|`optional`|List|The information regarding this recyclability claims. The entries should be the [recyclability claims relationship list](../6_Relationship_Lists/6_006_Recyclability_Claims.md) identifiers.|
|certification|`optional`|Boolean|Does the component have a certificate (e.g. FSC, REACH, FSA etc.)? Answer as: `TRUE` for yes and `FALSE` for no.|
|certificationClaims|`optional`|List|The information regarding the certifications. The entries should be the [certification claims relationship list](../6_Relationship_Lists/6_005_Certification_Claims.md) identifiers.|
|manufacturers|`optional`|List|The information regarding the manufacturer(s). The entries should be the [Organisations Relationship List](../6_Relationship_Lists/6_010_Organisations.md) identifiers.|
|manufacturedCountry|`optional`|String|The country the component was manufactured in. Use the country numeric [ISO codes](https://www.iso.org/obp/ui/#search){target=_blank} as described in the [ISO 3166 international standard](https://www.iso.org/iso-3166-country-codes.html){target=_blank}.|
|updateDate|`mandatory`|Date|The date that the component was provided/last updated. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|
|releaseDate|`optional`|Date|The date that the component will be available to use. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|
|discontinueDate|`optional`|Date|The date that the component will no longer be available to use. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|

## Diagram

``` mermaid
erDiagram
MATERIALS }o--o{ COMPONENTS : component_constituents
  COMPONENTS {
    identifier UUID "*"
    name String
    description String
    externalIdentifiers Dictionary
    imageURLs List
    LOWcode String
    componentConstituents List "*"
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
    shape String
    function String
    flexibility String
    branding Boolean "*"
    componentEndOfLifeRoutes List
    colour String
    opacity String
    loaned Boolean "*"
    reuseSystems List
    manufacturers List
    manufacturedCountry String
    recycledContent Decimal
    recycledContentClaims List
    recyclability Boolean
    recyclabilityClaims List
    partOfMultipack Boolean "*"
    certification Boolean
    certificationClaims List
    updateDate Date "*"
    releaseDate Date
    discontinueDate Date
  }
  COMPONENTS }o..o{ CONTROLLED_LISTS : attributes
  COMPONENTS }o..o{ RELATIONSHIP_LISTS : attributes
  COMPONENTS }o--o{ COMPLETE_PACKAGING : complete_packaging_constituents
  COMPONENTS }o..o{ MULTIPACK : multipack_constituents
  MULTIPACK }o..o{ LOADS : load_constituents
  COMPLETE_PACKAGING }o..o{ MULTIPACK : multipack_constituents
  COMPLETE_PACKAGING }o..o{ LOADS : load_constituents
  COMPONENTS }o..o{ LOADS : load_constituents
    CONTROLLED_LISTS {
    shape optional
    function optional
    flexibility optional
    opacity optional
    reuseSystem optional
  }
  RELATIONSHIP_LISTS {
    componentEndOfLifeRoutes optional
    recycledContentClaims optional
    recyclabilityClaims optional
    certificationClaims optional
    organisations optional
  }
```

Components should be provided as a separate csv file. The specification of this csv file is as follows:

[Components Template](https://www.open3p.org/wp-content/uploads/2023/09/components20230922.csv){target=_blank}

## Example

=== "Cardboard box - JSON"

    ``` json linenums="1"  hl_lines="3 4"
    [
        {
            "identifier": "9dad67b0-d5a2-4afb-9287-e712fd1ea3e6",
            "name": "Cardboard box",
            "description": "54cm x 38cm x 38cm 0204 style cardboard box: Sturdy and spacious for shipping or storage. All flaps meet for easy sealing. Versatile packaging solution for various items.",
            "componentConstituents": [
                {
                "materialConstituentsIdentifier": "6d856739-3893-4321-84b9-738a4ef1c830",
                "materialCombinationIdentifier": "16f41cca-1a77-4e31-8b0f-2723f752317b"
                }
            ],
            "height": 380,
            "width": 540,
            "depth": 380,
            "weight": 600,
            "weightTolerance": 35,
            "weightToleranceType": "grams",
            "shape": "c-shape-0004",
            "function": "function-0048",
            "flexibility": "c-flexibility-0002",
            "branding": false,
            "componentEndOfLifeRoutes": [
                "671ee5cc-a402-48a5-ba56-1f4d3840aef0"
            ],
            "colour": "cmyk(0%,14%,33%,18%)",
            "opacity": "c-opacity-0001",
            "loaned": false,
            "partOfMultipack": false,
            "recycledContent": 30,
            "recycledContentClaims": [
                "81ac4ec3-e097-4092-9c8f-4ef717d3740c"
            ],
            "recyclability": true,
            "recyclabilityClaims": [
                "6af9c69a-6ec1-42dd-a8da-54bab8165e44"
            ],
            "certification": false,
            "manufacturers": ["GB-COH-10906273"],
            "manufacturedCountry": "826",
            "updateDate": "2024-01-25",
            "releaseDate": "2011-01-01"
        }
    ]
    ```
=== "Wine bottle - JSON"

    ``` json linenums="1"  hl_lines="3 4"
    [
        {
            "identifier": "94108707-b914-43f3-bed5-93adbbd208c1",
            "name": "Wine bottle",
            "description": "Introducing our 750ml Bordeaux Bottle, a sophisticated and eco-conscious choice for wine packaging. Crafted with a commitment to sustainability, this bottle embodies the perfect blend of elegance and environmental responsibility.",
            "externalIdentifiers": {
                "gtin": "70123456 789012",
                "internal id": "0-recycle-green-750-bordeaux",
                "sku": "8855-bb-g"
            },
            "imageURLs" : ["https://dsposal.uk/media/35604/52419bc2-317f-4815-b39c-f90a20cb7a7a.jpg"],
            "componentConstituents": [
            {
              "materialConstituentsIdentifier": "70023f95-2d0f-4e47-ab6e-0ce51d50e55d",
              "materialCombinationIdentifier": "b050ab75-4bcb-4c7f-b8f5-8a1f9e5ba7d3"
            }
            ],
            "height": 305,
            "heightDate": "2015-06-16",
            "width": 72.4,
            "widthDate": "2015-06-16",
            "depth": 72.5,
            "depthDate": "2015-06-16",
            "weight": 700,
            "weightTolerance": 6,
            "weightToleranceType": "percent",
            "function": "function-0005",
            "flexibility": "c-flexibility-0002",
            "branding": false,
            "componentEndOfLifeRoutes": [
                "e2aaabed-f901-4bbe-87e6-c781de2fb569"
            ],
            "colour": "cmyk(90%,30%,100%,20%)",
            "opacity": "c-opacity-0002",
            "loaned": false,
            "partOfMultipack": false,
            "recycledContent": 70,
            "recycledContentClaims": [
                "defd2813-0987-486a-8698-e8257b5ece63"
            ],
            "recyclability": true,
            "recyclabilityClaims": [
                "79290e8d-bd0e-4fcc-aa22-b932df206c49"
            ],
            "certification": true,
            "certificationClaims": [
                "79290e8d-bd0e-4fcc-aa22-b932df206c49"
            ],
            "manufacturers": ["GB-COH-10906273"],
            "manufacturedCountry": "826",
            "updateDate": "2023-12-07",
            "releaseDate": "2015-06-16"
        }
    ]
    ```

## Data flow

``` mermaid
flowchart LR
    subgraph baseMaterials[Base Materials]
        bm_example["example base materials"]
    end
    subgraph materials[Materials]
        ma_cardboard["Cardboard
        -
        16f41cca-1a77-4e31-8b0f-2723f752317b"]
        ma_glass["Glass
        -
        b050ab75-4bcb-4c7f-b8f5-8a1f9e5ba7d3"]
    end
        subgraph components["`**Components**`"]
        co_cardboardBox["`**Cardboard box
        - 
        9dad67b0-d5a2-4afb-9287-e712fd1ea3e6**`"]
        co_wineBottle["`**Wine bottle
        - 
        94108707-b914-43f3-bed5-93adbbd208c1**`"]
    end
    subgraph completePackages[Complete Packages]
        cp_example["example complete pakages"]
    end
    baseMaterials --> materials
    ma_cardboard --> co_cardboardBox
    ma_glass --> co_wineBottle
    co_cardboardBox --> completePackages
    co_wineBottle --> completePackages
```


## Guide for how to take measurements

### Units

All measurements should be given using the metric system.

- Height: millimetre (mm)
- Width: millimetre (mm)
- Length: millimetre (mm)
- Volume: cubic metre (m3)
- Weight: grams (g)
- Weight Tolerance: percent (%)

Numbers should be entered with a decimal place. Use the decimal / full stop / period character as a separator. Do not exceed 3 decimal places. When rounding, use convential rounding methods: for 5 and above round up, 4 and below round down. For example: volume = 0.67952 rounded to 0.68. 

**Important**: When converting between systems of measurement, perform the conversion first and then apply the convential rounding. This will give more accuracy and consistency.

### Default Front of a component
Prior caputuring measurements, first determine the default front of the component, this is similar to [GS1](https://www.gs1.org/){target=_blank} (Note: GS1 rules are specified only for complete packaging and not components. Therefore, there are subtle differences to convert from taking a measurement for the complete packaging versus a component). In this standard, as with [GS1](https://www.gs1.org/standards/gs1-package-and-product-measurement-standard/current-standard#4-Consumer-(end-user)-trade-items+4-2-Determining-the-default-front){target=_blank}, the default front is the face with the largest surface area, where area is equal to the `width` times the `height`.

**Important**: Determining of default front provides a consistent, repeatable process to find measurements for a given component.

<center>![image](../img/measurements/figure1.defaultFront.png){:height="40%" width="30%"}</center>
<center>_Figure 1: An example for finding the default front of a component. The default front is the face of the with the largest area (Area = `width` X `height`)_</center>

Some components have the same surface area, thus more than one possible front. These components can be presented both vertically and horizontally. If a component has more than one possible front, the highest side is considered to be the default front.

**Note**: Calculating the area for a rectangular component is simple. However, for non-rectangular components (for example, components with a cylindrical or irregular form), the method to calculate the area is:

- First break the component into multiple sides. Then, for:
    - a round component: do not use (=pi*r^2) to calculate the area. Instead, draw "two dimensional" rectangles around the round component's sides and then calculate the area for each side.
    - any other shape component: draw a "two dimensional" rectangle around the sides of the component, and then calculate the area for each side.
- The side with the maximum area then becomes the default front of that component.

<center>![image](../img/measurements/figure2.defaultFront.png){:height="40%" width="50%"}</center>
<center>_Figure 2: An example for finding the default front of an irregular shaped component. After drawing rectangles around the component, the default front is the face of the with the largest surface area (Area = `width` X `height`)_</center>

### Measuring the height, width, and depth of a component
After the default front has been determined, as with [GS1](https://www.gs1.org/standards/gs1-package-and-product-measurement-standard/current-standard#4-Consumer-(end-user)-trade-items+4-3-Determining-the-height,-width-and-depth){target=_blank}, it is possible to determine the height, width, and depth of a component. 

1. For rectangular components: 
    - Height: from the base to the top
    - Width: from the left to the right
    - Depth: from the front to the back


<center>![image](../img/measurements/figure1.measuring.png){:height="40%" width="30%"}</center>
<center>_Figure 3: Example of measuring the height, width, and depth for a rectangular component._</center>

**Note:** If there are two different measurements for the height, width, or depth, always report the maximum measurement.

<center>![image](../img/measurements/figure2.measuring.png){:height="40%" width="30%"}</center>
<center>_Figure 4: Example of reporting the maximum width, when there are two different size widths. Here, the width reported would be 12 mm because it is larger than the 8 mm. Additionally, there are two different sized depths. Here, the 9 mm depth would be reported because it is larger than the 5 mm depth._</center>


2. For irregular shaped components:
Similar to finding the default front of an irregularly shaped component, draw a "three dimensional" rectangle around the component.
    - Height: from the base to the top
    - Width: from the left to the right
    - Depth: from the front to the back

3. For unformed, flexible components:
    - Take the measurements as if the component was fully formed and filled.

4. For standing components:
    - Height: from the flat surface to the top most point
    - Width: from the left-most point to the right-most point
    - Depth: from the default front to the farthest opposite surface

5. For components with leaning or irregular verticlas:
    - Height: from the flat surface to the top most point (parallel to the vertex)
    - Width: from the left most point to the right most point 
    - Depth: from the default front to the farthest opposite surface

6. For components that are cylindrical:
    - For cylindrical items two dimensions will be nominally equal. Which dimensions are equal is determined by the result of determination of the default front.


## Guide for component images
As with providing measurements, please first find the default front of the component. The image capturing process and naming convention is similar to [GS1](https://www.gs1.org/standards/gs1-product-image-specification-standard/current-standard#1-Introduction){target=_blank}. As with measurements, we altered the gs1 standard for capturing the component.

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


