# Closure Functions
---

8

## Check Caller

```lua
<bool> checkcaller(<void>)
```

Returns true if the current thread was created by Krnl.

***

## Get Script Closure

```lua
<function> getscriptclosure(<Instance> Script)
```

Returns a new copy of `Script`'s closure.

***

## New C Closure

```lua
<function> newcclosure(<function> f)
```

Pushes a new C closure that invokes the function `f` upon call.

***

## Hook Function

```lua
<function> hookfunction(<function> Old, <function> New)
<function> hookfunc(<function> Old, <function> New)
```

Hooks function `Old`, replacing it with the function `New`. The old function is returned, you must use this function in order to call the original function.

### Example

```lua
old = hookfunction(print, function(text)
    old(string.reverse(text))
    return old(...)
end)

print("123")
```

***

## Is C Closure

```lua
<bool> iscclosure(<function> f)
```

Returns true if `f` is a C closure.

***

## Is Lua Closure

```lua
<bool> islclosure(<function> f)
```

Returns true if `f` is a Lua closure.

***

## Is Krnl Closure 

```lua
<bool> iskrnlclosure(<function> f)
<bool> checkclosure(<function> f)
```

Returns true if `f` is a Krnl closure. (created by krnl)

***

## Get Calling Script

```lua
<Instance> getcallingscript(<void>)
```

Returns the script that is calling the current function.

***

## Lua & C Closures

Closures are basically functions. A Lua closure is a function created in Lua (like through a LocalScript), while C Closures are functions that have been created with the Lua C API (like through an exploit or coroutines).
