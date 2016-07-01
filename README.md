# "All Haskell Number Types"

In some languages there is a notion of a "numeric tower." The reasoning behind
this is: there is an obvious way to inject less precise numbers into a more
precise number type. While this makes sense mathematically, this doesn't
even strictly work for the humble Int and Double types[1]!

Haskell has more of a "numeric salad bowl" of number types. Each kind of
number has different strengths and drawbacks. Which one you want to use depends
on factors like

- convenience: The standard library uses Int in many places.
- performance: Is numeric code your programs bottleneck? Double and Int compute
faster due to hardware support. They can also take up less memory.
- faithfulness: Double can't represent an arbitrary rational number. But Rational can.
- security: Allowing users to specify arbitrary Integers or Rationals can be
a denial of service vulnerability.

This is a list of the most common number types and what to import to get them.

|Type |Import |Notes|
|-----|-------|-----|
|Int  ||Signed machine integer (at least 30 bits wide)|
|Integer ||Arbitrary integer|
|Float ||Single precision float|
|Double ||Double precision float|
|Word8<br>Word16<br>Word32<br>Word64|Data.Word|fixed-size unsigned int|
|Word   |Data.Word|unsigned machine int|
|Int8
|Int16
|Int32
|Int64 |Data.Int|fixed-size signed int|
|Rational |Data.Ratio|type Rational = Ratio Integer, e.g. 5 % 16|

