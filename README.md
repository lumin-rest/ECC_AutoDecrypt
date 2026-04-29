# [Project: Bronze Forever](https://bronzeforever.net/) - ECC Runtime Decryption

Runtime decoder for Bronze Forever's ECC packet layer. Hooks Curve25519 ECDH exchange, ChaCha20 encryption, HMAC-SHA256 integrity, and ephemeral Schnorr signing to capture session keys and log plaintext traffic in real time. 

> [!WARNING]
> This requires your executor support the following functions: `getupvalues`, `getgenv`, `getloadedmodules`.

## Instructions

1. Create a new file in your executor's auto execute folder. (Ex: `ECC_AutoDecrypt.lua`)
2. Copy and paste the loadstring into the file, and save.

```lua
loadstring(game:HttpGet(
  "https://github.com/lumin-rest/ECC_AutoDecrypt/blob/main/main.lua?raw=true"
))()
```

3. Join Bronze Forever as usual, then launch lumin.

## Public ECC_Forge API

```lua
getgenv().PBF_REMOTE_FUNCTION
getgenv().PBF_REMOTE_EVENT
```

```lua
--[[
getgenv().ECC_Forge.sendPacket(
    Sender: <RemoteEvent/RemoteFunction>,
    Args: <Table>
)
]]

-- Example:
getgenv().ECC_Forge.sendPacket(getgenv().PBF_REMOTE_FUNCTION, {
    "PDS", "saveGameClient", {
        options = {
            tSpeed           = true,
            bagEnabled       = false,
            autosaveEnabled  = true,
            musictype        = 1,
            reduceGraphics   = false,
            lastUnstuckTick  = 0,
        },
        expShareOn = false,
    }
})
```
