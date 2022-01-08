# Console Functions
---

8

## Print

```lua
<void> rconsoleprint(<string> Text)
```

Prints `Text` into the console. `rconsoleprint` also supports colors.

***

## Info

```lua
<void> rconsoleinfo(<string> Text)
```

Prints `Text` into the console, with `[INFO]` written before it.

***

## Warn

```lua
<void> rconsolewarn(<string> Text)
```

Prints `Text` into the console, with `[WARNING]` written before it.

***

## Error

```lua
<void> rconsoleerr(<string> Text)
```

Prints `Text` into the console, with `[ERROR]` written before it.

***

## Clear

```lua
<void> rconsoleclear(<void>)
```

Clears all text from the console.

***

## Name

```lua
<void> rconsolename(<string> Title)
```

Sets the console's title to `Title`.

***

## Input

```lua
<string> rconsoleinput(<void>)
```

Yields until the user inputs information and presses Enter. Returns the input they put in.

***

## Close Console

```lua
<void> rconsoleclose(<void>)
```

Closes the console.

***

## Console Colors

| Color         | Code              |
| ------------- | ----------------- |
| Black         | @@BLACK@@         |
| Blue          | @@BLUE@@          |
| Green         | @@GREEN@@         |
| Cyan          | @@CYAN@@          |
| Red           | @@RED@@           |
| Magenta       | @@MAGENTA@@       |
| Brown         | @@BROWN@@         |
| Light Gray    | @@LIGHT_GRAY@@    |
| Dark Gray     | @@DARK_GRAY@@     |
| Light Blue    | @@LIGHT_BLUE@@    |
| Light Green   | @@LIGHT_GREEN@@   |
| Light Cyan    | @@LIGHT_CYAN@@    |
| Light Red     | @@LIGHT_RED@@     |
| Light Magenta | @@LIGHT_MAGENTA@@ |
| Yellow        | @@YELLOW@@        |
| White         | @@WHITE@@         |

![Color Preview](https://cdn.discordapp.com/attachments/775967135746621463/922084051194634240/image_1.png)

### Example

```lua
rconsolename("console") -- Sets the name of the console to "console"
rconsoleprint("gamer\n")
rconsoleprint("@@YELLOW@@") -- Changes the text color to Yellow
rconsoleprint("gamer but yellow\n")
rconsoleerr("error occurred!")
rconsolewarn("warning text")
wait(3)
rconsoleclear() -- Clears all text
wait(1)
rconsoleclose() -- Closes the console
```

:::hint
## Note

You must use \n at the end of rconsoleprint to make a new line.
rconsoleinfo, rconsolewarn, and rconsoleerr do this automatically.
:::

### Example: Krnl Key Checker

```lua
function key(color)
    rconsoleprint("[")
    rconsoleprint("@@"..color.."@@")
    rconsoleprint("KEY")
    rconsoleprint("@@LIGHT_GRAY@@")
    rconsoleprint("]")
end
function getversion()
    local ver = game:HttpGet("https://cdn.krnl.ca/version.txt"):split("")
    return "v"..ver[1].."."..ver[2].."."..ver[3]..ver[4]..ver[5]:lower()
end
function checkingkey()
    rconsolename("krnl "..getversion())
    key("GREEN")
    rconsoleprint(" Please enter your key: ")
    local input = rconsoleinput()
    key("GREEN")
    rconsoleprint(" Checking key. (this might take some time..\n")
    if input == "key" or input == game:HttpGet("https://cdn.krnl.ca/getkey.php"):split('value="')[2]:split('" placeholder')[1] then
        key("GREEN")
        rconsoleprint(" Correct key!\n")
        wait(0.7)
        rconsoleclose()
    else
        key("RED")
        rconsoleprint(" Incorrect key!\n")
        checkingkey()
    end
end
function inject()
    rconsoleclear()
    rconsoleinfo("Checking version.")
    wait(0.7)
    rconsoleinfo("Scanning.")
    wait(1)
    key("GREEN")
    rconsoleprint(" Please get a key here: https://cdn.krnl.ca/getkey.php\n")
    checkingkey()
end
inject()
```
