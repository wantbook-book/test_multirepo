# Allay
The allay ( /əˈleɪ/ uh-ʟᴀʏ) is a flying passive mob that collects and delivers items for any player that gives it something or any note block it hears recently playing.

## Contents
- 1 Spawning
- 2 Behavior
	- 2.1 Allay duplication
	- 2.2 Teleportation
- 3 Sounds
- 4 Data values
	- 4.1 ID
	- 4.2 Entity data
- 5 Achievements
- 6 Advancements
- 7 History
- 8 Issues
- 9 Trivia
- 10 Videos
- 11 Gallery
	- 11.1 Renders
	- 11.2 Textures
	- 11.3 Screenshots
	- 11.4 Development images
	- 11.5 Concept artwork
	- 11.6 In other media
- 12 See also
- 13 References
- 14 External links

## Spawning
Two allays in a cage near a pillager outpost.
Allays have a 50% chance of spawning in dark oak cages near pillager outposts in groups of 1-3.

Two allays inside a woodland mansion cell.
Allays also have a 50% chance to spawn inside jail cells within woodland mansions in groups of 1-3.


## Behavior
The allay's luminous texture allows it to be seen clearly in the dark, although it doesn't illuminate its surroundings.

The allay is small, peaceful and flies aimlessly until a player gives it an item with their use key. The allay starts following the player and seeks out dropped versions of the same item to deliver them to its player. The allay returns to wandering around if any player takes its item back by using an empty hand on it.

The allay locks onto the player that last gave it an item. This allay follows the player from up to a 64-block cubic area away and seeks items up to a 32-block cubic area away from the player. After delivering items, the allay has a delay of three seconds until it can seek items again. An allay has a single inventory slot to hold a stack of items (usually 64 items) in addition to the item it got from the player. While the allay does not discern enchantments, special item names or items in shulker boxes when it seeks, it still carries such items in separate trips.

Allays don't pick up any items if the game rule /gamerule mobGriefing is set to false, but the player can still give the allay items with the use key. 

If the allay hears a note block play within 16 blocks of its location while delivering items, it instead delivers its items to the note block and then spend 30 seconds around that particular note block, seeking items around it and returning them to it instead of its player. The allay returns to targeting its player after 30 seconds. A vibration particle emanates from the note block and reaches the allay to indicate the allay has locked on to the note block. While an allay is focused on a note block, it responds only to sound from that note block, which resets the time until the allay loses interest. This in principle allows allays to focus on a single note block while other note blocks are playing in the vicinity, thus allowing many allays to work in parallel with different note blocks. Because the allay and the note block interact via a vibration particle, placing wool between the note block and the allay can prevent this sound interaction. 

The allay can pick up items within a radius of about 1.3 blocks from itself and drop items up to 3 blocks away from its player or note block.

An allay performs a dance animation when there is a nearby jukebox playing. If the jukebox stops playing or if the allay gets too far away from the jukebox, it stops dancing.

The allay cannot enter water, although it attempts to gather items that are under water. 

Allays cannot be harmed by their interacted owners. If they are harmed by another source, they fly away for a few seconds. When killed, allays drop the items they were holding. If an allay dies while holding a totem of undying, it instead returns to full health and the totem is destroyed, as with any mob holding a totem of undying. Allays naturally regenerate 2 per second if damaged.

Using a lead or a named name tag performs the item's normal function, instead of giving it to the allay. An allay may be given a lead by first leashing the allay to a fence post.

### Allay duplication
An allay duplicating.
If an allay is given an amethyst shard while it is dancing due to a nearby jukebox playing any music disc, it splits into two allays (itself and a new allay) and the amethyst shard is consumed. After duplication, both allays have a five minute cooldown before being able to duplicate again. Allays do not have a baby form.

### Teleportation

  

This feature is exclusive to  Bedrock Edition. 


When a player teleports through a nether portal, the player's allay teleports with them, even if it does not enter the portal.

When a player teleports through an end portal, the allay teleports to the End only if a player gives the allay an item before teleporting and must be nearby the player as they teleport.

Allays holding an item follow the player through a portal if they are 21 blocks horizontally to the player or if they are within 22 blocks vertically of the player's legs. Allays do not travel through portals regardless of how close they are if they are tethered to a fence with a lead.


## Data values
### ID
Java Edition:

| Name  | Identifier | Entity tags          | Translation key          |
|-------|------------|----------------------|--------------------------|
| Allay | `allay`    | `fall_damage_immune` | `entity.minecraft.allay` |

Bedrock Edition:

| Name  | Identifier | Numeric ID | Translation key     |
|-------|------------|------------|---------------------|
| Allay | `allay`    | `134`      | `entity.allay.name` |

### Entity data
Allays have entity data associated with them that contain various properties.

Java Edition:

Main article: Entity format
- Entity data
	- 
	- Tags common to all entities
	- 
	- Tags common to all mobs
	- CanDuplicate: 1 or 0 (true/false) – true if the allay can duplicate. This is set tofalsewhen the allay duplicates, andtruewhenDuplicationCooldownreaches 0.
	- DuplicationCooldown: The allay's duplication cooldown in ticks. This is set to 6000 game ticks (5 minutes) when the allay duplicates.
	- Inventory: List of items the allay has picked up. This list can contain at most one compound tag. The item given by the player to the allay is stored in itsHandItems[0]tag, not here.
		- 
		- Tags common to all items
	- listener: The vibration event listener of this allay.
		- distance: Nonnegative integer.
		- event: Optional.
			- distance: Nonnegative integer.
			- game_event: A resource location of the game event.
			- pos: Three doubles representing the X, Y, and Z coordinates.
			- projectile_owner: Optional. The projectile owner'sUUID. The 128-bit UUID is stored as four 32-bit integers, ordered from most to least significant.
			- source: Optional. The source entity'sUUID. The 128-bit UUID is stored as four 32-bit integers, ordered from most to least significant.
		- event_delay: Nonnegative integer.
		- event_distance: Nonnegative integer.
		- range: Nonnegative integer.
		- source: Position source.
			- type: A resource location of the position source type.
			- For typeblock
				- pos: X, Y, and Z coordinates.
			- For typeentity
				- source_entity: The entity'sUUID. The 128-bit UUID is stored as four 32-bit integers, ordered from most to least significant.
				- y_offset:

Bedrock Edition:

SeeBedrock Edition level format/Entity format.
