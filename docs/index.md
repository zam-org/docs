# ZeroFrame Godot Documentation

Welcome to the ZeroFrame Godot documentation. ZeroFrame Godot is a plugin for the [Godot Engine](https://godotengine.org), a free and open-source game engine. ZeroFrame Godot allows your games to interact with [ZeroNet](https://zeronet.io), a peer-to-peer network that allows websites and user data to be stored across thousands of computers, rather than a single, potentially expensive centralized store. 

## What is ZeroFrame?

ZeroFrame is a plugin for Godot that one can import into their Godot game and use to move data to and from the ZeroNet network. ZeroNet itself is a program that runs on your computer, whereas ZeroFrame is just a way to communicate to ZeroNet from your Godot code.

While ZeroNet must be running somewhere for you to connect to the network, don't think that you'll need to start pushing your users to download it separately. Check out the [ZeroNet Godot Plugin](zeronet-godot.md) for quickly and easily adding a small ZeroNet instance right inside your game.

## What is ZeroNet?

[ZeroNet](https://zeronet.io) is a peer-to-peer network where websites and other data is hosted. It's similar to the regular internet, but on ZeroNet websites are not hosted by servers or the cloud. Rather, they are hosted by the users that visit them. This allows anyone to put up a ZeroNet website (or *zite*) and not worry about paying someone to keep it up, or whether the site happens to go down. As long as at least one of your users is online, the site itself is online, and in practice this practically means 100% of the time.

### What does this mean in terms of making games?

ZeroNet may be primarily for websites, but a website is just a collection of HTML, JavaScript, images and other things sitting together somewhere. Who's to say we can't store things like levels, high scores and achievements in the same place?

ZeroFrame handles transparently communicating with ZeroNet and provides easy-to-use function to save and retrieve user content, manage high scores, grant achievements and more! Take a look at the [ZeroFrame documentation](zeroframe-godot) for the details

## What is the Godot Engine?

The [Godot Engine](https://godotengine.org) is a free and open source game engine that's built by a community of volunteers. One does not need to worry about licenses or fees to use the engine, and the team's work and priorities are transparently shown on their [GitHub page](https://github.com/godotengine/godot).

The Godot Engine has a plugin system that works like libraries in programming languages. They allow you to import code that you otherwise would have to write yourself. Take a look at the [Godot Asset Library](https://godotengine.org/asset-library/) for plugins, and [Godot's feature page](https://godotengine.org/features) for more.