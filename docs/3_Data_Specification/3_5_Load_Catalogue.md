# Load Catalogue

All the complete packaging from different levels (primary, secondary, and tertiary), including multipacks, put together to send to the final destination. Each row corresponds to a single packaging item.

The specification of this csv file is as follows:

[load_Catalogue.csv](https://github.com/OpenDataManchester/PPP/blob/main/docs/7_Supporting_Files/7_1_5_Load_Catalogue_Template.csv){target=_blank}

|Column|<div style="width:80px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`required`|String|A globally unique identifier. See identifiers section for information on how to construct this identifier|
|name|`recommended`|String|The name of this load.|
|description|`recommended`|String|A brief description of this load.|
|tags|`recommended`|Dictionary|A dictionary of identifiers that might be used to identify the complete packaging in other systems. For example: bar codes or global trade item number (gtin). To provide tags please follow this format. `{'tagName1': 'identifier1', 'tagName2': 'identifier2'}`|
|loadIdentifier|`required`|String|The unique identifier of the created load. A globally unique identifier. See identifiers section for information on how to construct this identifier.|
|packagingItems|`required`|String|The complete packaging and/or the multipack identifiers used to create the load. There must be an equivalent record in the `complete_packaging` or `multipack` data.|
|quantityInLoad|`required`|Numeric|Number of units for the packaging items found in a load that this row corresponds to.|
|level|`required`|String|The intended use of the component for the packaging `i.e., primary, secondary, tertiary`. The entry here should be drawn from the level controlled list.|
|updateDate|`required`|String|The date that the load catalogue was provided/last updated. Use the format `dd/mm/yyyy`.|
