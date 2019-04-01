# ZeroNet Godot API Reference

[ZeroNet Godot](https://godotengine.org/asset-library/asset/327) is a plugin for the [Godot Game Engine](https://godotengine.org) that allows for running an instance of ZeroNet entirely within your game executable. This instance is sometimes called a "daemon", which simply means a program running in the background on your computer.

Plugins such as [ZeroFrame Godot](zeroframe-godot-api-reference) can then be used to interact with the daemon.

See below for methods that allow for control of the daemon's running state.

## Managing ZeroNet

### start

**Definition:**

`start(port: int = null)`

**Description:**

`start` starts a running instance of ZeroNet according to the current operating system/architecture. Currently supported platforms are `Linux 32/64bit`, `MacOS 10.9+` and `Windows`. This will spawn a new python process that will continue running until it is stopped. That means if it is not stopped with the `stop()` method, then ZeroNet will continue running in the background even after game exit.

??? "Example"

    An example of starting an instance of ZeroNet.

    ```
    ZeroNet.start()
    ```

    ZeroNet can also be told to listen for commands on a specific port.

    ```
    # Start ZeroNet listening on port 43110
    ZeroNet.start(43110)
    ```

### stop

**Definition:**

`stop()`

**Description:**

`stop` stops the last-started ZeroNet instance. `start` will create a ZeroNet instance and store the process ID, whereas `stop` will kill the process with the saved process ID.

??? "Example"

    Stop the running ZeroNet process.

    ```
    ZeroNet.stop()
    ```

The following block of code can be used to end the running ZeroNet process on game exit:

```
func _exit_tree():
	"""Ensure ZeroNet is stopped if the game is exited"""
	ZeroNet.stop()
```