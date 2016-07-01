# "All Haskell Number Types"

In some languages there is a notion of a "numeric tower." The reasoning behind
this is: there is an obvious way to inject less precise numbers into a more
precise number type. While this makes sense mathematically, this doesn't
even strictly work for the humble Int and Double types[1]!

Haskell has more of a "numeric salad bowl" of number types. Each kind of
number has different strengths and drawbacks. Which one you want to use depends
on factors like

- convenience: The standard library uses Int in many places.
- performance: Is numeric code your program's bottleneck? Double and Int compute
faster due to hardware support. Also they can take less memory and be unboxed.
- faithfulness: Double can't represent an arbitrary rational number. But Rational can.
- security: Allowing users to specify arbitrary Integers or Rationals can be
a denial of service vulnerability.
- safety: Natural will crash on some subtractions while Integer won't.

This is a list of the most common number types and what to import to get them.

|Type      |Import           |Ex.       |Notes|
|----------|-----------------|----------|-----|
|Int       |                 |3         |Signed machine integer (at least 30 bits wide)|
|Integer   |                 |3         |Arbitrary integer|
|Float     |                 |3.125     |Single precision float|
|Double    |                 |3.125     |Double precision float|
|Rational  |Data.Ratio       |5 % 16    |Rational|
|Complex t |Data.Complex     |3.0 :+ 2.0|Complex number|
|Word8<br>Word16<br>Word32<br>Word64|Data.Word|3|Fixed-size unsigned int|
|Word      |Data.Word        |3         |Unsigned machine int|
|Int8<br>Int16<br>Int32<br>Int64|Data.Int|3|Fixed-size signed int|
|Deci<br>Milli<br>Micro<br>Nano<br>Pico<br>Fixed n|Data.Fixed|3.00|Decimal fixed-point|
|Scientific|Data.Scientific  |9.109e-31 |Decimal scientific notation (scientific package)|
|Natural   |Numeric.Natural  |3         |Arbitrary non-negative|
|CReal     |Data.Number.CReal|sqrt 2    |Computable real (numbers package)|
|CReal n   |Data.CReal       |sqrt 2 :: CReal 100|Computable real (exact-real package)|

[1]: `let n = 2^62+1 :: Int in n == floor (fromIntegral n :: Double)`
