# Debug Library
---

16

## Get Constant

```lua
<variant> debug.getconstant(<function> f, <int> idx)
<variant> getconstant(<function> f, <int> idx)
```

Returns the constant at index `idx` in function `f` or level `f`. 

### Example

```lua
local idx = 1
local isReady = false
function f()
    if idx > 0 then
        print(isReady and 'Can initiate an ability' or 'Cannot initiate an ability')
    elseif idx == 0 then
        print('bruh moment')
    end
end
print(getconstant(f, 2))
```

***

## Get Constants

```lua
<table> debug.getconstants(<function> f)
<table> getconstants(<function> f)
```

Returns the constants in function `f` or at level `f`. 

### Example

```lua
local idx = 1
local isReady = false
function f()
    if idx > 0 then
        print(isReady and 'Can initiate an ability' or 'Cannot initiate an ability')
    elseif idx == 0 then
        print('bruh moment')
    end
end

table.foreach(getconstants(f),print)
```

***

## Set Constant

```lua
<void> debug.setconstant(<function> f, <int> idx, union<number, bool, string> value)
<void> setconstant(<function> f, <int> idx, union<number, bool, string> value)
```

Set constant `idx` to tuple `value` at level or function `f`.

***

## Get Upvalue

```lua
<variant> debug.getupvalue(union<function, number> f, <number> idx)
<variant> getupvalue(union<function, number> f, <number> idx)
```

Returns the upvalue with name `idx` in function or level `f`. 

### Example

```lua
local usable = false;
local duration = 5;
local start = tick();

function f()
    if not usable then
        if duration > (tick()-start) then
            print('You cannot use this yet!')
            return
        end

        print('Executing the ability!')
    end
end

print(getupvalue(f, 1))
```

***

## Get Upvalues

```lua
<table> debug.getupvalues(<function> f)
<table> getupvalues(<function> f)
```

Retrieve the upvalues in function `f` or at level `f`. 

### Example

```lua
local idx = 1
local isReady = false
function f()
    if idx > 0 then
        print(isReady and 'Can initiate an ability' or 'Cannot initiate an ability')
    elseif idx == 0 then
        print('bruh moment')
    end
end

table.foreach(getupvalues(f),print)
```

***

## Set Upvalue 

```lua
<void> debug.setupvalue(<function> f, <int> idx, <table> value)
<void> setupvalue(<function> f, <int> idx, <table> value)
```

Set upvalue `idx` to value `value` at level or function `f`. 

### Example

```lua
local usable = false;
local duration = 5;
local start = tick();

function f()
    if not usable then
        if duration > (tick()-start) then
            print('You cannot use this yet!')
            return
        end

        print('Executing the ability!')
    end
end

debug.setupvalue(f, 2, 0) -- on the index of 2, which is the duration

f()
```

***

## Get Proto 

```lua
union<table, function> debug.getproto(<function> f, <int> idx, <bool?> activated)
union<table, function> getproto(<function> f, <int> idx, <bool?> activated)
```

Gets the inner function of `f` at `index`.

:::hint
## Note

If activated is *true*, it will return a table of functions.
These are the instances of that function that exist within the GC.
:::

***

## Get Protos 

```lua
<table> debug.getprotos(<function> f)
<table> getprotos(<function> f)
```

Returns a table containing the inner function `f`.

### Example

```lua
function f()
    function f1()
        print('hello from function f1')
    end

    function f2()
        print('hello from function f2')
    end
end

for i,v in pairs(getprotos(f)) do
    v()
end
```

:::hint
## Note

These functions will not have upvalues, use debug.getproto with activated set to true to get a list of instances.
:::

***

## Set Proto 

```lua
<void> debug.setproto(<function> f, <int> idx, <function> replacement)
<void> setproto(<function> f, <int> index, <function> replacement)
```

Replaces `f` at `index` with function `replacement` at level or function `f`.

:::hint
## Note

Set Proto has been removed due to the [ACE vulnerability](https://v3rmillion.net/showthread.php?tid=1149589).
:::

***

## Get Stack 

```lua
<table> debug.getstack(<function> f, <int> idx, <table> value)
<table> getstack(<function> f, <int> idx, <table> value)
```

Gets the method stack at level or function `f`.

***

## Set Stack 

```lua
<void> debug.setstack(<function> f, <int> idx, <table> value)
<void> setstack(<function> f, <int> idx, <table> value)
```

Sets the stack indice at `indice` to value `value` at level or function `f`.

***

## Get Registry 

```lua
<table> debug.getregistry(<void>)
<table> getregistry(<void>)
```

Returns the Lua registry.

***

## Get Info 

```lua
<table> debug.getinfo(<function> f)
<table> getinfo(<function> f)
```

Returns a table of information about function `f`.

### Info

| Name        | Type     | Description                                                    |
| ----------- | -------- | -------------------------------------------------------------- |
| name        | String   | The name of the function                                       |
| short_src   | String   | A shorter version of source                                    |
| what        | String   | What the function is&#xA;Lua = Lua function&#xA;C = C function |
| currentline | Integer  | The line that is currently active                              |
| nups        | Integer  | The number of upvalues that the function has                   |
| func        | Function | The function that is active                                    |
| source      | String   | Where the function was defined                                 |

### Example 

```lua
table.foreach(getinfo(print),print)
```

***

## Info 

```lua
<variant> debug.info(<function> f, <int> idx)
<variant> info(<function> f, <int> idx)
```

Allows programmatic inspection of the call stack.

***

## Traceback 

```lua
<string> debug.traceback(<string> message, <number> level = 1)
<string> traceback(<string> message, <number> level = 1)
```

Returns a traceback of the current function call stack as a string.

### Example

```lua
local function a()
	print(traceback("Specific moment during a()"))
end
 
local function b()
	a()
end
 
local function c()
	b()
end
 
a()
```

***

## Profile Begin 

```lua
<void> debug.profilebegin(<string> label)
<void> profilebegin(<string> label)
```

Opens a microprofiler label.

***

## Profile End 

```lua
<void> debug.profileend(<void>)
<void> profileend(<void>)
```

Closes the top microprofiler label.

***

## Set Metatable

```lua
<void> debug.setmetatable(<table> Table, <table> New)
```

Sets `Table`'s metatable to `New`.
An alias for `setrawmetatable`.

***

## Get Metatable

```lua
<void> debug.getmetatable(<table> Table)
```

Returns `Table`'s raw metatable, bypassing the `__metatable` field.
An alias for `getrawmetatable`.
