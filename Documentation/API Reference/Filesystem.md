# Filesystem Functions
---

12

## Write File

```lua
<void> writefile(<string> Path, <string> Content)
```

Writes `Content` to the supplied `Path`.

### Example

```lua
writefile("robux.txt","unlimited robux")
```

***

## Read File

```lua
<string> readfile(<string> Path)
```

Returns the contents of the file located at `Path`.

### Example

```lua
print(readfile("robux.txt")) -- Prints the contents of robux.txt
```

***

## Append File

```lua
<void> appendfile(<string> Path, <string> Content)
```

Appends `Content` to the file contents at `Path`.

***

## Load File

```lua
<variant> loadfile(<string> Path)()
```

Loads the contents of the file located at `Path` as a chunk and returns it.

***

## Do File

```lua
<variant> dofile(<string> Path)
```

Loads the contents of the file located at `Path` as a chunk and returns it.

***

## List Files

```lua
<table> listfiles(<string> Folder)
```

Returns a table of all files in `Folder`.

***

## Is File

```lua
<bool> isfile(<string> Path)
```

Returns true if `Path` is a file or not.

***

## Is Folder

```lua
<bool> isfolder(<string> Path)
```

Returns true if `Path` is a folder or not.

***

## Make Folder

```lua
<void> makefolder(<string> Path)
```

Creates a new folder at `Path`.

***

## Zip Inflate 

```lua
<table> zip_inflate(<string> Path)
```

Returns a table of all files in the specified zip folder.

### Example 

```lua
for i,v in pairs(zip_inflate("Zip.zip")) do
    print(i,v)
end
```

***

## Delete Folder

```lua
<void> delfolder(<string> Path)
```

Deletes the folder located at `Path`.

***

## Delete File

```lua
<void> delfile(<string> Path)
```

Deletes the file located at `Path`.

***

### Example: Reading the contents of a file within a folder

```lua
makefolder("lol")
writefile("lol\\hi.txt","hello")
print(readfile("lol\\hi.txt")) -- hello
```
