---
title: Identifiers
---

# Identifiers

Identifiers are crucial for uniquely referencing items within the Open 3P ecosystem, enabling both humans and machines to accurately identify and reference specific objects. Without identifiers, it can be challenging for different stakeholders to recognise that they are referring to the same thing, leading to confusion and inefficiencies.

## Types of Identifiers

In the Open 3P data standard, various types of identifiers are used to distinguish and categorise items based on their generation method and intended usage. These identifiers can be broadly categorised into three types:

1. **Universally Unique Identifier (UUID)**: These identifiers are globally unique and do not contain any information about the user, organisation, or machine that created them. UUIDs ensure complete anonymity and eliminate the risk of conflicts with other identifiers.

2. **Controlled List Identifier**: Controlled list identifiers are specifically created for use within the Open 3P standard. They define specific attributes within the standard and are regulated by the Standard Custodian Board to maintain consistency and integrity across the ecosystem.

3. **External Identifier**: External identifiers are generated outside the Open 3P standard but can be incorporated into it to establish links with external data sources. One example is the Global Trade Item Number (GTIN), commonly used as a barcode. While GTINs are not specific to the Open 3P standard, they provide valuable links to external product data and are widely recognised in the industry.

!!! question "Why Not Use GTIN as the Packaging Identifier?"

    The question often arises as to why GTINs are not used as packaging identifiers within the Open 3P standard. There are several reasons for this decision:

    1. **Organisational Identifiability**: GTINs inherently contain information about the organisation that provided the item, potentially compromising anonymity within the Open 3P ecosystem.

    2. **Stability and Flexibility**: GTINs do not need to change when minor packaging variations occur, leading to potential inconsistencies in the identification process.

    3. **Access and Standards**: GTINs are regulated by standards bodies and may not be readily accessible or applicable to all packaging items within the Open 3P ecosystem.

By utilising a standardised approach to identifiers within the Open 3P ecosystem, stakeholders can ensure consistency, interoperability, and accuracy in referencing packaging materials and products.

## Universally Unique Identifier (UUID)

Each record in each schema needs to have an identifier. Since the packaging supply chain is global, the Open 3P data standard needs to be global and thus the unique identifier also needs to be global. We are therefore using the [Universally Unique Identifier (UUID)](https://en.wikipedia.org/wiki/Universally_unique_identifier) standard methodology to (probabilistically) guarantee uniqueness.

> A universally unique identifier (UUID) is a 128-bit label used for information in computer systems. The term globally unique identifier (GUID) is also used.
>
> -*[A Universally Unique IDentifier (UUID) URN Namespace](https://datatracker.ietf.org/doc/html/rfc4122)*

### Generating

Generating a UUID must be done by a machine and there are various ways to create one. 

#### Online

There are various online tools available, including but not limited to and in no specific order:

- [Online UUID Generator](https://www.uuidgenerator.net/)
- [Online UUID/GUID Generator](https://www.uuidtools.com)
- [Generate UUID Online](https://generate-uuid.com)
- [Webtools - Online UUID (GUID) Generator](https://www.webtools.services/uuid-generator)

#### In code

=== "Python"

    ``` py
    import uuid

    uuid.uuid4()
    ```

=== "C#"

    ``` c#
    using System;
    using System.Diagnostics;

    namespace SampleApplication {
        class Program {
            static void Main(string[] args) {
                Guid myuuid = Guid.NewGuid();
                string myuuidAsString = myuuid.ToString();

                Debug.WriteLine("Your UUID is: " + myuuidAsString);
            }
        }
    }
    ```

=== "T-SQL"

    ``` t-sql
    NEWID ( )
    ```

## Controlled List Identifier

Controlled lists are fundamental elements of data standards, crucial for maintaining consistency and accuracy in data entry within the packaging industry. They serve as centralised repositories for standardised terms and phrases used across various aspects of packaging.

Each entry in a controlled list is assigned a unique identifier, allowing for precise referencing of specific records within the list. These identifiers serve as keys to access detailed information about each term or concept, ensuring clarity and uniformity in data representation.

By leveraging controlled list identifiers, stakeholders can streamline data entry processes, minimise errors, and promote interoperability across different systems and platforms within the packaging ecosystem.

## External Identifier

External identifiers play a vital role in linking data within the Open 3P standard to external sources, enabling seamless integration and access to additional information. While these identifiers are generated outside the Open 3P standard, they can be incorporated into it to establish connections with relevant external data sources.

One example of an external identifier commonly used in the packaging industry is the Global Trade Item Number (GTIN), which is widely recognised as a barcode. GTINs provide valuable links to external product data and facilitate efficient inventory management and supply chain operations.

To provide external identifiers within the Open 3P standard, follow this format:

=== "JSON" 

    ```json
    {
        "externalIdentifierName1": "identifier1",
        "externalIdentifierName2": "identifier2"
    }
    ```
For instance, a dictionary of identifiers for base materials in other systems could include the manufacturer's own internal identifier and the GTIN:

=== "JSON"

    ```json
    {
        "ManufacturerInternalID": "ABC123",
        "GTIN": "01234567890123"
    }
    ```

By adhering to standardised formats for external identifiers, stakeholders can ensure interoperability and compatibility with external data sources, enhancing data quality and facilitating seamless data exchange within the packaging ecosystem.






