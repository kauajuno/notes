SQL has multiple types, some are used more often and some are used only in very specific situation, let's get through all of them:

# Numeric types

Numeric types are all the types that represent numbers, they are:

- TINYINT: represents an integer and occupies 1 byte.
- SMALLINT: represents an integer and occupies 2 bytes.
- MEDIUMINT: represents an integer and occupies 3 bytes.
- INT: represents an integer and occupies 4 bytes.
- BIGINT: represents an integer and occupies 8 bytes.
- FLOAT: represents numbers with decimal points and occupies 4 bytes, offering 7 decimal places of accuracy.
- DOUBLE: represents numbers with decimal points and occupies 8 bytes, offering 15 decimal places of accuracy.
- DECIMAL: represents numbers with decimal points in a more flexible way, where it is possible to specify how many digits the number has in total and how many come after the decimal point.
- BIT: represents a single binary value.

>[!info]
> The bytes occupied by a type influence how large is the number it can store. For example, TINYINT occupies 1 byte, therefore, it can represent numbers from -2⁷ to 2⁷ - 1, as one bit is used for the signal. If signaling the value is unnecessary, the [[SQL modifiers|modifier]] UNSIGNED can be used so it can store numbers from 0 all the way to 2⁸ - 1.


# Date and time types

These types intend to represent date and/or time in different ways:

- DATE: represents a date in the format YYYY/MM/DD.
- TIME: represents a time in the format HH:MM:SS.
- DATETIME: basically a junction of the last two, in the format YYYY/MM/DD HH:MM:SS
- TIMESTAMP: it's DATETIME, but used to track changes on a row (automatically updates when a row is changed).
- YEAR: represents a year in the format YYYY.

# String types

String types are used to represent strings in different ways:

- CHAR: represents a fixed-length string.
- VARCHAR: represents a variable-length string.
- TINYTEXT: represents a string using 2⁸ - 1 bytes.
- MEDIUMTEXT: represents a string using 2¹⁶ - 1 bytes.
- TEXT: represents a string using 2²⁴ - 1 bytes.
- BIGTEXT: represents a string using 2³² - 1 bytes.
- BINARY: same as CHAR but for a string composed of binary values.
- VARBINARY: same as VARCHAR but for a string composed of binary values.

# Logic types

Actually, there's a single logic type:

- BOOLEAN: essentially it works just the same as BIT, but this one explicitly stores either true or false instead of 0 and 1.

# Set and Enum types

These types define which values it can store, with a single difference between the two:

- ENUM: given multiple possible values, it can store any of them or NULL.
- SET: given multiple possible values, it can store many of them or NULL.
