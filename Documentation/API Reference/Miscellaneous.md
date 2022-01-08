# Miscellaneous Functions
---

24

## Set Clipboard

```lua
<void> setclipboard(<string> Content)
```

Sets `Content` to the clipboard.

***

## Set Fast Flag

```lua
<void> setfflag(<string> Flag, <string> Value)
```

Sets `Flag`'s value to `Value`.
You can find a list of all Fast Flags [here](https://fflag.eryn.io).

### Example

```lua
setfflag("AbuseReportScreenshot","False")
```

:::hint
## Note

You must execute this before the game loads.
Use Auto-Execute + Auto-Attach.
:::

***

## Get Custom Asset

```lua
<string> getcustomasset(<string> Path)
```

Returns a string that can be used as a fake Asset ID for GUI elements.

### Example

```lua
writefile("dog.png", game:HttpGet("https://i.imgur.com/aVEAmYC.png")) -- Creates a png in the workspace folder
local ScreenGui = Instance.new("ScreenGui", game.CoreGui)
local ImageLabel = Instance.new("ImageLabel", ScreenGui)
ImageLabel.AnchorPoint = Vector2.new(0.5, 0.5)
ImageLabel.Position = UDim2.new(0.5, 0, 0.5, 0)
ImageLabel.Size = UDim2.new(0, 250, 0, 250)
ImageLabel.Image = getcustomasset("dog.png")
print(getcustomasset("dog.png"))
```

### Supported Classes & File Types

| Class                | File Type      |
| -------------------- | -------------- |
| ImageLabel           | PNG, JPG, JPEG |
| ImageButton          | PNG, JPG, JPEG |
| ImageHandleAdornment | PNG, JPG, JPEG |
| Decal                | PNG, JPG, JPEG |
| Texture              | PNG, JPG, JPEG |
| Trail                | PNG, JPG, JPEG |
| Sky                  | PNG, JPG, JPEG |
| VideoFrame           | WEBM           |
| Sound                | MP3, OGG       |

***

## Get Special Info

```lua
<table> getspecialinfo(<Instance> Object)
```

Returns a table of special properties for `MeshParts`, `UnionOperations`, and `Terrain` Instances.

| MeshParts   | UnionOperations | Terrain        |
| ----------- | --------------- | -------------- |
| InitialSize | FormFactor      | SmoothGrid     |
| PhysicsData | AssetId         | MaterialColors |
|             | InitialSize     |                |
|             | ChildData       |                |
|             | MeshData        |                |
|             | PhysicsData     |                |

***

## Message Box

```lua
<uint> messagebox(<string> Text, <string> Title, <uint> Flag)
```

Creates a message box.

### Flags

| Flag                          | Value |
| ----------------------------- | ----- |
| OK                            | 0     |
| OK / Cancel                   | 1     |
| Abort / Retry / Ignore        | 2     |
| Yes / No / Cancel             | 3     |
| Yes / No                      | 4     |
| Retry / Cancel                | 5     |
| Cancel / Try Again / Continue | 6     |

### Return Values

| Value | Description            |
| ----- | ---------------------- |
| 1     | OK was clicked.        |
| 2     | Cancel was clicked.    |
| 3     | Abort was clicked.     |
| 4     | Retry was clicked.     |
| 5     | Ignore was clicked.    |
| 6     | Yes was clicked.       |
| 7     | No was clicked.        |
| 10    | Try Again was clicked. |
| 11    | Continue was clicked.  |

### Example

```lua
local msgbox = messagebox("press yes for robux","Robux Generator",4)
if msgbox == 6 then
    print("free robux")
elseif msgbox == 7 then
    print("no robux")
end
```

***

## Get Objects

```lua
<table> game:GetObjects(<string> AssetId)
```

Returns a table of all objects for the specified `AssetId`.

### Example

```lua
print(game:GetObjects("rbxassetid://3567096419")[1].Name)
```

***

## Queue On Teleport

```lua
<void> queue_on_teleport(<string> Code)
```

Executes `Code` after the local player is teleported.

### Example 

```lua
queue_on_teleport('print("teleported")')
game:GetService("TeleportService"):TeleportToPlaceInstance(game.PlaceId, game.JobId)
```

***

## Request

```lua
<table> request(<table> Options)
<table> http_request(<table> Options)
```

Creates an HTTP request with `Options`.

### Krnl Headers 

| Header           | Description             |
| ---------------- | ----------------------- |
| User-Agent       | An identifier for Krnl. |
| Krnl-Hwid        | The user's Hardware ID. |
| Krnl-Fingerprint | Alias for Krnl-Hwid.    |

### Request Fields 

| Name    | Type       | Required | Description                                                            |
| ------- | ---------- | -------- | ---------------------------------------------------------------------- |
| Url     | String     | Yes      | The target URL for this request. Must use&#xA;HTTP or HTTPS protocols. |
| Method  | String     | No       | The HTTP method being used.&#xA;GET, POST, HEAD, etc.                  |
| Headers | Dictionary | No       | A dictionary of headers to be used.                                    |
| Cookies | Dictionary | No       | A dictionary of cookies to be used.                                    |
| Body    | String     | No       | The request body.                                                      |

### Response Fields 

| Name          | Type    | Description                                    |
| ------------- | ------- | ---------------------------------------------- |
| Success       | Boolean | The success status of the request.             |
| StatusCode    | Integer | The HTTP status code of the request.           |
| StatusMessage | String  | The HTTP status code converted to string form. |
| Headers       | Table   | The response headers of the request.           |
| Cookies       | Table   | The response cookies of the request.           |
| Body          | String  | The requested content.                         |

### Example

```lua
local response = request({
    Url = "https://krnl.ca",
    Method = "GET", -- Optional | GET, POST, HEAD, etc
    Headers = {}, -- Optional | HTTP Headers
    Cookies = {} -- Optional | HTTP Cookies
})
print(response.Success)
```

***

## Set Parent Internal 

```lua
<void> setparentinternal(<Instance> Object, <Instance> Parent)
```

Internally sets the parent of `Object` to `Parent` without firing any signals.

***

## Add Child Internal 

```lua
<void> addchildinternal(<Instance> Parent, <Instance> Object)
```

Internally adds `Object` to `Parent` without firing any signals.

### Example 

```lua
addchildinternal(workspace,Instance.new("Part"))
```

***

## Identify Executor

```lua
<string> identifyexecutor(<void>)
```

Returns `Krnl` if the current executor is Krnl.

***

## Krnl Loaded

```lua
<bool> KRNL_LOADED
```

A variable that determines if the current executor is Krnl.

***

## Get Hidden UI

```lua
<Instance> gethui(<void>)
<Instance> hiddenUI(<void>)
```

Returns a holder made for GUI's to be parented in.

```lua
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Parent = gethui()
```

***

## Is Luau

```lua
<bool> isluau(<void>)
```

Returns true if the current game is using Luau.
This function is deprecated and will always return true as all games use Luau.

***

## Set FPS Cap

```lua
<void> setfpscap(<uint> Cap)
```

Sets the fps cap to `Cap`.

:::hint
## Note

Setting the fps cap to *math.huge* will freeze your game.
:::

***

## Run Secure 

```lua
<void> run_secure(<string> Encrypted)
```

Loads `Encrypted` as a chunk.

:::hint
## Note

This is most likely Krnl's version of Synapse's secure lua. (syn.run_secure_function)
:::

***

## Run Auto Execute Scripts 

```lua
<void> run_auto_execute_scripts(<void>)
```

Executes all scripts that are in your autoexec folder.

***

## Run Teleport Queue Scripts 

```lua
<void> run_teleport_queue_scripts(<void>)
```

Executes all scripts that have been created with `queue_on_teleport`. 

### Example 

```lua
queue_on_teleport('print("bruh")')
run_teleport_queue_scripts() -- Prints "bruh"
run_teleport_queue_scripts() -- Does not print since the script has ran already
```

:::hint
## Note

This removes your queue on teleport scripts so you will need to call queue on teleport again.
:::

***

## Get Network Mode 

```lua
<int> getnetworkmode(<void>)
```

Returns the current network mode.

***

## Set Network Mode 

```lua
<void> setnetworkmode(<int> Mode)
```

Sets the current network mode to `Mode`.

***

## Luau Compile 

```lua
<string> luau_compile(<string> String)
```

Returns a Luau compiled version of `String`.

***

## Luau Load 

```lua
<void> luau_load(<string> Compiled)
```

Loads a Luau compiled string as a chunk.

### Example 

```lua
luau_load(luau_compile('print("hey")'))
```

***

## Handle Teleport 

```lua
<void> HANDLE_TELEPORT(<void>)
```

handles a teleport???? idk lol

***

## Safe Call 

```lua
<variant> KRNL_SAFE_CALL(<function> f, <variant?> Args...)
```

Calls function `f` with `Args` with a fake `LocalScript`.

:::hint
## Warning

I think this is supposed to be like *syn.secure_call*, but clearly isn't secure at all.
:::
