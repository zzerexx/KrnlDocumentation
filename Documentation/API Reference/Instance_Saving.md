# Instance Saving Functions
---

2

## Save Instance 

```lua
<void> saveinstance(<void>)
```

Saves the current game into your workspace folder. 
Games are saved as `Game-Save-PlaceId`.

***

## Save Instance Settings 

The `saveinstance` function does not have any arguments. However, you can still change the settings with the `Krnl.SaveInstance` table.
Here are all the settings you can change:

| Name                 | Type    |
| -------------------- | ------- |
| SavePlayer           | Boolean |
| DecompileScripts     | Boolean |
| SaveRemovedInstances | Boolean |
| BufferSize           | Number  |

### Example 

```lua
Krnl.SaveInstance.DecompileScripts = true -- Enables script decompilation
saveinstance()
```

***

## Decompile 

```lua
<string> decompile(<LocalScript, ModuleScript> Script)
```

Returns the decompiled version of `Script`.

### Example 

```lua
setclipboard(decompile(LocalScript))
```
