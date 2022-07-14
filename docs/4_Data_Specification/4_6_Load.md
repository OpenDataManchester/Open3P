# Load

All the complete packaging from different levels (primary, secondary, and tertiary), including multipacks, put together to send to the final destination. Each row corresponds a unique complete packaging (or multipack) item sent to a specific location during a specific time period.

The specification of this csv file is as follows:

[RWS_transportRestrictions.csv ](https://github.com/OpenDataManchester/Open3R/blob/V2/docs/8_Supporting_Files/8_1_4_RWS_Transport_Restrictions_Template.csv){target=_blank}

|Column|Status|Format|Notes|
|:-|:-|:-|:-|
|identifier|`required`|String|A globally unique identifier. See identifiers section for information on how to construct this identifier|
|name|`required`|String|The name of this load.|
|description|`recommended`|String|A brief description of this load.|
|tags|`recommended`|String|A list of identifiers that might be used to identify the load in other systems. For example: bar codes or global trade item number (gtin). To provide tags please follow this format. `tagName1: identifier1; tagName2: identifier2`|
|loadIdentifier|`required`|String|The unique identifier of the created load. A globally unique identifier. See identifiers section for information on how to construct this identifier.|
|packagingItems|`required`|String|The complete packaging and/or the multipack identifiers used to create the load. There must be an equivalent record in the `complete_packaging` or `multipack` data.|
|quantityInLoad|`required`|Numeric|Number of units for the packaging items found in a load that this row corresponds to.|
|startDate|`required`|String|The date that the load began for the destination. Use the format `dd/mm/yyyy`.|
|endDate|`required`|String|The date that the load ended for the destination. Use the format `dd/mm/yyyy`.|
|destinationAddressName|`recommended`|String|The name of the load destination address.|
|destinationAddressStreet|`required`|String|The street address of this load destination.|
|destinationAddressCountry|`required`|String|The country of this load destination.|
|destinationPostalCode|`required`|String|The postal code of this load destination.|
|timesSent|`required`|Numeric|The number of times this load was sent to the destination during the specified time period.|
