---
title: 'set_mouse_cursor_position'
weight: 200
---

{{% alert title="Beta feature" color="danger" %}}
`set_mouse_cursor_position` is available since Karabiner-Elements 13.5.1.
{{% /alert %}}

Move the mouse cursor to the specified point.

```json
{
    "to": [
        {
            "software_function": {
                "set_mouse_cursor_position": {
                    "x": 0,
                    "y": 0,
                    "screen": 0
                }
            }
        }
    ]
}
```

| Name     | Required     | Description                                     |
| -------- | ------------ | ----------------------------------------------- |
| `x`      | **Required** | The new mouse cursor position                   |
| `y`      | **Required** | The new mouse cursor position                   |
| `screen` | Optional     | The screen index of the new mouse cursor origin |

## Examples

Set the mouse cursor position to (0,0) of the second screen.

```json
{
    "to": [
        {
            "software_function": {
                "set_mouse_cursor_position": {
                    "x": 0,
                    "y": 0,
                    "screen": 1
                }
            }
        }
    ]
}
```