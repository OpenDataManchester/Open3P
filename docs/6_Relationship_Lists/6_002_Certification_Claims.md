---
title: Certification Claims
description: The certification claims relationship list.
---

# Certification Claims

The Certification Claims relationship list identifies the certificates that can be assigned to various tables. This is used in the following schemas:

* [Base Materials](../3_Data_Specification/3_1_Base_Materials.md)
* [Materials](../3_Data_Specification/3_2_Materials.md)
* [Components](../3_Data_Specification/3_3_Components.md)
* [Complete Packaging](../3_Data_Specification/3_4_Complete_Packaging.md)

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|certificationIdentifier|`required`|String|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|certificationSource|`recommended`|String|What source provided the certificate? The entry should be the [Certification Source Controlled List](../5_Controlled_Lists/5_002_Certification_Source.md) identifier.|
|certificationIssueDate|`recommended`|String|The date that the certificate was provided/last updated. Use the format `dd/mm/yyyy`.|