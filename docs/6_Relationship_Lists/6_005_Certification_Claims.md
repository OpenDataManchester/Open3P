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
|certificationSource|`required`|String|What source provided the certificate? The entry should be the [Certification Source Controlled List](../5_Controlled_Lists/5_002_Certification_Source.md) identifier.|
|certificationIssueDate|`recommended`|String|The date that the certificate was provided/last updated. Use the format `dd/mm/yyyy`.|

## Diagram

``` mermaid
erDiagram
  BASE_MATERIALS }o..o{ CERTIFICATION_CLAIMS : within
  MATERIALS }o..o{ CERTIFICATION_CLAIMS : within
  COMPONENTS}o..o{ CERTIFICATION_CLAIMS : within
  COMPLETE_PACKAGING }o..o{ CERTIFICATION_CLAIMS : within
  CERTIFICATION_CLAIMS {
    certificationIdentifier String
    certificationSource String
    certificationIssueDate String
  }
  CERTIFICATION_CLAIMS }o--o{ CONTROLLED_LISTS : attributes
      CONTROLLED_LISTS {
    certificationSource required }
  }
```

## Template

Certification claims should be provided as a separate csv file. The specification of this csv file is as follows:

[Certification Claims Template](https://www.open3p.org/wp-content/uploads/2023/09/certificationClaims20230922.csv)

## Example

=== "JSON"

    ``` json linenums="1"
    --A certificate provided by the FSA.
    {
      "certificationIdentifier": "eed87ac3-6e3e-45fb-af2c-dd0f64fdb597",
      "certificationSource": "certification-source-0002",
      "certificationIssueDate": "01/08/2022"
    }
    ```

