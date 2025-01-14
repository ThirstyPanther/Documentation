# Scripting

Ultra Engine supports scripts written with the [Lua](https://www.lua.org) programming language.
Scripts can be attached to entities or used to control the entire program.
You can even combine Lua scripts with C++ and C# programs.

To bind C++ classes and functions to Lua, we use the [sol2](https://github.com/ThePhD/sol2) library. You can use this to call Lua functions from C++ or expose your C++ classes and functions to Lua.

## Functions

| Name | Type | Description |
|-----|-----|-----|
| [ExecuteString](ExecuteString.md) | Function | |
| [RunScript](RunScript.md) | Function | |
| [LuaState](LuaState.md) | Function | |
| [SandboxLua](SandboxLua.md) | Function | |
