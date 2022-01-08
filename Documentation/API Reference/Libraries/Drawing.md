# Drawing Library
---

2

## New Drawing 

```lua
<userdata> Drawing.new(<string> Class)
```

Returns a new Drawing object with `Class`.

## Clear Drawings 

```lua
<void> Drawing.clear(<void>)
<void> Drawing.Clear(<void>)
```

Removes all Drawing objects.

***

## Fonts 

| Font      | Value |
| --------- | ----- |
| UI        | 0     |
| System    | 1     |
| Plex      | 2     |
| Monospace | 3     |

![Font Preview](https://i.imgur.com/PSBpdpJ.png)

***

## Base Properties 

| Name         | Type     |
| ------------ | -------- |
| Visible      | Boolean  |
| Transparency | Number   |
| Color        | Color3   |
| \:Remove     | Function |
| \:Destroy    | Function |
| ZIndex       | Integer  |

:::hint
## Notes

*   These properties apply to all Drawing objects.

*   Transparency is the opposite than on normal GUI elements. 1 means fully opaque while 0 means fully transparent.
:::

***

## Drawing Classes & Properties

:::hint
### Note

\*​ indicates a read-only property

\*\*​ indicates a write-only property
:::

### Line

| Name      | Type    |
| --------- | ------- |
| Thickness | Number  |
| From      | Vector2 |
| To        | Vector2 |

### Text 

| Name          | Type          |
| ------------- | ------------- |
| Text          | String        |
| Size          | Number        |
| Center        | Boolean       |
| Outline       | Boolean       |
| OutlineColor  | Color3        |
| Position      | Vector2       |
| TextBounds\*​ | Vector2       |
| Font          | Drawing.Fonts |

### Image 

| Name      | Type    |
| --------- | ------- |
| Data\*\*​ | String  |
| Size      | Vector2 |
| Position  | Vector2 |
| Rounding  | Number  |

:::hint
## Notes

Data does NOT refer to the URL of the image. You must grab the image data yourself with game\:HttpGet, then assign that to Data.
:::

### Circle 

| Name      | Type    |
| --------- | ------- |
| Thickness | Number  |
| NumSides  | Number  |
| Radius    | Number  |
| Position  | Vector2 |
| Filled    | Boolean |

### Square 

| Name      | Type    |
| --------- | ------- |
| Thickness | Number  |
| Size      | Vector2 |
| Position  | Vector2 |
| Filled    | Boolean |

### Quad 

| Name      | Type    |
| --------- | ------- |
| Thickness | Number  |
| PointA    | Vector2 |
| PointB    | Vector2 |
| PointC    | Vector2 |
| PointD    | Vector2 |
| Filled    | Boolean |

:::hint
## Note

PointA = Top Right
PointB = Top Left
PointC = Bottom Left
PointD = Bottom Right
:::

### Triangle 

| Name      | Type    |
| --------- | ------- |
| Thickness | Number  |
| PointA    | Vector2 |
| PointB    | Vector2 |
| PointC    | Vector2 |
| Filled    | Boolean |

### Example

```lua
local Line = Drawing.new("Line")
Line.Visible = true
Line.Transparency = 1
Line.Color = Color3.fromRGB(255,255,255)
Line.From = Vector2.new(0,0)
Line.To = Vector2.new(400,200)
Line.Thickness = 1

local Text = Drawing.new("Text")
Text.Visible = true
Text.Transparency = 1
Text.Color = Color3.fromRGB(255,255,255)
Text.Text = "krln"
Text.Size = 18
Text.Center = true
Text.Outline = true
Text.OutlineColor = Color3.fromRGB(0,0,0)
Text.Position = Vector2.new(700,400)
Text.Font = Drawing.Fonts.System

local Image = Drawing.new("Image")
Image.Visible = true
Image.Transparency = 1
Image.Data = game:HttpGet("https://i.imgur.com/T80x8dv.png")
Image.Size = Vector2.new(128,128)
Image.Position = Vector2.new(130,130)
Image.Rounding = 0

local Circle = Drawing.new("Circle")
Circle.Visible = true
Circle.Transparency = 1
Circle.Color = Color3.fromRGB(255,255,255)
Circle.Thickness = 1
Circle.NumSides = 64
Circle.Radius = 100
Circle.Filled = false
Circle.Position = Vector2.new(400,400)

local Square = Drawing.new("Square")
Square.Visible = true
Square.Transparency = 1
Square.Color = Color3.fromRGB(255,255,255)
Square.Thickness = 1
Square.Size = Vector2.new(200,200)
Square.Position = Vector2.new(850,300)
Square.Filled = true

local Quad = Drawing.new("Quad")
Quad.Visible = true
Quad.Transparency = 1
Quad.Color = Color3.fromRGB(255,255,255)
Quad.Thickness = 1
Quad.PointA = Vector2.new(700,100)
Quad.PointB = Vector2.new(600,100)
Quad.PointC = Vector2.new(650,350)
Quad.PointD = Vector2.new(800,250)
Quad.Filled = false

local Triangle = Drawing.new("Triangle")
Triangle.Visible = true
Triangle.Transparency = 1
Triangle.Color = Color3.fromRGB(255,255,255)
Triangle.Thickness = 1
Triangle.PointA = Vector2.new(600,400)
Triangle.PointB = Vector2.new(500,700)
Triangle.PointC = Vector2.new(800,600)
Triangle.Filled = true

wait(10)
Drawing.clear()
```
