# Widget::Draw

This method is called each time the widget is redrawn.

## Syntax

- void **Draw**(const int x, const int y, const int width, const int height)

| Parameter | Description |
|---|---|
| x | x screen coordinate of drawn area |
| y  | y screen coordinate of drawn area |
| width | width of the drawn area |
| height | height of the drawn area |

## Remarks

This is a protected virtual method. It can only be used by declaring it in a custom widget.
