# Unique Component

From the component catelogue, information differs based on the application of the component. Pull the component catelogue item to add unique information.

[rws_area_served.csv](https://github.com/OpenDataManchester/Open3R/blob/V2/docs/8_Supporting_Files/8_1_2_RWS_Area_Served_Template.csv){target=_blank}

|Column|Status|Format|Notes|
|:-|:-|:-|:-|
|identifier|`required`|String|A globally unique identifier. See identifiers section for information on how to construct this identifier|
|name|`required`|String|The name of this component.|
|description|`recommended`|String|A brief description of this component.|
|tags|`recommended`|String|A list of identifiers that might be used to identify the component in other systems. For example: bar codes or global trade item number (gtin). To provide tags please follow this format. `tagName1: identifier1; tagName2: identifier2`|
|componentCatalogue|`required`|String|The unique identifier of the component that this row relates to. There must be an equivalent record in the `component_Catalogue` data|
|level|`required`|String|The component level of packaging in the system `i.e., primary, secondary, tertiary`. Use the identifier of the level that this row relates to. The entry here should be drawn from the level controlled list.|
|reuseSystem|`required`|String|The system that facilitates the reuse of the component  `e.g., Loop`|
|importedUK|`required`|Boolean|Is the component manufactured in the UK?|
|manufacturedCountry|`required`|Numeric|The country the component was manufactured in. Use the country numeric [ISO codes](https://www.iban.com/country-codes) as described in the ISO 3166 international standard.|
|directContactWithProduct|`required`|Boolean|Does the component come into direct contact with the product before purchased by a consumer?|
|uploadDate|`required`|String|The date that the component was provided/last updated. Use the format `dd/mm/yyyy`.|
|releaseDate|`required`|String|The date that the component will be available to use. Use the format `dd/mm/yyyy`.|
|discontinuedDate|`required`|String|The date that the component will no longer be available to use. Use the format `dd/mm/yyyy`.|

