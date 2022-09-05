# Multipack

If the complete packaging is further combined to create multipacks, the information is collected here. Each row corresponds to a unique complete packaging item or a unique component.

The specification of this csv file is as follows:

[multipack.csv](https://github.com/OpenDataManchester/PPP/blob/main/docs/7_Supporting_Files/7_1_4_Multipack_Template.csv){target=_blank}

|Column|Status|Format|Notes|
|:-|:-|:-|:-|
|identifier|`required`|String|A globally unique identifier. See identifiers section for information on how to construct this identifier|
|name|`recommended`|String|The name of this multipack.|
|description|`recommended`|String|A brief description of this multipack.|
|tags|`recommended`|Dictionary|A dictionary of identifiers that might be used to identify the complete packaging in other systems. For example: bar codes or global trade item number (gtin). To provide tags please follow this format. `{'tagName1': 'identifier1', 'tagName2': 'identifier2'}`|
|multipackIdentifier|`required`|String|The unique identifier of the created multipack. A globally unique identifier. See identifiers section for information on how to construct this identifier.|
|completePackaging|`required if`|String|The unique identifier of the complete packaging that this row relates to. There must be an equivalent record in the `completePackaging` data. If referring to components, use  `NA`.|
|component|`required if`|String|The unique identifier of the component that this row relates to. There must be an equivalent record in the `component_Catalogue` data. If referring to complete packaging, use `NA`. |
|tier|`recommended`|Integer|The tier associated with the multipack. The inner most tier denoted as 1, and the outermost tier is the biggest number.|
|outsideTier|`required`|Boolean|Is this the very outside of the multipack?|
|identicalQuantity|`required`|Numeric|Number of identical units for the unique complete packaging item or a component this row corresponds to.|
|uploadDate|`here`|String|The date that the component was provided/last updated. Use the format `dd/mm/yyyy`.|
|releaseDate|`here`|String|The date that the component will be available to use. Use the format `dd/mm/yyyy`.|
|discontinuedDate|`here`|String|The date that the component will no longer be available to use. Use the format `dd/mm/yyyy`.|