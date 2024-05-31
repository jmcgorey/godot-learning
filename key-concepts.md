# Key Concepts

## Godot Docs Link

https://docs.godotengine.org/en/stable/getting_started/introduction/key_concepts_overview.html

## Notes

In Godot:

-   A game is a tree of [nodes](#node), that you group together into scenes.
-   Nodes can communicate with eachother via signals

### Scene

A scene is a reusable group of [nodes](#node). It can be a character, a weapon, a menu, a house, a whole level, or anything really.

> Note: These fill the role of both "prefabs" and "scenes" from some other game engines

You can nest scenes! - Ex: put a character in a level, and drag and drop a scene as a child of it

### Node

A [scene](#scene) is composed of one or more nodes

Nodes are the building blocks of your game; you arrange them into trees.

An example of a character scene's nodes would be:

```
Player
|	Camera2D			# Provides the viewport that follows the player
|	Sprite2D			# Provides the image that is displayed for the character
|	CollisionShape2D	# Provides the physics the character uses to interact with the world
```

Godot provides many base node types that you can combine and extend to build more powerful ones. Most things will be done via 2D, 3D, or user interface nodes.

### Scene Tree

Used to organize all of your game's scenes.

### Signals

Emitted by [nodes](#node) when some event occurs. This allows you to make nodes communicate without hard-wiring them to eachother in code.

> Note: Signals are Godot's version of the observer pattern. Read more at: https://gameprogrammingpatterns.com/observer.html

Example:

-   Buttons emit a signal when pressed. You can connect this to run code, like starting the game or opening a menu.

-   Signals can tell you when two objects collided, when a character entered an area, and much more.

You can also define new signals tailored to your game.

### Summary

The four core concepts are:

-   nodes
-   scenes
-   the scene tree
-   and signals

You will work with these all the time.

Nodes are the game's smallest building blocks. You combine them to create scenes. You combine scenes and then nest them into the scene tree. You use signals to make nodes react to events in other nodes or different scene tree branches.
