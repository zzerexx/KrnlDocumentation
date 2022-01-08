# Krnl Library
---

2

## Require 

```lua
<table> Krnl:Require(<string> Module)
```

Returns a module.
Only modules in the Vendor library can be required. (Hook, Promise, Thread, Maid, Signal)

### Example

```lua
local Hook = Krnl:Require("Hook")
```

***

## Load Async 

```lua
<variant> Krnl:LoadAsync(<string> Url)
```

Loads the contents of `Url` as a chunk.
Equivalent to `loadstring(game:HttpGet(Url))()`.

### Example

```lua
Krnl:LoadAsync("https://pastebin.com/raw/A8hgfe3A")
```

***

## Save Instance 

```lua
<table> Krnl.SaveInstance
```

Returns a table of settings and functions related to Save Instance.
You can edit some of these options to change Save Instance's settings.

| Name                 | Type     | Description                                                   |
| -------------------- | -------- | ------------------------------------------------------------- |
| SavePlayer           | Boolean  | If enabled, character instances will be saved.                |
| DecompileScripts     | Boolean  | If enabled, scripts will be decompiled.                       |
| EscapeForm           | Function | no clue                                                       |
| CacheScripts         | Function | supposed to cache scripts                                     |
| \_scriptCache        | Table    | A table of all scripts that have been cached.                 |
| Save                 | Function | An alias for saveinstance().                                  |
| SaveRemovedInstances | Boolean  | If enabled, instances that are parented to nil will be saved. |
| BufferSize           | Number   | idk tbh                                                       |

### Example 

```lua
local s = Krnl.SaveInstance

s.SavePlayer = false
s.DecompileScripts = true
s.SaveRemovedInstances = false

Krnl.SaveInstance.Save() -- or saveinstance()
```
