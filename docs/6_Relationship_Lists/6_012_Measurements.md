---
title: Meaurements
description: The measurements relationship list.
---

# Measurements

The measurements relationship list identifies the different measurement that an item in each schema can have. 

## Table
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|measurementIdentifier|`mandatory`|UUID|A globally unique identifier. See [identifiers](../4_Identifiers/4_1_Identifiers.md) section for information on how to construct this identifier|
|itemIdentifier|`mandatory`|UUID|The unique identifier of the items that this component is made of. There must be an equivalent record in the `Base_Materials`, `Materials`, `Components`, `Complete_Packaging`, `Multipacks` OR `Load` data.|
|measureIdentifier|`mandatory`|ID|The measure type of this item. The entry here should be drawn from the [meausures](../5_Controlled_Lists/5_017_Measures.md).|
|measurementValue|`mandatory`|Decimal|The value of this measurement. |
|tolerance|`optional`|Decimal|The threshold of the measure that this item can vary by. |
|toleranceType|`optional`|String|The threshold of the measurment type this can be given in `unit` or `percentage`; where `unit` matches to the `measure` unit. For example if the measure unit is grams, the tolerance type will also be grams. |
|date|`optional`|Date|The date that the measure was last verified/measured. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|

## Diagram

``` mermaid
erDiagram
  as["ALL SCHEMA"]
  as }o..o{ MEASUREMENTS : attributes
  MEASUREMENTS {
    measurementIdentifier UUID "*"
    itemIdentifier UUID "*"
    measureIdentifier ID "*"
    measurementValue Decimal
    tolerance Decimal
    toleranceType String
    date Date
  }
  MEASUREMENTS }o--o{ CONTROLLED_LISTS : attributes
  CONTROLLED_LISTS {
    measures mandatory
  }
```
## Example

=== "Wine bottle Measurements - JSON"

    ``` json linenums="1" hl_lines="3 4"
    [
      {
        "measurementIdentifier": "e83b250b-8fd5-472f-82d1-049b0c4e9ca9",
        "itemIdentifier": "94108707-b914-43f3-bed5-93adbbd208c1",
        "measureIdentifier": "measure-0001",
        "measurementValue": 700,
        "tolerance": 6,
        "toleranceType": "percentage"
      },
      {
        "measurementsIdentifier": "a8bd2583-bbbb-49bb-a6e9-ea735a0b550e",
        "itemIdentifier": "94108707-b914-43f3-bed5-93adbbd208c1",
        "measureIdentifier": "measure-0002",
        "measurementValue": 305,
        "date": "2015-06-16"
      }
    ]
    ```
=== "Wine bottle Measurements - XML"

    ``` xml linenums="1" hl_lines="3 4"
    <?xml version="1.0" encoding="UTF-8" ?>
    <root>
      <row>
        <measurementIdentifier>e83b250b-8fd5-472f-82d1-049b0c4e9ca9</measurementIdentifier>
        <itemIdentifier>94108707-b914-43f3-bed5-93adbbd208c1</itemIdentifier>
        <measureIdentifier>measure-0001</measureIdentifier>
        <measurementValue>700</measurementValue>
        <tolerance>6</tolerance>
        <toleranceType>percentage</toleranceType>
      </row>
      <row>
        <measurementsIdentifier>a8bd2583-bbbb-49bb-a6e9-ea735a0b550e</measurementsIdentifier>
        <itemIdentifier>94108707-b914-43f3-bed5-93adbbd208c1</itemIdentifier>
        <measureIdentifier>measure-0002</measureIdentifier>
        <measurementValue>305</measurementValue>
        <date>2015-06-16</date>
      </row>
    </root>
    ```