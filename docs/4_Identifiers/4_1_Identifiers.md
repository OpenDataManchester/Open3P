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

=== "C"

    ``` c
    #include <stdio.h>

    int main(void) {
      printf("Hello world!\n");
      return 0;
    }
    ```

=== "C++"

    ``` c++
    #include <iostream>

    int main(void) {
      std::cout << "Hello world!" << std::endl;
      return 0;
    }
    ```

=== "Excel Function"

    ``` vb
    =CONCATENATE(DEC2HEX(RANDBETWEEN(0,4294967295),8),"-",DEC2HEX(RANDBETWEEN(0,65535),4),"-",DEC2HEX(RANDBETWEEN(0,65535),4),"-",DEC2HEX(RANDBETWEEN(0,65535),4),"-",DEC2HEX(RANDBETWEEN(0,4294967295),8),DEC2HEX(RANDBETWEEN(0,65535),4))
    ```

=== "T-SQL"

    ``` t-sql
        NEWID ( )
    ```











