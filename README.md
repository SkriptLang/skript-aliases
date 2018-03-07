# Skript Aliases
## Work In Progress
Development of aliases will start in coming days/weeks. At the moment, there
are some things in Skript that may require changes.

These are the new aliases for Skript, currently work in progress. If you are
looking for the plugin, you should go to the main
[repository](https://github.com/bensku/Skript).

## Structure of Aliases
Aliases are laid out in multiple subfolders and files inside them. In each file,
they are put in *sections*, like code in scripts is put to triggers. Names for
sections should be descriptive and unique per-file, but other than that they do
not matter much.

In sections, most of lines will define new aliases. The basic format is quite
simple, actually:
```
carrot¦s = minecraft:carrot
```
The strange character, ¦, tells where the difference between singular and plural
is. In this case: *carrot*, *carrots*

For figuring out the ids, [Minecraft Wiki](https://minecraft.gamepedia.com/Minecraft_Wiki)
is probably the best place. Alternatively, you can see them ingame if you use
F3+H.

### Multiple Items and Other Aliases
Aliases may refer to multiple items by separating them with commas. They can
also refer to other aliases, which have been loaded before. For example:
```
food = minecraft:potato, carrot
```
(refers to minecraft:item_id and minecraft:some_item)

### Name Patterns
Alias names can contain optional parts and "choose one" parts. They work
similarly with Skript's syntax patterns:
```
[vegan] food = minecraft:potato, carrot # Optional part
(vegetables|food) = minecraft:potato, carrot # Choose one
```
Spaces after and before optional parts are mostly ignored. Leave them outside
of the optional parts.

### (NBT) Tags
Aliases can define NBT tags to apply for items. The tags should be in Mojang's
JSON format that Vanilla commands such as /give use. Tags are put after item
id, separated with a space:
```
mundane potion = minecraft:potion {"Potion": "minecraft:mundane"}
```
If there are multiple ids defined for an alias, each of them can have their
own tags specified before the next id is given.

### Variations
Sometimes, there are multiple items that are quite similar, but still have
some differences. For example potions are like this: they all share an id, but
have their own tags.

WIP - documenting this and rest of features is yet to be done

## Developing Aliases (for experienced developers)
1. Fork if you don't have write access
2. Clone this in plugins/Skript, rename cloned folder to just *aliases*
3. Make your changes in correct files and folders
4. Use a text editor to modify aliases
5. Test using Spigot/Paper and Skript, without any addons
6. Open a pull request or push to this repo

## Developing Aliases (for newbies)
Since working on aliases is easy, some of you might not be familiar with Git
or Github, but still want to help. I've written this guide to make it a bit
easier.

### What you need
To contribute to aliases, you will need:

* A Git client
  * Windows/Mac: get it from their [website](https://git-scm.com/)
  * Linux: use your distro to install it
  * A tutorial can be found [here](https://guides.github.com/introduction/git-handbook/)
* A text editor
  * Anything that you use to edit scripts will do
* A Github Account
* A Minecraft server for testing
  * Skript (currently a development build; *published soon*)
  * Spigot or Paper
  * No addons

### Setting Everything Up
Got them? Good. Now, go edit your config.sk in plugins/Skript. To end of the
of the file, add:
```
load default aliases: false
```
Default aliases from Skript's jar or packed aliases will not be used. Instead,
you will get the latest version of them using Git.

[Fork](https://guides.github.com/activities/forking/) this repository, unless
you have write access. Clone your forked repository in plugins/Skript. Rename
the produced folder from *skript-aliases* to just aliases.

### What Now?
If you have something you want to do, good. If not, you can check issues in
this repository to find out something you'd like to work on.

When know *what* you want to do, it is time to familiarize yourself with
the structure of aliases. Where is it what you want to change? Does it require
a new file, or would it be a simple modification or addition to an existing one?
Read the comments in files; they will usually describe their contents. If you
make your own file, add it to a correct folder and comment it similarly.

You can, and must, test your changes using Skript. Basically, reload aliases
a lot while you do your changes. Log in to the server and give items to you to
make sure your aliases work correctly. Commit using Git and push to your fork
when you get something done.

When it is all ready, open a pull request. Your change will be reviewed, and
if everything goes well, soon added to Skript's default aliases.
