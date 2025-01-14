# CreateTerrain

This function creates a new terrain entity.

## Syntax

- shared_ptr<[Terrain](Terrain.md)\> **CreateTerrain**(shared_ptr<[World](World.md)\> world, const int width, const int height)
- shared_ptr<[Terrain](Terrain.md)\> **CreateTerrain**(shared_ptr<[World](World.md)\> world, const [iVec2](iVec2.md) resolution)

| Parameter | Description |
|---|---|
| world | world to create the terrain in |
| resolution, (width, height) | number of terrain points on each axis |

## Example

```c++
#include "UltraEngine.h"

using namespace UltraEngine;

int main(int argc, const char* argv[])
{
    //Get the displays
    auto displays = GetDisplays();
   
    //Create a window
    auto window = CreateWindow("Ultra Engine", 0, 0, 1280, 720, displays[0], WINDOW_CENTER | WINDOW_TITLEBAR | WINDOW_CLIENTCOORDS);
    
    //Create a framebuffer
    auto framebuffer = CreateFramebuffer(window);
    
    //Create a world
    auto world = CreateWorld();

    //Create a camera
    auto camera = CreateCamera(world);
    camera->SetFOV(70);
    camera->SetClearColor(0.125);
    camera->SetRotation(45, 0, 0);
    camera->Move(0, 0, -500);
    
    //Create a light
    auto light = CreateDirectionalLight(world);
    light->SetRotation(45, 45, 0);
    
    //Create terrain
    auto terrain = CreateTerrain(world, 1024);
    terrain->LoadHeightmap("https://raw.githubusercontent.com/Leadwerks/Documentation/master/Assets/Terrain/1024.r16");
    terrain->SetScale(1, 300, 1);
    terrain->SetPosition(0,-100,0);

    //Main loop
    while (window->Closed() == false and window->KeyDown(KEY_ESCAPE) == false)
    {
        world->Update();
        world->Render(framebuffer);
    }
    return 0;
}
```
