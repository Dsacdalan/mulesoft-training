# DataWeave 2.0 Cookbook

Collection of examples of common DataWeave operations.

List of official MuleSoft DataWeave documentation:

* [Introduction to Mule 4: DataWeave 2.0](https://docs.mulesoft.com/mule-runtime/4.1/intro-dataweave2)
* [Part 1: DataWeave 2.0 Syntax Changes in Mule 4](https://blogs.mulesoft.com/dev/mule-dev/dataweave-mule-4-beta-syntax-changes-part-1/)
* [Part 2: DataWeave 2.0 Syntax Changes in Mule 4](https://blogs.mulesoft.com/dev/mule-dev/dataweave-mule-4-beta-syntax-changes-part-2/)
* [MuleSoft 4.1 DataWeave Cookbook](https://docs.mulesoft.com/mule-runtime/4.1/dataweave-cookbook)
* [MuleSoft 4.1 DataWeave Reference](https://docs.mulesoft.com/mule-runtime/4.1/dw-functions)

## Table of Contents

* [If, Else](#If,-Else)
* [Type Casting](#Type-Casting)

## If, Else

```java
%dw 2.0
output application/json
---
{
    message: if (payload.message == "success") true else false
}
```

## Type Casting

Note: DataWeave type casting does not handle NULL.
If a value could be NULL, you must handle the NULL case yourself.

```java
%dw 2.0
output application/json
---
{
    message: payload.message as Boolean
}
```