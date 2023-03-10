---
title: Identifiers
---

# Identifiers

Identifiers are the way that humans and machines can know that a particular thing is that thing. In the context of Open 3P, there are different ways of talking about the various things involved. A packaging manufacturer may refer to a particular bottle as ‘small clear bottle’, but a filler may know it as ‘500 ml clear bottle’. In a database it may be recorded as ‘0.5L PET Bottle’. While these are all referring to the same thing, it could be hard for a human to know that they are the same, and pretty much impossible for a computer.

To help get around this, we use identifiers. These are codes that we use to unambiguously reference a particular thing. Within the Open 3P data standard we need to uniquely identify every entry. Each record in each schema needs to have an identifier. Since the packaging supply chain is global, the Open 3P data standard needs to be global and thus the unique identifier also needs to be global. We are therefore using the [Universally Unique Identifier (UUID)](https://en.wikipedia.org/wiki/Universally_unique_identifier) standard methodology to (probabilistically) guarantee uniqueness.

> A universally unique identifier (UUID) is a 128-bit label used for information in computer systems. The term globally unique identifier (GUID) is also used.
>
> -*[A Universally Unique IDentifier (UUID) URN Namespace](https://datatracker.ietf.org/doc/html/rfc4122)*

## Generating

Generating a UUID must be done by a machine and there are various ways to create one. 

### Online

There are various online tools available, including but not limited to and in no specific order:

- [Online UUID Generator](https://www.uuidgenerator.net/)
- [UUID Generator](https://www.uuidgen.org/v/4)
- [Online UUID/GUID Generator](https://www.uuidtools.com)
- [Generate UUID Online](https://generate-uuid.com)
- [Webtools - Online UUID (GUID) Generator](https://www.webtools.services/uuid-generator)

### In code

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

=== "Excel Function"

    ``` vb
    =CONCATENATE(DEC2HEX(RANDBETWEEN(0,4294967295),8),"-",DEC2HEX(RANDBETWEEN(0,65535),4),"-",DEC2HEX(RANDBETWEEN(0,65535),4),"-",DEC2HEX(RANDBETWEEN(0,65535),4),"-",DEC2HEX(RANDBETWEEN(0,4294967295),8),DEC2HEX(RANDBETWEEN(0,65535),4))
    ```

=== "vba"

    ``` vb
    Function GUID$(Optional lowercase As Boolean, Optional parens As Boolean)
        Dim k&, h$
        GUID = Space(36)
        For k = 1 To Len(GUID)
            Randomize
            Select Case k
                Case 9, 14, 19, 24: h = "-"
                Case 15:            h = "4"
                Case 20:            h = Hex(Rnd * 3 + 8)
                Case Else:          h = Hex(Rnd * 15)
            End Select
            Mid$(GUID, k, 1) = h
        Next
        If lowercase Then GUID = LCase$(GUID)
        If parens Then GUID = "{" & GUID & "}"
    End Function
    ```

=== "T-SQL"

    ``` t-sql
    NEWID ( )
    ```

=== "PHP"

    ``` php
    function guidv4($data = null) {
        // Generate 16 bytes (128 bits) of random data or use the data passed into the function.
        $data = $data ?? random_bytes(16);
        assert(strlen($data) == 16);

        // Set version to 0100
        $data[6] = chr(ord($data[6]) & 0x0f | 0x40);
        // Set bits 6-7 to 10
        $data[8] = chr(ord($data[8]) & 0x3f | 0x80);

        // Output the 36 character UUID.
        return vsprintf('%s%s-%s-%s-%s-%s%s%s', str_split(bin2hex($data), 4));
    }
    ```











