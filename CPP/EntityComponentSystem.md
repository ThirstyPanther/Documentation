# Entity Component System

The Ultra Engine Entity Component System is a high-level system for developing games and simulations. The component system is designed to meet the following goals:

- Allow addition of modular logical components without increasing the overall complexity of the program.
- Support for saving and loading of user-defined objects and game states.
- Facilitate emergent behavior as a result of component interaction.

The entity component system consists of internal engine elements combined with a [preprocessor](https://github.com/UltraEngine/Preprocessor) that generates code for your game. The type of components that are available will vary depending on what code files you have present in your project directory.

### Actors

In the core Ultra Engine API you are accustomed to using entities. In the entity component system, the [Actor](Actor.md) is our main object type. The actor poseesses an entity as and additional modular "blocks" of behavior called components.

### Components

[Components](Component.md) are blocks of functionality that can be added to an actor. An actor can have multiple components, but only one component of each type.

### Usage

To start using the entity component system, create an actor:

```c++
auto actor = CreateActor(entity);
```

You can add components to the actor like this:

```c++
actor->AddComponent<Mover>();
```

You can call any methods of any components, and all component methods by the same name will be called:

```c++
actor->Kill();
```

You also can call a method for just one specific component, but it is generally better to call the actor method so that all components are have this method called:

```c++
actor->GetComponent<PlayerController>()->Kill();
```

You can access members of an individual component:

```c++
actor->GetComponent<PlayerController>()->health = 99;
```

You can also call a method to set a value, and this will call the same method for each component that has it:

```c++
actor->SetHealth(99);
```

You can copy an actor. The entity will be instantiated and all components will be copied to the new actor, with their current properties intact:

```c++
auto actor2 = actor->Copy();
```

The entity component system works together with the [Scene](Scene.md) system to save your entity components to a file and load them back into the program. This can be used for game saves or serializing the game state to send over a network to another player.
