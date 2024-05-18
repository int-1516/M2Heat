# M2Heat Documentation

This Python module provides functionality for game-related tasks such as pathfinding, network communication, and managing game entities.

## Table of Contents
- [Requirements](#requirements)
- [Modules](#modules)
  - [logger](#logger-module)
  - [timer](#timer-module)
  - [heat](#heat-module)
  - [channel_switcher](#channel_switcher-module)
  - [maps](#maps-module)
  - [script_parser](#script_parser-module)
  - [utility](#utility-module)
  - [bot_state_manager](#bot_state_manager-module)
  - [path_finder](#path_finder-module)
  - [profile_manager](#profile_manager-module)
  - [runner](#runner-module)
  - [const](#const-module)
  - [callbacks](#callbacks-module)
- [`heat` Module](#classes)
  - [Classes](#classes)
    - [pos](#pos)
    - [item_filter_profile](#item_filter_profile)
    - [whitelist_profile](#whitelist_profile)
    - [route_profile](#route_profile)
    - [config_profile](#config_profile)
    - [item_filter_profile_manager_t](#item_filter_profile_manager_t)
    - [whitelist_profile_manager_t](#whitelist_profile_manager_t)
    - [route_profile_manager_t](#route_profile_manager_t)
    - [config_profile_manager_t](#config_profile_manager_t)
    - [astar_t](#astar_t)
    - [map_t](#map_t)
    - [item_t](#item_t)
    - [mob_table_t](#mob_table_t)
    - [network_stream_t](#network_stream_t)
    - [instance_t](#instance_t)
    - [ground_item_t](#ground_item_t)
    - [player_t](#player_t)
    - [map_info_t](#map_info_t)
    - [background_t](#background_t)
  - [Global Variables](#global-variables)
  - [Global Functions](#global-functions)

## Requirements
- Python 2.7

## Modules

### `logger` Module
The `logger` module provides functions for logging messages.

#### Functions
- `trace(s: str)`: Logs a trace message with the given string `s`.
- `error(s: str)`: Logs an error message with the given string `s`.

### `timer` Module
The `timer` module provides functions for working with time.

#### Functions
- `get_epoch_ms() -> int`: Returns the current time in milliseconds since the epoch.
- `get_mtime(file_name: str) -> int`: Returns the modification time of the file specified by `file_name`.

### `heat` Module
The `heat` module contains various classes and functions for game-related tasks.

## Classes

### `pos`
Represents a position in a 3D space.

#### Methods
- `__init__(self, x: float, y: float, z: float)`: Initializes the position with coordinates `x`, `y`, and `z`.
- `normalized(self) -> pos`: Returns a new `pos` instance that is the normalized version of the current instance.

#### Properties
- `x: float`: X-coordinate.
- `y: float`: Y-coordinate.
- `z: float`: Z-coordinate.

### `item_filter_profile`
Stores a list of item vnums (IDs).

#### Properties
- `vnums: List[int]`

### `whitelist_profile`
Stores a list of whitelisted names.

#### Properties
- `names: List[str]`

### `route_profile`
Handles route profiles.

#### Methods
- `get(self) -> Tuple[str, List[pos]]`: Returns a tuple containing a route name and a list of positions.

### `config_profile`
Configuration settings for a bot.

#### Properties
- `botting: bool`
- `distance: float`
- `hit_limit: int`
- `walk: bool`
- `attack_hack: bool`
- `skill_hack: bool`
- `attack_types: int`
- `antiban: bool`
- `picking: bool`
- `auto_login: bool`
- `auto_potion: bool`
- `auto_potion_percent: int`
- `auto_revive: bool`
- `anti_exp: bool`
- `pickup_selected: bool`
- `pickup_enable_auto_sell: bool`
- `pickup_enable_auto_store: bool`
- `pickup_sell_potions: bool`
- `storage_password: str`
- `move_speed: float`
- `antiban_trigger_player: bool`
- `antiban_trigger_gm: bool`
- `antiban_trigger_pm: bool`
- `antiban_trigger_gm_pm: bool`
- `antiban_stop_hacks: bool`
- `antiban_wait_till_gone: bool`
- `antiban_logout: bool`
- `antiban_change_ch: bool`
- `antiban_exit_game: bool`

### `item_filter_profile_manager_t`
Manages item filter profiles.

#### Properties
- `current: item_filter_profile`

### `whitelist_profile_manager_t`
Manages whitelist profiles.

#### Properties
- `current: whitelist_profile`

### `route_profile_manager_t`
Manages route profiles.

#### Properties
- `current: route_profile`

### `config_profile_manager_t`
Manages configuration profiles.

#### Properties
- `current: config_profile`
- `current_name: str`

#### Methods
- `load(self, name: str)`: Loads the profile specified by `name`.

### `astar_t`
Pathfinding using the A* algorithm.

#### Methods
- `find_path(self, start: pos, end: pos) -> List[pos]`: Finds and returns a path from `start` to `end`.

### `map_t`
Handles drawing and managing lines on a map.

#### Methods
- `add_line(self, x: int, y: int, tx: int, ty: int, r: float, g: float, b: float, a: float)`: Adds a line to the map.
- `clear_lines(self)`: Clears all lines from the map.

### `item_t`
Represents an item with various properties.

#### Methods
- `name(self) -> str`: Returns the name of the item.
- `type(self) -> int`: Returns the type of the item.
- `sub_type(self) -> int`: Returns the sub-type of the item.
- `size(self) -> int`: Returns the size of the item.
- `buy_price(self) -> int`: Returns the buy price of the item.
- `sell_price(self) -> int`: Returns the sell price of the item.
- `sellable(self) -> bool`: Returns whether the item is sellable.
- `storable(self) -> bool`: Returns whether the item is storable.
- `stackable(self) -> bool`: Returns whether the item is stackable.

### `mob_table_t`
Represents a mob (mobile entity) with properties and methods.

#### Methods
- `name(self) -> str`: Returns the name of the mob.
- `position(self) -> pos`: Returns the position of the mob.

#### Properties
- `type`: Mob type.
- `rank`: Mob rank.
- `battle_type`: Mob battle type.
- `level`: Mob level.
- `size`: Mob size.

### `network_stream_t`
Handles network-related actions.

#### Methods
- `item_use(self, cell: int) -> bool`: Uses an item from a specified cell.
- `on_click(self, vid: int) -> bool`: Handles click actions on a specified VID.
- `sell(self, slot: int, count: int, type: int) -> bool`: Sells an item from a specified slot.
- `attack(self, mode: int, vid: int) -> bool`: Performs an attack on a specified VID.
- `add_fly_targeting(self, vid: int, pos: pos) -> bool`: Adds fly targeting to a specified VID at a position.
- `fly_targeting(self, vid: int, pos: pos) -> bool`: Executes fly targeting for a specified VID at a position.
- `shoot(self, type: int) -> bool`: Shoots using a specified type.
- `use_skill(self, skill_idx: int, target_vid: int) -> bool`: Uses a skill on a target VID.
- `state(self, pos: pos, rot: float, func: int, arg: int) -> bool`: Sets the state at a position with specified rotation, function, and argument.
- `pickup(self, vid: int) -> bool`: Picks up an item specified by VID.
- `phase(self) -> str`: Returns the current network phase.
- `set_login_phase(self) -> None`: Sets the network to login phase.
- `set_direct_enter_mode(self, chr: int) -> None`: Sets the mode for direct enter.

### `instance_t`
Represents an instance of an entity in the game.

#### Methods
- `vid(self) -> int`: Returns the VID of the instance.
- `vnum(self) -> int`: Returns the VNUM of the instance.
- `type(self) -> int`: Returns the type of the instance.
- `name(self) -> str`: Returns the name of the instance.
- `dead(self) -> bool`: Returns whether the instance is dead.
- `position(self) -> pos`: Returns the position of the instance.
- `rotation(self) -> float`: Returns the rotation of the instance.
- `boss(self) -> bool`: Returns whether the instance is a boss.
- `resource(self) -> bool`: Returns whether the instance is a resource.
- `pk(self) -> bool`: Returns whether the instance is in PK mode.
- `empire(self) -> int`: Returns the empire of the instance.
- `motion(self) -> int`: Returns the motion state of the instance.
- `alignment(self) -> int`: Returns the alignment of the instance.
- `affect(self, id: int, visible: bool)`: Applies an affect to the instance.
- `move(self, destination: pos)`: Moves the instance to a specified destination.
- `speed(self) -> float`: Returns the speed of the instance.

### `ground_item_t`
Represents an item on the ground.

#### Methods
- `vnum(self) -> int`: Returns the vnum of the item.
- `position(self) -> pos`: Returns the position of the item.
- `owner(self) -> str`: Returns the owner of the item.

### `player_t`
Handles player-specific actions and properties.

#### Methods
- `run_cool_time(self, skill_idx: int) -> None`: Sets the cooldown for a skill.
- `get_item_index(self, window_type: int, slot: int) -> int`: Returns the item index in a specified window and slot.
- `get_item_count(self, window_type: int, slot: int) -> int`: Returns the item count in a specified window and slot.
- `on_press_actor(self, vid: int, is_auto: bool) -> None`: Handles press actions on an actor.
- `set_status(self, type: int, value: int) -> None`: Sets a status with a specified type and value.

### `map_info_t`
Provides information about the map.

#### Methods
- `name(self) -> str`: Returns the name of the map.

### `background_t`
Handles background and map-related queries.

#### Methods
- `map_info(self, x: float, y: float) -> map_info_t`: Returns map information for the specified coordinates.
- `blocked(self, x: float, y: float) -> bool`: Checks if the specified coordinates are blocked.

## Global Variables
- `item_filter_profile_manager`: Instance of `item_filter_profile_manager_t`.
- `whitelist_profile_manager`: Instance of `whitelist_profile_manager_t`.
- `route_profile_manager`: Instance of `route_profile_manager_t`.
- `config_profile_manager`: Instance of `config_profile_manager_t`.
- `astar`: Instance of `astar_t`.
- `map`: Instance of `map_t`.
- `network`: Instance of `network_stream_t`.
- `player`: Instance of `player_t`.
- `background`: Instance of `background_t`.

#### Usage Example
```python
import heat, const, logger

# Get all mobs within a distance of 1000 units
all_mobs = heat.mobs(const.MOBS_ALL, 1000)
logger.trace("Number of all mobs within 1000 units: %d" % len(all_mobs))

# Get regular mobs within a distance of 500 units
regular_mobs = heat.mobs(const.MOBS_MOB, 500)
logger.trace("Number of regular mobs within 500 units: %d" % len(regular_mobs))

# Get the mob instance by its VID
mob_vid = 12345
mob_instance = heat.mob_by_vid(mob_vid)
if mob_instance:
    logger.trace("Mob instance with VID %d found" % mob_vid)
else:
    logger.trace("Mob instance with VID %d not found" % mob_vid)

# Get ground items within a distance of 800 units
ground_items = heat.items(800)
logger.trace("Number of ground items within 800 units: %d" % len(ground_items))

# Calculate the distance between two positions
start_pos = heat.pos(100, 200, 0)
end_pos = heat.pos(500, 600, 0)
dist = heat.distance(start_pos, end_pos)
logger.trace("Distance between start and end positions: %f" % dist)

# Get the main instance
main_inst = heat.main_instance()
if main_inst:
    logger.trace("Main instance found: %s" % main_inst.name())
else:
    logger.trace("Main instance not found")

# Get the current map name
current_map = heat.current_map()
logger.trace("Current map: %s" % current_map)

# Get an item instance by its VNUM
item_vnum = 1001
item_instance = heat.item(item_vnum)
if item_instance:
    logger.trace("Item instance with VNUM %d found: %s" % (item_vnum, item_instance.name()))
else:
    logger.trace("Item instance with VNUM %d not found" % item_vnum)

# Get a mob instance by its VNUM
mob_vnum = 2001
mob_instance = heat.npc(mob_vnum)
if mob_instance:
    logger.trace("Mob instance with VNUM %d found: %s" % (mob_vnum, mob_instance.name()))
else:
    logger.trace("Mob instance with VNUM %d not found" % mob_vnum)

# Get the current quest script as a string
quest_script = heat.quest_script_str()
logger.trace("Current quest script: %s" % quest_script)

# Get the current path
current_path = str(heat.get_path())
logger.trace("Current path: %s" % current_path)

# Get the resources path
resources_path = str(heat.get_resources_path())
logger.trace("Resources path: %s" % resources_path)

# Get the scripts path
scripts_path = str(heat.get_resources_path())
logger.trace("Scripts path: %s" % scripts_path)
```

## Global Functions
- `mobs(type: int, distance: float) -> Dict[int, instance_t]`: Returns a dictionary of mobs filtered by type and within the specified distance.
- `mob_by_vid(vid: int) -> instance_t`: Returns a mob instance by its VID.
- `items(distance: float) -> Dict[int, ground_item_t]`: Returns a dictionary of ground items within the specified distance.
- `distance(start: pos, end: pos) -> float`: Calculates the distance between two positions.
- `main_instance() -> instance_t`: Returns the main instance.
- `current_map() -> str`: Returns the current map name.
- `item(vnum: int) -> item_t`: Returns an item instance by its VNUM.
- `npc(vnum: int) -> mob_table_t`: Returns a mob instance by its VNUM.
- `quest_script_str() -> str`: Returns the current quest script as a string.
- `get_path() -> str`: Returns the current path.
- `get_resources_path() -> str`: Returns the resources path.
- `get_scripts_path() -> str`: Returns the scripts path.

### `channel_switcher` Module
The `channel_switcher` module provides functionality for managing and switching between game channels.

#### Classes

##### `channel_switcher`
Handles channel-related operations and information.

###### Methods
- `__init__(self)`: Initializes the `channel_switcher` instance.
- `get_region_id(self) -> int`: Returns the region ID.
- `get_server_id(self, region_id: int) -> int`: Returns the server ID for the specified region.
- `get_channel_info(self) -> None`: Retrieves and stores channel information.
- `get_channel_count(self) -> int`: Returns the number of available channels.
- `connect_to_channel(self, id: int) -> None`: Connects to the specified channel.
- `get_next_channel(self) -> int`: Returns the next channel ID.
- `connect_to_next_channel(self) -> None`: Connects to the next channel.
- `get_curr_channel(self) -> int`: Returns the current channel ID.
- `on_connect(self, ip: str, port: int) -> None`: Handles the connection event.

###### Properties
- `channels: Dict[int, Dict[str, Any]]`: Dictionary of channel information.
- `current_channel: int`: Current channel ID.
- `port_diff: int`: Port difference between the current channel and the connected port.
- `port: int`: Connected port.
- `job: Optional[Any]`: Job object.

#### Global Variables
- `instance: channel_switcher`: Instance of the `channel_switcher` class.

#### Usage Example
```python
from channel_switcher import instance as channel_switcher

# Get the number of available channels
channel_count = channel_switcher.get_channel_count()

# Connect to the next channel
channel_switcher.connect_to_next_channel()

# Connect to channel 3
channel_switcher.connect_to_channel(3)
```

In this example, we import the `instance` variable from the `channel_switcher` module and rename it to `channel_switcher` for convenience. We then use the `get_channel_count()` method to retrieve the number of available channels and print it. Finally, we call the `connect_to_next_channel()` method to connect to the next channel.

### `maps` Module
The `maps` module provides functionality for parsing and retrieving map-related information, such as NPC positions and warp positions.

#### Classes

##### `point`
Represents a point on a map with its index, coordinates, and vnum.

###### Methods
- `__init__(self, index: int, x: int, y: int, vnum: int)`: Initializes a new `point` instance with the specified index, coordinates, and vnum.

###### Properties
- `index: int`: The index of the point.
- `x: int`: The x-coordinate of the point.
- `y: int`: The y-coordinate of the point.
- `vnum: int`: The vnum associated with the point.

#### Functions

##### `parse_points() -> Dict[str, List[point]]`
Parses the point files in the "resources/points" folder and returns a dictionary mapping map names to lists of `point` instances.

##### `get_npc_position(map_name: str, vnum: int) -> Optional[heat.pos]`
Retrieves the position of an NPC with the specified `vnum` on the given `map_name`. Returns a `heat.pos` instance if found, or `None` otherwise.

##### `get_warp_position(map_name: str, target_map_name: str) -> Optional[heat.pos]`
Retrieves the position of a warp point on the given `map_name` that leads to the specified `target_map_name`. Returns a `heat.pos` instance if found, or `None` otherwise.

#### Global Variables
- `points: Dict[str, List[point]]`: A dictionary mapping map names to lists of `point` instances, parsed from the point files.

#### Usage Example
```python
import logger
from maps import get_npc_position, get_warp_position, points

# Get the points for a specific map
map_name = "metin2_map_a1"
map_points = points.get(map_name)

if map_points:
    logger.trace("\nPoints for map '%s':" % map_name)
    for point in map_points:
        logger.trace("Index: %d, Position: (%d, %d), Vnum: %d" % (point.index, point.x, point.y, point.vnum))
else:
    logger.trace("No points found for map '%s'" % map_name)

# Get the position of an NPC with vnum 1001 on the "metin2_map_a1" map
npc_position = get_npc_position("metin2_map_a1", 1001)
if npc_position:
    logger.trace("NPC position: (%d, %d)" % (npc_position.x, npc_position.y))
else:
    logger.trace("NPC not found")

# Get the position of a warp point on the "metin2_map_a1" map that leads to "metin2_map_b1"
warp_position = get_warp_position("metin2_map_a1", "metin2_map_b1")
if warp_position:
    logger.trace("Warp position: (%d, %d)" % (warp_position.x, warp_position.y))
else:
    logger.trace("Warp point not found")
```

In this example, we import the `get_npc_position` and `get_warp_position` functions from the `maps` module. We then use `get_npc_position` to retrieve the position of an NPC with vnum 1001 on the "metin2_map_a1" map. If the NPC is found, we print its position; otherwise, we print a message indicating that the NPC was not found.

Similarly, we use `get_warp_position` to retrieve the position of a warp point on the "metin2_map_a1" map that leads to the "metin2_map_b1" map. If the warp point is found, we print its position; otherwise, we print a message indicating that the warp point was not found.

### `script_parser` Module
The `script_parser` module provides a class for parsing quest scripts and extracting relevant information such as dialogue, answers, and images.

#### Classes

##### `script_parser`
A class to parse a quest script.

###### Methods
- `__init__(self)`: Initializes the `script_parser` instance and automatically parses the quest script obtained from `heat.quest_script_str()`.

###### Properties
- `dialogue: str`: The parsed dialogue from the quest script, with tags removed.
- `answers: List[Tuple[int, str]]`: A list of tuples representing the available answers in the quest script. Each tuple contains the answer index and the answer text.
- `images: List[Dict[str, str]]`: A list of dictionaries representing the images in the quest script. Each dictionary contains the following keys:
  - `"image_type": str`: The type of the image.
  - `"idx": str`: The index of the image.
  - `"title": str`: The title of the image.
  - `"desc": str`: The description of the image.
  - `"index": str`: The index of the image within the total number of images.
  - `"total": str`: The total number of images.

#### Usage Example
```python
import logger
from script_parser import script_parser

# Create an instance of script_parser
parser = script_parser()

# Access the parsed dialogue
logger.trace("Dialogue:")
logger.trace(parser.dialogue)

# Access the available answers
logger.trace("\nAnswers:")
for answer in parser.answers:
    logger.trace("Index: %d, Text: %s" % (answer[0], answer[1]))

# Access the images
logger.trace("\nImages:")
for image in parser.images:
    logger.trace("Type: %s, Index: %d, Title: %s" % (image['image_type'], image['idx'], image['title']))
    logger.trace("Description: %s" % image['desc'])
    logger.trace("Image %d of %d" % (image['index'], image['total']))
    logger.trace("---")
```

In this example, we import the `script_parser` class from the `script_parser` module. We create an instance of `script_parser`, which automatically parses the quest script obtained from `heat.quest_script_str()`.

We can then access the parsed dialogue using `parser.dialogue`, which contains the dialogue text with tags removed.

The available answers can be accessed using `parser.answers`, which is a list of tuples. Each tuple contains the answer index and the answer text. We iterate over the answers and print their index and text.

The images can be accessed using `parser.images`, which is a list of dictionaries. Each dictionary represents an image and contains information such as the image type, index, title, description, and its position within the total number of images. We iterate over the images and print their details.

### `utility` Module
The `utility` module provides various utility functions and classes for game-related tasks and functionality.

#### Functions

##### `get_module(original_module: str) -> Optional[module]`
Retrieves the corresponding module for the given `original_module` name.

##### `get_module_name(original_module: str) -> Optional[str]`
Retrieves the corresponding module name for the given `original_module` name.

##### `generate_unblocked_points(character_position: heat.pos, position: heat.pos) -> List[heat.pos]`
Generates unblocked points around the given `position` based on the `character_position`.

##### `is_same_position(a: Optional[heat.pos], b: Optional[heat.pos]) -> bool`
Checks if two positions `a` and `b` are the same.

##### `get_points(start: heat.pos, end: heat.pos, max_distance: float) -> List[heat.pos]`
Generates intermediate points between `start` and `end` based on the `max_distance`.

##### `is_path_blocked(main_position: heat.pos, target_position: heat.pos, max_distance: float = 100) -> bool`
Checks if the path between `main_position` and `target_position` is blocked.

##### `sort_distance_to_main(instances: List[instance_t], main_instance: instance_t, is_mob: bool = False) -> List[instance_t]`
Sorts the `instances` based on their distance to the `main_instance` and prioritizes instances based on their type or owner.

##### `is_empty_slot(slot: int, storage: bool = False) -> bool`
Checks if the specified `slot` is empty in the inventory or storage.

##### `find_empty_slot(size: int, storage: bool = False) -> int`
Finds an empty slot in the inventory or storage that can accommodate an item of the given `size`.

##### `get_npc(vnum: int) -> Optional[mob_table_t]`
Retrieves the NPC instance with the specified `vnum`.

##### `has_attr(slot: int) -> bool`
Checks if the item in the specified `slot` has attributes.

##### `is_inventory_full() -> bool`
Checks if the inventory is full.

##### `stack_item(vnum: int, slot: int, count: int) -> bool`
Stacks an item with the specified `vnum` and `count` from the inventory `slot` to the storage.

##### `store_item(vnum: int, slot: int) -> bool`
Stores an item with the specified `vnum` from the inventory `slot` to the storage.

##### `get_pickable_distance() -> int`
Retrieves the pickable distance based on the player's mount status.

##### `get_race() -> int`
Retrieves the player's race ID.

##### `get_hp() -> int`
Retrieves the player's current HP percentage.

##### `get_sp() -> int`
Retrieves the player's current SP percentage.

##### `get_default_teacher() -> Optional[int]`
Retrieves the default teacher VNUM based on the player's race.

##### `get_teacher() -> Tuple[Optional[str], Optional[heat.pos], Optional[int]]`
Retrieves the teacher's map name, position, and VNUM based on the player's empire.

##### `get_game_window_instance() -> Optional[game_window_instance]`
Retrieves the game window instance.

##### `select_answer(idx: Optional[int], answers: List[Tuple[int, str]]) -> None`
Selects an answer from the quest window based on the `idx` and `answers`.

##### `close_quest_window() -> None`
Closes the quest window.

##### `close_popup_notice() -> None`
Closes the popup notice window.

#### Classes

##### `movement_handler`
Handles movement along a path.

###### Methods
- `__init__(self, path: Optional[List[heat.pos]] = None)`: Initializes the `movement_handler` with an optional `path`.
- `set_path(self, path: List[heat.pos], character_position: heat.pos, change_direction: bool = True) -> None`: Sets the `path` and updates the path index based on the `character_position`.
- `set_closest_point(self, character_position: heat.pos) -> None`: Sets the closest point on the path based on the `character_position`.
- `draw(self) -> None`: Draws the path on the map.
- `move_along_path(self, main_instance: instance_t, distance_threshold: float = 250) -> bool`: Moves the `main_instance` along the path.

###### Properties
- `path: Optional[List[heat.pos]]`: The path to follow.
- `path_idx: int`: The current index on the path.
- `reverse_direction: bool`: Indicates if the movement is in the reverse direction.
- `change_direction: bool`: Indicates if the direction should be changed.
- `on_direction_change: Optional[Callable[[bool], None]]`: Callback function called when the direction changes.
- `on_path_complete: Optional[Callable[[], None]]`: Callback function called when the path is completed.

##### `Hooks`
Provides functionality for hooking and modifying functions.

###### Methods
- `__init__(self)`: Initializes the `Hooks` instance.
- `__del__(self)`: Removes all the hooks when the instance is deleted.
- `get_module(self, module_name: str) -> Optional[module]`: Retrieves the module with the specified `module_name`.
- `add(self, function: Tuple[str, str], hook: Callable, run_original: bool = True, run_after: bool = False, overwrite: bool = False) -> bool`: Adds a hook to the specified `function`.
- `remove(self, function: Tuple[str, str]) -> bool`: Removes the hook from the specified `function`.

#### Global Variables
- `hook: Hooks`: An instance of the `Hooks` class.

#### Usage Example
```python
import logger
from utility import get_hp, get_sp, get_race, get_module

# Get app module and set camera max distance
app = get_module("app")
app.SetCameraMaxDistance(20000)

# Get the player's current HP percentage
hp_percentage = get_hp()
logger.trace("Current HP: %d%%" % hp_percentage)

# Get the player's current SP percentage
sp_percentage = get_sp()
logger.trace("Current SP: %d%%" % sp_percentage)

# Get the player's race ID
race_id = get_race()
logger.trace("Player's race ID: %d" % race_id)
```

In this example, we import the `get_hp`, `get_sp`, and `get_race` functions from the `utility` module. We then use these functions to retrieve the player's current HP percentage, SP percentage, and race ID, respectively. The retrieved values are printed to the console.

### `bot_state_manager` Module
The `bot_state_manager` module provides a class for managing the state of the bot, including activation, pickup, and stop/resume functionality.

#### Classes

##### `bot_state_manager`
Manages the state of the bot.

###### Methods
- `__init__(self)`: Initializes the `bot_state_manager` instance with default values.
- `request_stop(self, reason: str = "not specified") -> None`: Requests the bot to stop and increments the `stop_count`. If the `stop_count` reaches 1, it resets the bot state and logs the stop request with the specified `reason`.
- `request_resume(self, reason: str = "not specified") -> None`: Requests the bot to resume and decrements the `stop_count`. If the `stop_count` reaches 0, it logs the resume request with the specified `reason`.
- `is_stopped(self) -> bool`: Checks if the bot is currently stopped.

###### Properties
- `is_bot_active: bool`: Indicates if the bot is currently active.
- `is_pickup_active: bool`: Indicates if pickup is currently active.
- `stop_count: int`: The count of stop requests.

#### Global Variables
- `instance: bot_state_manager`: An instance of the `bot_state_manager` class.

#### Usage Example
```python
import logger
from bot_state_manager import instance as bot_state

# Request the bot to stop
bot_state.request_stop("Taking a break")

# Check if the bot is stopped
if bot_state.is_stopped():
    logger.trace("Bot is currently stopped")
else:
    logger.trace("Bot is running")

# Request the bot to resume
bot_state.request_resume("Break is over")

# Check if the bot is active
if bot_state.is_bot_active:
    logger.trace("Bot is active")
else:
    logger.trace("Bot is inactive")

# Check if pickup is active
if bot_state.is_pickup_active:
    logger.trace("Pickup is active")
else:
    logger.trace("Pickup is inactive")
```

In this example, we import the `instance` variable from the `bot_state_manager` module and rename it to `bot_state` for convenience.

We start by requesting the bot to stop using `bot_state.request_stop()` and provide a reason for stopping. We then check if the bot is currently stopped using `bot_state.is_stopped()` and print the appropriate message.

Next, we request the bot to resume using `bot_state.request_resume()` and provide a reason for resuming.

Finally, we check if the bot is active using `bot_state.is_bot_active` and if pickup is active using `bot_state.is_pickup_active`, and print the corresponding messages.

### `path_finder` Module
The `path_finder` module provides functionality for finding paths between maps and navigating to a destination using teleporters and warps.

#### Classes

##### `tp_path_finder`
Finds teleport paths between maps.

###### Methods
- `__init__(self)`: Initializes the `tp_path_finder` instance by parsing the path finder data and building the graph.
- `find_path(self, cur_pos: heat.pos, start_map: str, end_map: str, current_level: int) -> List[Dict[str, str]]`: Finds the teleport path between the `start_map` and `end_map` based on the current position and level.

##### `path_finder`
Handles path finding and navigation to a destination.

###### Methods
- `__init__(self)`: Initializes the `path_finder` instance with default values and sets up callbacks.
- `__del__(self)`: Removes the registered callbacks and clears the map lines.
- `set_destination(self, destination: Dict[str, Any], event_handler: Optional[Callable[[bool], None]], jump_enabled: bool = False) -> bool`: Sets the destination and initiates path finding.

###### Properties
- `DISTANCE_THRESHOLD: int`: The distance threshold for considering the destination as reached.
- `tp: tp_path_finder`: An instance of the `tp_path_finder` class for finding teleport paths.
- `movement_handler: utility.movement_handler`: An instance of the `movement_handler` class for handling movement along the path.
- `tp_path: List[Dict[str, str]]`: The teleport path to the destination.
- `tp_idx: int`: The current index in the teleport path.
- `path: List[heat.pos]`: The generated path to the destination.
- `path_idx: int`: The current index in the generated path.
- `cur_pos: Optional[heat.pos]`: The current position of the character.
- `cur_map: str`: The current map name.
- `event_handler: Optional[Callable[[bool], None]]`: The event handler to be called on path completion or reset.
- `move_speed_original: int`: The original move speed before modification.

#### Global Variables
- `instance: path_finder`: An instance of the `path_finder` class.

#### Usage Example
```python
import logger
from path_finder import instance as path_finder

def on_path_complete(success):
    if success:
        logger.trace("Reached the destination!")
    else:
        logger.trace("Failed to reach the destination.")

destination = {
    "map": "metin2_map_a1",
    "pos": heat.pos(1000, 2000, 0)
}

success = path_finder.set_destination(destination, on_path_complete)
if success:
    logger.trace("Path finding started.")
else:
    logger.trace("Failed to start path finding.")
```

In this example, we import the `instance` variable from the `path_finder` module and rename it to `path_finder` for convenience.

We define a function `on_path_complete` that will be called when the path finding is completed. It takes a `success` parameter indicating whether the destination was reached successfully or not.

We create a `destination` dictionary specifying the target map and position.

We call `path_finder.set_destination` with the `destination` and `on_path_complete` function as arguments. This sets the destination and initiates the path finding process. The function returns a boolean indicating whether the path finding started successfully.

### `profile_manager` Module
The `profile_manager` module provides functionality for managing configuration profiles based on character level ranges.

#### Classes

##### `profile_manager`
Manages configuration profiles based on character level ranges.

###### Methods
- `__init__(self)`: Initializes the `profile_manager` instance with default values.
- `set_level_ranges(self, level_ranges: List[Tuple[int, int, str]], character_name: str = "")`: Sets the level ranges and associated profile names for a specific character or as default.

###### Properties
- `level_ranges: Dict[str, List[Tuple[int, int, str]]]`: A dictionary mapping character names to their level ranges and associated profile names.
- `current_level: int`: The current level of the character.

#### Global Variables
- `instance: profile_manager`: An instance of the `profile_manager` class.

#### Usage Example
```python
from profile_manager import instance as profile_manager

# Set level ranges and profile names for a specific character
profile_manager.set_level_ranges([(1, 10, "profile_low_level"), (11, 20, "profile_mid_level"), (21, 30, "profile_high_level")], "character_name")

# Set default level ranges and profile names
profile_manager.set_level_ranges([(1, 15, "profile_default_low"), (16, 30, "profile_default_high")])
```

In this example, we import the `instance` variable from the `profile_manager` module and rename it to `profile_manager` for convenience.

We use the `set_level_ranges` method to define level ranges and associated profile names for a specific character named "character_name". We provide a list of tuples, where each tuple contains the minimum level, maximum level, and the corresponding profile name.

We also set default level ranges and profile names using `set_level_ranges` without specifying a character name. These default level ranges will be used for characters that don't have specific level ranges defined.

The `profile_manager` will automatically load the appropriate configuration profile based on the character's current level and the defined level ranges. It will log a message indicating the loaded profile and the character name.

### `runner` Module
The `runner` module provides a job runner system for executing tasks at specified intervals.

#### Classes

##### `runner`
Manages and executes jobs.

###### Methods
- `__init__(self)`: Initializes the `runner` instance with an empty list of jobs.
- `add(self, param: Any, interval: int = 100, remove_after: bool = False) -> job.job`: Adds a new job to the runner with the specified parameters and returns the created job object.
- `remove(self, param: Any) -> bool`: Removes a job from the runner based on the provided parameter. Returns `True` if the job was successfully removed, `False` otherwise.

###### Properties
- `jobs: List[job.job]`: A list of job objects managed by the runner.

#### Global Variables
- `instance: runner`: An instance of the `runner` class.

#### Usage Example
```python
import logger
from runner import instance as runner

def task1():
    logger.trace("Task 1 executed")

def task2():
    logger.trace("Task 2 executed")

# Add a job that executes task1 every 1000ms (1 second)
job1 = runner.add(task1, interval=1000)

# Add a job that executes task2 after 500ms and removes itself after execution
job2 = runner.add(task2, interval=500, remove_after=True)
```

In this example, we import the `instance` variable from the `runner` module and rename it to `runner` for convenience.

We define two functions, `task1` and `task2`, which represent the tasks to be executed by the jobs.

We use the `add` method of the `runner` instance to add two jobs:
- `job1` executes `task1` every 1000ms (1 second).
- `job2` executes `task2` after 500ms and removes itself after execution by setting `remove_after=True`.

The `runner` will continuously execute the jobs based on their specified intervals. In this example, `task1` will be executed every 1 second, while `task2` will be executed once after 500ms and then remove itself from the runner.

### `hmr` Module
The `hmr` module is a hot module reloading system that allows you to dynamically reload Python modules without restarting the entire application. It monitors specified directories for changes in Python files and automatically reloads the corresponding modules when changes are detected.

#### Usage Example
Here's an example of a test module that the `hmr` module can handle:

```python
# test_module.py

import logger

class TestModule:
    def __init__(self):
        self.interval = 1000
        self.job = None
        logger.trace("TestModule initialized")

    def __del__(self):
        logger.trace("TestModule deleted")

    def loop(self):
        logger.trace("TestModule loop executed")

instance = TestModule()
```

In this example, the `test_module.py` file defines a `TestModule` class with the following:
- An `__init__` method that initializes the module, sets the `interval` attribute to 1000ms, and initializes the `self.job` attribute to `None`.
- A `__del__` method that is called when the module is deleted.
- A `loop` method that is executed at the specified interval.

The `self.job` attribute is used to store the `job` instance associated with the `TestModule` instance. It will be assigned by `hmr` and is responsible for managing the execution of the `loop` method at the specified interval.

When the `hmr` module detects changes in the `test_module.py` file, it will automatically reload the module, creating a new instance of the `TestModule` class and executing its `loop` method at the specified interval. If the `test_module.py` file is deleted, the `hmr` module will unload the module and call its `__del__` method.

The `hmr` module provides a convenient way to develop and test modules without the need to restart the entire application every time a change is made. It can be particularly useful during development and debugging phases.

Note: The `hmr` module watches changes on files inside scripts folder. You can change the path by creating `custom.txt` file near `m2heat.dll` which includes your scripts path. By default it will watch `current_folder\\scripts`

### `const` Module
The `const` module contains various constants used throughout the application.

#### Configuration Constants
- `LEARN_SKILLS: bool`: Indicates whether skills should be learned. Default value is `True`.
- `DEFAULT_SAFEBOX_PASSWORD: str`: The default password for the safebox. Default value is `asdqwe`.
- `CHANGE_CHANNEL_ON_ROUTE_COMPLETE: bool`: Indicates whether to change the channel when a route is completed. Default value is `True`.
- `ATTACK_MOBS_ON_STONE: bool`: Indicates whether to attack mobs on stone. Default value is `True`.

#### Race Constants
- `WARRIOR: List[int]`: A list of race IDs representing the warrior class.
- `ASSASSIN: List[int]`: A list of race IDs representing the assassin class.
- `SURA: List[int]`: A list of race IDs representing the sura class.
- `SHAMAN: List[int]`: A list of race IDs representing the shaman class.
- `LYCAN: List[int]`: A list of race IDs representing the lycan class.

#### NPC Constants
- `TELEPORTER: int`: The VNUM of the teleporter NPC.
- `OLD_MAN: int`: The VNUM of the old man NPC.
- `SALESWOMAN: int`: The VNUM of the saleswoman NPC.
- `STOREKEEPER: int`: The VNUM of the storekeeper NPC.

#### Inventory Constants
- `STORAGE_SLOTS: int`: The number of slots in the storage.
- `INVENTORY_SLOTS: int`: The number of slots in the inventory.
- `INVENTORY: int`: The ID of the inventory window.
- `EQUIPMENT: int`: The ID of the equipment window.
- `COSTUME: int`: The ID of the costume window.
- `DSA: int`: The ID of the dragon soul alchemy window.

#### Equipment Slot Constants
- `ARMOR: int`: The slot index for armor.
- `HELMET: int`: The slot index for helmet.
- `SHOES: int`: The slot index for shoes.
- `BRACELET: int`: The slot index for bracelet.
- `WEAPON: int`: The slot index for weapon.
- `NECKLACE: int`: The slot index for necklace.
- `EARRING: int`: The slot index for earring.
- `ARROW: int`: The slot index for arrow.
- `SHIELD: int`: The slot index for shield.

#### Weapon Type Constants
- `SWORD: int`: The weapon type ID for sword.
- `DAGGER: int`: The weapon type ID for dagger.
- `BOW: int`: The weapon type ID for bow.

#### Mob Type Constants
- `MOBS_ALL: int`: The mob type ID for all mobs.
- `MOBS_MOB: int`: The mob type ID for regular mobs.
- `MOBS_BOSS: int`: The mob type ID for boss mobs.
- `MOBS_PLAYER: int`: The mob type ID for player mobs.
- `MOBS_MINE: int`: The mob type ID for mine mobs.
- `MOBS_STONE: int`: The mob type ID for stone mobs.
- `MOBS_NPC: int`: The mob type ID for NPC mobs.
- `MOBS_RANGE_UNLIMITED: int`: The unlimited range for mob detection.

#### Phase Window Constants
- `PHASE_WINDOW_LOGO: int`: The phase window ID for the logo screen.
- `PHASE_WINDOW_LOGIN: int`: The phase window ID for the login screen.
- `PHASE_WINDOW_SELECT: int`: The phase window ID for the character selection screen.
- `PHASE_WINDOW_CREATE: int`: The phase window ID for the character creation screen.
- `PHASE_WINDOW_LOAD: int`: The phase window ID for the loading screen.
- `PHASE_WINDOW_GAME: int`: The phase window ID for the game screen.
- `PHASE_WINDOW_EMPIRE: int`: The phase window ID for the empire selection screen.

#### Shop Event Constants
- `SHOP_START_EVENT: int`: The event ID for the shop start event.
- `SHOP_END_EVENT: int`: The event ID for the shop end event.

#### Safebox Event Constants
- `SAFEBOX_COOLDOWN_EVENT: int`: The event ID for the safebox cooldown event.
- `SAFEBOX_SET_PASSWORD_EVENT: int`: The event ID for the safebox set password event.
- `SAFEBOX_ASK_PASSWORD_EVENT: int`: The event ID for the safebox ask password event.
- `SAFEBOX_WRONG_PASSWORD_EVENT: int`: The event ID for the safebox wrong password event.
- `SAFEBOX_START_EVENT: int`: The event ID for the safebox start event.
- `SAFEBOX_END_EVENT: int`: The event ID for the safebox end event.

#### Teacher Constants
- `BODY_FORCE_TEACHER: int`: The teacher ID for the body force teacher.
- `MENTAL_FIGHT_TEACHER: int`: The teacher ID for the mental fight teacher.
- `BLADE_FIGHT_TEACHER: int`: The teacher ID for the blade fight teacher.
- `ARCHERY_TEACHER: int`: The teacher ID for the archery teacher.
- `WEAPONRY_TEACHER: int`: The teacher ID for the weaponry teacher.
- `BLACK_MAGIC_TEACHER: int`: The teacher ID for the black magic teacher.
- `DRAGON_FORCE_TEACHER: int`: The teacher ID for the dragon force teacher.
- `HEALING_FORCE_TEACHER: int`: The teacher ID for the healing force teacher.

#### Default Teacher Constants
- `DEFAULT_WARRIOR_TEACHER: int`: The default teacher ID for the warrior class.
- `DEFAULT_ASSASSIN_TEACHER: int`: The default teacher ID for the assassin class.
- `DEFAULT_SURA_TEACHER: int`: The default teacher ID for the sura class.
- `DEFAULT_SHAMAN_TEACHER: int`: The default teacher ID for the shaman class.

### `callbacks` Module
The `callbacks` module provides a callback system for handling various game events and hooks.

#### Classes

##### `whisper(callback.callback)`
Handles whisper-related callbacks.

##### `safebox(callback.callback)`
Handles safebox-related callbacks.

##### `shop(callback.callback)`
Handles shop-related callbacks.

##### `quest(callback.callback)`
Handles quest-related callbacks.

##### `phase(callback.callback)`
Handles phase-related callbacks.

#### Global Variables
- `whisper_instance: whisper`: Instance of the `whisper` callback.
- `safebox_instance: safebox`: Instance of the `safebox` callback.
- `shop_instance: shop`: Instance of the `shop` callback.
- `quest_instance: quest`: Instance of the `quest` callback.
- `phase_instance: phase`: Instance of the `phase` callback.

#### Usage Example
```python
import logger
from callbacks import whisper_instance, phase_instance

def on_whisper_received(mode, name, line):
    logger.trace("Received whisper from %s: %s" % (name, line))

def on_phase_change(phase):
    logger.trace("Phase changed to %d" % phase)

# Register callbacks
whisper_instance.add(on_whisper_received)
phase_instance.add(on_phase_change, remove_after_call=True)
```

In this example, we import the callback instances from the `callbacks` module.

We define callback functions for each event:
- `on_whisper_received` is called when a whisper is received.
- `on_phase_change` is called when the game phase changes and the callback will be removed.

We register these callback functions using the `add` method of the respective callback instances.

When the corresponding events occur, the registered callback functions will be called with the relevant arguments.
