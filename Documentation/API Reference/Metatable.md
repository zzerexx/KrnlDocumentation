# Metatable Functions
---

5

## Get Raw Metatable

```lua
<table> getrawmetatable(<table> Table)
<table> debug.getmetatable(<table> Table)
```

Returns `Table`'s raw metatable, bypassing the `__metatable` field.

***

## Set Raw Metatable 

```lua
<void> setrawmetatable(<table> Table, <table> New)
<void> debug.setmetatable(<table> Table, <table> New)
```

Sets `Table`'s metatable to `New`.

***

## Set Read Only

```lua
<void> setreadonly(<table> Table, <bool> Value)
```

Sets `Table`'s read-only condition to `Value`.

***

## Is Read Only 

```lua
<bool> isreadonly(<table> Table)
```

Returns `Table`'s read-only condition.

***

## Hook Metamethod

```lua
<function> hookmetamethod(<Instance> Object, <string> Metamethod, <function> f)
```

Hooks the `Metamethod` passed in `Object`'s metatable with `f`. A function to call the original metamethod is returned, you must use this function in order to call the original metamethod.

### Example

```lua
-- __namecall Hook
local OldNamecall
OldNamecall = hookmetamethod(game,"__namecall",function(self,...)
    return OldNamecall(self,...)
end)

-- __index Hook
local OldIndex
OldIndex = hookmetamethod(game,"__index",function(self,i)
    return OldIndex(self,i)
end)

-- __newindex Hook
local OldNewIndex
OldNewIndex = hookmetamethod(game,"__newindex",function(self,i,v)
    return OldNewIndex(self,i,v)
end)
```

### Example: Basic Remote Spy

```lua
local old
old = hookmetamethod(game,"__namecall",function(self,...)
	local args = {...}
	if getnamecallmethod() == "FireServer" then
        local Path = self:GetFullName()
        local Arguments = table.concat(args,"\n")
		print("Path: "..Path.."\nArguments:\n"..Arguments)
	end
	return old(self,...)
end)
```
