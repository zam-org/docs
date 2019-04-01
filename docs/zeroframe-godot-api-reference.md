# ZeroFrame Godot API Reference

[ZeroFrame Godot]() is a plugin for the [Godot Game Engine](https://godotengine.org) that allows you to communicate with ZeroNet. With this you can create simple multiplayer functionality within your game without having to rent a server or create any APIs.

Below is the API reference, which defines all of the methods that one can use after [installation](https://github.com/zam-org/godot-zeroframe-plugin#installation). To see a general guide to usage, see [Getting Started](getting-started).

## Login and Registration

Logging in to [zites](terminology#zite) is done through the means of an ID provider. For more information on how login and registration works, see [ZeroNet ID providers](zeronet/zeronet-id-providers). 

### login

**Definition:**

```
login(master_seed: String = "", provider: int = PROVIDER_ZEROID) -> Result
```

**Description:**

`login` is used for logging in to a [ZeroNet provider](zeronet/zeronet_providers.md). The method takes in `master_seed`, which is a string of random digits and numbers that acts as your ZeroNet account password. The `master_seed` is a value stored in your ZeroNet instance's `data/users.json` file.

You can also set which provider you would like to log in to. The default value is `PROVIDER_ZEROID`, which means after setting ZeroNet's master seed value, the library will try to request a certificate with ZeroID that matches `master_seed`. If successful, a certificate will be added to your ZeroNet client, and you can then use that to act as your user on various zites.

??? "Example"

    An example of logging in to ZeroID with a master seed.

    ```
    # Login to ZeroID
    var res = yield(login("7d0ae0e2bebafb7d02440979c407896796727e30a5d2c27565ed1d1ea2ba4f87", "completed"))

    # If res.error is set, something went wrong. Print out the error
    if res.error != nil:
        prints("There was an error logging in!", res.error)
        return

    # If we made it here then there was no error!
    print("Login successful!")
    ```

### register

**Definition:**

`register(username: String, provider: int = PROVIDER_ZEROID) -> Result`

**Description:**

`register` is used for registering with a ZeroNet ID provider. The default provider is ZeroID, which is currently the only supported ID provider. After registration it is not necessary to login, as a certificate will already be provided to the client.

??? "Example"

    An example of registering with ZeroID. Only lowercase letters are allowed in `username`.

    res = yield(ZeroFrame.register("thekingbob"), "completed")
    if res.error:
        prints("Error during registration:", res.error)
    
    prints("Registration successful!")

### retrieve_master_seed

**Definition:**

`retrieve_master_seed() -> Result`

**Description:**

### logout

**Definition:**

`logout() -> Result`

**Description:**

Log out of all ZeroNet providers and remove the master seed from the ZeroNet client.


### is_logged_in

**Definition:**

`func is_logged_in(provider: int = PROVIDER_ZEROID) -> Result`

**Description:**

## Achievements

Each achievement is defined by the site in a file called `achievements.json`
in the site's `data/` folder. Each achievement has an ID and follows the
following format:

```
{
  ...
  "achievements": {
    "1": {
      title: "Master Builder",
      description: "Build 100 structures",
      default: 0,
      needed: 100,
      icon: "data/achievement_icons/mbuilder.png"
    },
  }
  ...
}
```

User achievement progress is tracked in their own `data.json` file (stored at
`data/users/{userId}/data.json`). This file should contain an "achievements"
key with an object value. Achievement data for this user is then stored in
the following format:

```
{
  ...
  "achievements": {
    "1": 57 
  },
  ...
}
```

where `"1"` is the ID of the achievement It is worth noting that an
achievement's ID can be anything, they just need to match between both the
global and individual user achievement JSON files.

`"57"` is the progress made towards the achievement - or in this case how many
structures the players has created. Determining whether the achievement has
been completed later on is then a simple manner of comparing this value
against the achievement's `needed` value.

### set_achievement_value

**Definition:**

`set_achievement_value(id: int, value: int) -> Result`

**Description:**

### get_all_achievements

**Definition:**

`get_all_achievements() -> Result`

**Description:**

### get_achievement

**Definition:**

`get_achievement(id: int) -> Result`

**Description:**

### get_completed_achievements

**Definition:**

`get_completed_achievements(username: String = "", provider: int = PROVIDER_ZEROID) -> Result`

**Description:**

### get_uncompleted_achievements

**Definition:**

`get_uncompleted_achievements(username: String = "", provider: int = PROVIDER_ZEROID) -> Result`

**Description:**

### achievement_completed

**Definition:**

`achievement_completed(id: int, username: String = "", provider: int = PROVIDER_ZEROID) -> Result`

**Description:**

### get_achievement_progress

**Definition:**

`get_achievement_progress(id: int, username: String = "", provider: int = PROVIDER_ZEROID) -> Result`

**Description:**

## Scores

TODO

### fetch_score

**Definition:**

`fetch_score(id: int, username: String = "", limit: int = 0) -> Result`

**Description:**

### save_score

**Definition:**

`save_score(id: int, score: float) -> Result`

**Description:**

## Storage

The storing and loading of arbitrary data from a user's storage. Users are able to read from any other user's storage, but only modify their own.

### save_file

**Definition:**

`save_file(filepath: String, data: Array) -> Result`

**Description:**

### load_file

**Definition:**

`load_file(filepath: String) -> Result`

**Description:**

### remove_file

**Definition:**

`remove_file(filepath: String) -> Result`

**Description:**

### save_data

**Definition:**

`save_data(key, data) -> Result`

**Description:**

### get_data

**Definition:**

`get_data(key: String, username: String = "", provider: int = PROVIDER_ZEROID) -> Result`

**Description:**

### remove_data

**Definition:**

`remove_data(key: String) -> Result`

## Daemon Management

These functions are for controlling the [ZeroNet Godot
Addon](zeronet-godot-api-reference) which is required by ZeroFrame. The same
functionality can be had by calling ZeroNet directly, but this way you only
have to import one library into your script.

These functions are provided purely for convenience.

### start_zeronet

**Definition:**

`start_zeronet() -> Result`

**Description:**

Starts the internal ZeroNet daemon. For more information see [ZeroNet.start()](zeronet-godot-api-reference#start)

### stop_zeronet

**Definition:**

`stop_zeronet() -> Result`

**Description:**

Stops the internal ZeroNet daemon. For more information see [ZeroNet.stop()](zeronet-godot-api-reference#stop)

## Site Management

### connect_site

**Definition:**

`connect_site(site_address: String) -> Result`

**Description:**

### connected

**Definition:**

`connected() -> Result`

**Description:**

Check whether we are currently connected to a zite.

At the moment ZeroFrame can only connect to one zite at a time. This poses
some problems during activities such as `login()` which require disconnecting
from the current site, connecting to the specified ID provider, and then
connecting back to the previous site again. Ideally in the future it will be
possible to connect to more than one zite at a time.

??? "Example"

    Check whether we're connected to a zite.

    ```
    if (yield(ZeroFrame.connected(), "completed")):
        prints("We're connected!")
    else:
        print("Not currently connected to any zite.")