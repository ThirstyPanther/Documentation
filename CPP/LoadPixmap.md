# LoadPixmap

This function loads a pixmap from a file path or stream.

## Syntax

- shared_ptr<[Pixmap](Pixmap.md)\> LoadPixmap(const [WString](WString.md)& path, const int miplevel = 0, const int face = 0, const [LoadFlags](Constants.md#LoadFlags) flags = LOAD_DEFAULT)
- shared_ptr<[Pixmap](Pixmap.md)\> LoadPixmap(shared_ptr<[Stream](Stream.md)\>, const int miplevel = 0, const int face = 0, const [LoadFlags](Constants.md#LoadFlags) flags = LOAD_DEFAULT)

| Parameter | Description |
|---|---|
| path | file path to load the pixmap from |
| stream | stream to load the pixmap from |
| miplevel | optional mipmap level to load |
| face | optional texture face to load |
| flags | optional load flags |

## Returns
Returns the loaded pixmap, or NULL if no pixmap was loaded.

## Example

```c++
#include "UltraEngine.h"

using namespace UltraEngine;

int main(int argc, const char* argv[])
{
    //Get the displays
    auto displays = GetDisplays();

    //Create window
    auto window = CreateWindow("Ultra Engine", 0, 0, 800, 600, displays[0]);

    //Create user interface
    auto ui = CreateInterface(window);

    //Create a pixmap
    auto pixmap = LoadPixmap("https://raw.githubusercontent.com/Leadwerks/Documentation/master/Assets/Materials/Ground/dirt01.dds");

    //Show the pixmap
    ui->root->SetPixmap(pixmap);

    while (true)
    {
        const Event ev = WaitEvent();
        switch (ev.id)
        {
        case EVENT_WINDOWCLOSE:
            return 0;
            break;
        }
    }

    return 0;
}
```
