---
title: Multipack
---

# Multipack

If the complete packaging is further combined to create multipacks, the information is collected here. Each row corresponds to a single packaging item.

**Note:** The multipack portion is optional (only applies to multipacks). If the complete packaging or component is *not* in a multipack, all of the fields below are optional. 

The specification of this csv file is as follows:

[multipack.csv](https://github.com/OpenDataManchester/PPP/blob/main/docs/7_Supporting_Files/7_1_4_Multipack_Template.csv){target=_blank}

|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`required`|String|A globally unique identifier. See identifiers section for information on how to construct this identifier|
|name|`recommended`|String|The name of this multipack.|
|description|`recommended`|String|A brief description of this multipack.|
|tags|`recommended`|Dictionary|A dictionary of identifiers that might be used to identify the complete packaging in other systems. For example: bar codes or global trade item number (gtin). To provide tags please follow this format. `{'tagName1': 'identifier1', 'tagName2': 'identifier2'}`|
|multipackIdentifier|`required`|String|The unique identifier of the created multipack. A globally unique identifier. See identifiers section for information on how to construct this identifier.|
|packagingItems|`required`|String|The complete packaging and/or the component identifiers used to create the multipack. There must be an equivalent record in the `complete_packaging` or `component_Catalogue` data.|
|tier|`recommended`|Integer|The tier associated with the multipack. The inner most tier denoted as 1, and the outermost tier is the biggest number.|
|identicalQuantity|`required`|Numeric|Number of identical units for the unique complete packaging item or a component this row corresponds to.|
|updateDate|`required`|String|The date that the multipack was provided/last updated. Use the format `dd/mm/yyyy`.|
|releaseDate|`recommended`|String|The date that the component will be available to use. Use the format `dd/mm/yyyy`.|
|discontinueDate|`recommended`|String|The date that the component will no longer be available to use. Use the format `dd/mm/yyyy`.|