# Websocket Library
---

1

## Connect 

```lua
<table> Krnl.WebSocket.connect(<string> Url)
<table> WebSocket.connect(<string> Url)
```

Attempts to connect to `Url`.

***

## Methods

### Send 

```lua
<void> Socket:Send(<string> Message)
```

Sends `Message` to `WebSocket`.

### Close 

```lua
<void> Socket:Close(<void>)
```

Closes the connection.

***

## Events

### On Message 

```lua
<RBXScriptSignal> Socket.OnMessage
```

Fires when the server sends a message.

### On Close 

```lua
<RBXScriptSignal> Socket.OnClose
```

Fires when the connection closes.

***

## Properties

### Connected 

```lua
<bool> Socket._connected
```

A boolean that determines if the websocket is connected.

***

## Headers

| Header           | Description             |
| ---------------- | ----------------------- |
| User-Agent       | An identifier for Krnl. |
| Krnl-Hwid        | The user's Hardware ID. |
| Krnl-Fingerprint | An alias for Krnl-Hwid. |

***

## Example 

Try testing websockets [here](https://www.piesocket.com/websocket-tester)!

```lua
local socket = Krnl.WebSocket.connect("wss://demo.piesocket.com/v3/channel_1?api_key=oCdCMcMPQpbvNjUIzqtvF1d2X2okWpDQj4AwARJuAgtjhzKxVEjQU6IdCjwm&notify_self=1")

socket.OnMessage:Connect(function(msg)
    print(msg)
end)
socket.OnClose:Connect(function()
    warn("Connection was closed")
end)

socket:Send("yo")
task.wait(3)
socket:Close()
```
