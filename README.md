# Perided UI Library

A dark, minimal Roblox UI library built for executors.

## Requirements

Requires an executor with `gethui()` and `syn.protect_gui()` support (e.g. Synapse X, KRNL, Fluxus).

## Loading

```lua
local Perided = loadstring(game:HttpGet("https://raw.githubusercontent.com/Goatofhells/Perciddd/refs/heads/main/testoetcid.txt"))()
```

## Creating a GUI

```lua
local gui = Perided("Title", "1.0")
```

| Parameter | Type | Description |
|-----------|------|-------------|
| title | string | Shown in the top bar |
| version | string | Shown below the title |

Returns a `gui` object.

---

## GUI: Adding Tabs

```lua
local tab = gui:AddTab(name, icon)
```

| Parameter | Type | Description |
|-----------|------|-------------|
| name | string | Tab label shown in the sidebar |
| icon | number | Asset ID for the tab icon (optional) |

Returns a `tab` object.

---

## Tab Elements

### Toggle

```lua
local toggle = tab:AddToggle(label, default, callback)
```

| Parameter | Type | Description |
|-----------|------|-------------|
| label | string | Text shown on the row |
| default | boolean | Starting state |
| callback | function(state: boolean) | Called when toggled |

```lua
toggle:Set(true)
toggle:Get() -- returns boolean
```

---

### Input

```lua
local input = tab:AddInput(label, placeholder, callback)
```

| Parameter | Type | Description |
|-----------|------|-------------|
| label | string | Text shown on the row |
| placeholder | string | Greyed-out hint text |
| callback | function(text: string, enterPressed: boolean) | Called on focus lost |

```lua
input:Set("hello")
input:Get() -- returns string
```

---

### Button

```lua
local btn = tab:AddButton(label, callback)
```

| Parameter | Type | Description |
|-----------|------|-------------|
| label | string | Button text |
| callback | function() | Called on click |

---

### Slider

```lua
local slider = tab:AddSlider(label, min, max, default, callback)
```

| Parameter | Type | Description |
|-----------|------|-------------|
| label | string | Text shown on the row |
| min | number | Minimum value |
| max | number | Maximum value |
| default | number | Starting value |
| callback | function(value: number) | Called on change |

```lua
slider:Set(50)
slider:Get() -- returns number
```

---

### Keybind

```lua
local keybind = tab:AddKeybind(label, default, callback)
```

| Parameter | Type | Description |
|-----------|------|-------------|
| label | string | Text shown on the row |
| default | KeyCode | Starting keybind |
| callback | function(key: KeyCode) | Called when key is changed |

```lua
keybind:Set(Enum.KeyCode.F)
keybind:Get() -- returns KeyCode
```

---

### Dropdown

```lua
local dropdown = tab:AddDropdown(label, options, default, callback)
```

| Parameter | Type | Description |
|-----------|------|-------------|
| label | string | Text shown on the row |
| options | table | Array of string options |
| default | string | Default selected option |
| callback | function(selected: string) | Called on selection |

```lua
dropdown:Set("Option A")
dropdown:Get() -- returns string
```

---

## Example

```lua
local Perided = loadstring(game:HttpGet("https://raw.githubusercontent.com/Goatofhells/Perciddd/refs/heads/main/testoetcid.txt"))()
local gui = Perided("MyScript", "2.0")

local main = gui:AddTab("Main", 123456789)

local esp = main:AddToggle("ESP", false, function(state)
    print("ESP:", state)
end)

local name = main:AddInput("Name", "Enter name...", function(text, enter)
    print("Name:", text)
end)

main:AddButton("Teleport", function()
    print("Teleport pressed")
end)

local speed = main:AddSlider("Speed", 0, 100, 16, function(val)
    print("Speed:", val)
end)

local mode = main:AddDropdown("Mode", {"Silent", "Loud", "Spinbot"}, "Silent", function(sel)
    print("Mode:", sel)
end)
```
