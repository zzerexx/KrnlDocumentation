# Bit Library
---

Read more about Bitwise Operators [here](http://lua-users.org/wiki/BitwiseOperators).
Krnl doesn't have all of them, but it still has most of them.
14

## And

```lua
<int> bit.band(<uint> x, <uint> disp)
```

Returns the bitwise *and* of its operands.

***

## Or

```lua
<int> bit.bor(<uint> x, <uint> disp)
```

Returns the bitwise *or* of its operands.

***

## Xor

```lua
<int> bit.bxor(<uint> x, <uint> disp)
```

Returns the bitwise *exclusive or* of its operands.

***

## Not

```lua
<int> bit.bnot(<uint> x)
```

Returns the bitwise negation of `x`.

***

## Left Shift

```lua
<int> bit.lshift(<uint> x, <uint> disp)
```

Returns the number `x` shifted `disp` bits to the left.

***

## Right Shift

```lua
<int> bit.rshift(<uint> x, <uint> disp)
```

Returns the number `x` shifted `disp` bits to the left.

***

## Arithmetic Shift

```lua
<int> bit.arshift(<int> x, <int> disp)
```

Returns the number `x` shifted `disp` bits to the right. The number `disp` may be any representable integer. Negative displacements shift to the left.

This shift operation is what is called an *arithmetic* shift. Vacant bits on the left are filled with copies of the higher bit of `x`; vacant bits on the right are filled with zeros. In particular, displacements with absolute values higher than 31 result in zero or `0xFFFFFFFF` (all original bits are shifted out).

***

## Left Rotate

```lua
<int> bit.lrotate(<int> x, <int> disp)
```

Returns the number `x` rotated `disp` bits to the left.

***

## Right Rotate

```lua
<int> bit.rrotate(<int> x, <int> disp)
```

Returns the number `x` rotated `disp` bits to the right.

***

## Extract

```lua
<uint> bit.extract(<uint> x, <uint> field, <uint> width = 1)
```

Returns the unsigned number formed by the bits `field` to `field + width - 1` from `x`.

***

## Replace

```lua
<uint> bit.replace(<uint> x, <uint> field, <uint> width)
```

Returns a copy of `x` with the bits `field` to `field + width - 1` replaced by the value `v`.

***

## Test

```lua
<bool> bit.btest(<number> x)
```

Returns a boolean signalling whether the bitwise *and* of its operands is different from zero.

***

## Count Left

```lua
<uint> bit.countlz(<uint> x)
```

Returns the number of consecutive zero bits in the 32-bit representation of `x` starting from the left-most (most significant) bit. Returns `32` if `x` is zero.

***

## Count Right

```lua
<uint> bit.countrz(<uint> x)
```

Returns the number of consecutive zero bits in the 32-bit representation of `x` starting from the right-most (least significant) bit. Returns `32` if `x` is zero.


