---
title: Load Catalogue
---

# Load Catalogue

All the complete packaging from different levels (primary, secondary, and tertiary), including multipacks, put together to send to the final destination. Each row corresponds to a single packaging item.

## Table
|Column|<div style="width:90px">Status</div>|Format|Notes|
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

## Diagram

<figure markdown>
[![Schema](../img/load-catalogue-v1.0.0-22-12-20.png){ width="450" }](https://opendatamanchester.github.io/PPP/img/load-catalogue-v1.0.0-22-12-20.png){target=_blank}
  <figcaption>Data schema</figcaption>
</figure>

## Template

Loads should be provided as a separate csv file, in tidy format. This means that each row of the csv file should be a single complete package or a multipack of a load. An example is provided.

The specification of this csv file is as follows:

[load_Catalogue.csv](https://github.com/OpenDataManchester/PPP/blob/main/docs/7_Supporting_Files/7_1_5_Load_Catalogue_Template.csv){target=_blank}

## Example

=== "JSON"

    ``` json linenums="1"
    {
      "identifier": "91F2060F-17CD-DA56-7746-0018A90AEF5A",
      "name": "Full pallet of multipack guacamole dip",
      "description": "24 cases of 3 x multipack tubs of guacamole dip",
      "tags": {
        "GTIN":"00123456789012",
        },
      "loadIdentifier": "CA88F5CE-2D09-AFE0-08D7-44804780F924",
      "packagingItems": "346C5546-282B-C040-CE74-DD0DD4688C0B",
      "quantityInLoad": "72",
      "level": {
        "identifier":"component-catalogue-level-0001",
        "category":"primary",
        "detailed":"The individual container that you store goods in to sell to consumers. This is called a "sales unit". For example, if you sell peas in steel tins with paper labels, the primary packaging is "steel tin" and "paper label"."
      },
      "updateDate": "01/08/2022",
    }
    ```
