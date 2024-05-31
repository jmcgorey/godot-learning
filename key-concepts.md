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

#### Secenes, Detailed

A scene is a set of nodes organized into a tree. Once saved, scenes work like new node types in the editor. You can use them as childs of existing nodes. If used in this context, the instance of the scene appears as a single node with its internals hidden.

Scenes are a vehicle to allow you to structure your game's code however you want. You can create new and complex node types by composing nodes together.

Some examples:

-   A game character that runs and jumps,
-   A life bar,
-   A chest you can interact with

The Godot editor is essentially a scene editor. A project can contain as many scenes as you need, but the engine only requires one as its main scene. This will be loaded first, and then the tree is used from there.

Scenes have the characteristics of nodes, but also these ones as well:

-   They always have one root node, like the "Player" example
-   You can save them to your local drive and load them later
-   You can create as many instances of a scene as you'd like. You can have five or ten characters in your game, created from your Character scene
    -   And, if you update the scene model, all instances of the scene are updated as well

#### Scene file extensions

Scenes are saved as files somewhere within your project directory. "Where" exactly is up to you. In an example on the site, with a scene containing just a `Label` node, it was saved as a `label.tscn` file. `.tscn` stands for "text scene". This specific example file is called a "Packed Scene", since it packs information about the scene's content.

#### Instancing

Once you have saved a scene, it works as something of a blueprint. You can reproduce it in other scenes as many times as you'd like. Replicating an object from a template like this is called **instancing**

Take, for example, creating a `Ball` scene. When you instance a Ball, you only see the Ball node. You don't see the innards of the Ball. Also, each instance has a unique name.

Finally, every instance of the `Ball` starts with the same structure and properties of the scene saved in `ball.tscn`. However, you can modify each independently by changing properties exposed by the source scene.

#### Editing Scenes and Instances

The instancing system allows us to edit a scene in two ways. Using the Ball example from above, we can:

-   Change the properties of just one Ball without affecting the others by using the Inspector
    -   Changing a property on an instance **always** overrides values from the corresponding packed scene.
    -   If you change a property on an instance, a "revert" button will appear next to the property. Clicking it will restore the value of the property to the one specified by the saved scene.
-   Change the default properties of _every_ Ball by opening the `ball.tscn` scene and making a change there. Upon saving, all instances of the Ball in the project will see their values update.

#### Thinking of scenes as a design language

Image the elements that players will see in your game, and structure your code around them.

For example, see the breakdown of a shooter game [here](https://docs.godotengine.org/en/stable/getting_started/step_by_step/instancing.html#scene-instances-as-a-design-language).

It has all of the familar elements:

-   Player
-   Enemy
-   Weapon
-   Obstacle
-   HUD
-   Stage

You can come up with a diagram like this for almost any type of game. Look on the Godot docs site for a more in-depth explanation for this particular diagram.

Once you have built your diagram, create a scene for each element listed in it to develop your game. You'll use instancing (either by code or right in the editor) to build your scene tree.

In the link above, there is also an example scene diagram for an open-world game with a lot of assets and nested elements. Take some time to look at that.

Using this scene-building methodology, it is easy to iterate on your game. All you need to do is create and instantiate more scenes.

The editor is designed to be accessible to programmers, designers, and artists. A team working on a game can include all sorts of people, like 2D or 3D artists, level designers, game designers, and animators, all working with the Godot editor.

#### Scenes & Instancing Summary

Overall, the scene system gives you:

-   The ability to divide your game into reusable components
-   A tool to structure and encapsulate complex systems
-   A language to think about your game project's structure in a natural way

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

#### Node, Detailed

All nodes have the following characteristics:

-   A name
-   Editable Properties
-   They receive callbacks to update every frame
-   You can extend them with new properties and functions
-   You can add them to another node as a child
    -   This lets us form a tree from the nodes, which is used to organize projects

Combining nodes produces more complex behavior. Like the character example above, each node brings something different to the table.

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
