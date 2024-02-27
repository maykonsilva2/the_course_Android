### Integer types

| Type  | Size(bits) | Min value                         | Max value                          |
|-------|------------|-----------------------------------|------------------------------------|
| Byte  | 8          | -128                              | 127                                |
| Short | 16         | -32768                            | 32767                              |
| Int   | 32         | -2,147,483,648(-2^31)             | 2,147,483,647(2^31 -1)             |
| Long  | 64         | -9,223,372,036,854,775,808(-2^63) | 9,223,372,036,854,775,807(2^63 -1) |

NOTE: You can see that these values are always -1 in the last place because they are one less than a power of 2. For example, 2^31 is 2,147,483,648, and 2^31 - 1 is 2,147,483,647. This is because when you subtract 1 from a power of 2, you change all the bits from 0 to 1, except for the most significant bit, which becomes 0. 

For example:
````kotlin
    2^31 = 10000000000000000000000000000000 // 1 followed by 31 zeros
    2^31 - 1 = 01111111111111111111111111111111 // 0 followed by 31 ones
````

This pattern holds for any power of 2 and any number of bits. For example, with 8 bits, the range of values is from -2^7 to 2^7 - 1, which is -128 to 127.

````kotlin
    2^7 = 10000000 // 1 followed by 7 zeros
    2^7 - 1 = 01111111 // 0 followed by 7 ones
````

NOTE: When you initialize a variable with no explicit type specification, the compiler automatically infers the type.
````kotlin
    val one = 1 // Int
    val threeBillion = 3000000000 // Long
    val oneLong = 1L // Long. To specify the log value explicit, append the suffix L to the value
    val oneByte: Byte = 1 //specify the explicit type
````

### Floating-point types

| Type   | Size(bits) | Significand bits | Exponent bits | Decimal digits |
|--------|------------|------------------|---------------|----------------|
| Float  | 32         | 24               | 8             | 6-7            |
| Double | 64         | 53               | 11            | 15-16          |

Note: To delve deeper into the *significant bits* https://towardsdatascience.com/binary-representation-of-the-floating-point-numbers-77d7364723f1

NOTE: To explicitly specify the ``Float`` type for a value, add the suffix `f` or `F`. If such a value contains more than `6-7` decimal digits, it will be rounded.

NOTE: kotlin also supports a conventional notation for floating-point numbers: 
- Double by default: 123.5  -> 123.5e10
