# Piston
A piston is a block capable of pushing most entities and blocks when given a redstone signal. 

## Contents
- 1 Obtaining
	- 1.1 Breaking
	- 1.2 Crafting
- 2 Usage
	- 2.1 Crafting ingredient
	- 2.2 Redstone component
		- 2.2.1 Start delay
	- 2.3 Limitations
		- 2.3.1 Exceptions
	- 2.4 Powering pistons
	- 2.5 Slime blocks and honey blocks
- 3 Technical components
- 4 Sounds
	- 4.1 Generic
	- 4.2 Unique
- 5 Data values
	- 5.1 ID
	- 5.2 Block states
	- 5.3 Block data
- 6 Achievements
- 7 Video
- 8 History
	- 8.1 Data history
- 9 Issues
- 10 Trivia
- 11 Gallery
	- 11.1 Screenshots
	- 11.2 Concept artwork
	- 11.3 In other media
- 12 See also
- 13 Notes
- 14 References
- 15 External links

## Obtaining
### Breaking
A piston can be broken using any tool with equal efficiency, and always drops itself.
In Java Edition, it is faster to break them with a pickaxe. The pickaxe is also the preferred tool for breaking the head when extended.[1]

| Block     | Piston                |
|-----------|-----------------------|
| Hardness  | 1.5                   |
| Tool      |                       |
|           | Breakingtime (sec)[A] |
| Default   | 2.25                  |
| Wooden    | 1.15                  |
| Stone     | 0.6                   |
| Iron      | 0.4                   |
| Diamond   | 0.3                   |
| Netherite | 0.25                  |
| Golden    | 0.2                   |


↑ Times are for unenchanted tools as used by players with no status effects, measured in seconds. For more information, see Breaking Speed.


### Crafting
| Ingredients                                    | Crafting recipe |
|------------------------------------------------|-----------------|
| AnyPlanks+Cobblestone+Iron Ingot+Redstone Dust |                 |

## Usage
See also: Tutorials/Piston uses and Mechanics/Redstone/Piston circuits

### Crafting ingredient
| Ingredients      | Crafting recipe |
|------------------|-----------------|
| Slimeball+Piston |                 |

### Redstone component
Pistons are always placed facing toward the player. When powered, the piston's wooden surface (the "head") tries to start extending after start delay. When it extends, it pushes at most 12 blocks. The piston makes a sound that can be heard within a 31×31×31 cube centered on the activating piston. Any entities in the path of the extending head are pushed with the blocks. If there is no place for the entities to go, the block pushes inside them, suffocating mobs if the block is not transparent when pushed into the eye height of the mob.

When a piston loses power, its head retracts. Like extending, this retraction starts after start delay. It finishes retracting 2 game ticks (1 redstone tick; 0.1 seconds) after it starts. 

A piston that pushes a slime block bounces any entity that it displaces in the direction the piston is facing. In addition, when a slime block is moved by a piston, any movable blocks adjacent (not diagonally) to the slime block also moves. See the #Slime blocks and honey blocks section below for more details.

In Bedrock Edition, blocks that stick to walls (such as levers) can be placed on pistons without being destroyed when activated.

#### Start delay
A piston won't extend or retract immediately when it is activated: this is called start delay.

In Bedrock Edition, the start delay is fixed at 2 game ticks (1 redstone tick; 0.1 seconds), meaning that the piston starts to extend or retract 2gt after it's activated.

In Java Edition, the start delay can be 0 game ticks (0 redstone ticks; 0 seconds) (start at the same tick) or 1 game tick (0.5 redstone ticks; 0.05 seconds) (start at the next tick) depending on the game process when the piston is activated:

- If the piston is updated and activated in thescheduled tickstage,random tickstage or block event stage, the piston stage is executed in this game tick's block event stage. At this time, the start delay is 0gt, which means the piston starts at the same tick.
- If the piston is activated during the execution of entity or tile entity, or activated by player actions, the piston stage is executed in the next game tick's block event stage. At this time, the start delay is 1gt, which means the piston starts at the next tick.

### Limitations
Pistons can push most blocks except those listed in the table below. 

Pistons cannot push blocks into the void or beyond the top of the map. They also cannot push more than 12 blocks. If the requirements for a block to be pushed are not met, the piston simply does not extend.

| Block                                                                                                                                                                | Effect (Java Edition)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | Effect (Bedrock Edition)                                                                    |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------|
|                                                                                                                                                                      | Barrier Beacon Bedrock Calibrated Sculk Sensor Command Block Crying Obsidian Enchanting Table End Gateway End Portal End Portal Frame Ender Chest Grindstone Jigsaw Block Jukebox Light Block Lodestone Monster Spawner Moving Piston Nether Portal Obsidian Piston (extended) Piston Head Reinforced Deepslate Respawn Anchor Sculk Catalyst Sculk Sensor Sculk Shrieker Structure Block Structure Void‌[BE  only]                                                                                                                                                                                                                                                                                                                                                                                    | Cannot be pushed or pulled.                                                                 |
| Allow Deny Border Structure Air                                                                                                                                      | N/A                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Cannot be pushed or pulled.                                                                 |
|                                                                                                                                                                      | Compound Creator Element Element Constructor Hardened Glass Hardened Glass Pane Heat Block Lab Table Material Reducer Underwater TNT                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | Can be pushed or pulled.                                                                    |
|                                                                                                                                                                      | Underwater Torch Colored Torches                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Breaks when pushed, turning to drops when applicable. Cannot be pulled.                     |
| Barrel Beehive Bee Nest Blast Furnace Brewing Stand Chest Chiseled Bookshelf Conduit Daylight Detector Dispenser Dropper Furnace Hopper Lectern Smoker Trapped Chest | Cannot be pushed or pulled, because these blocks holdblock entities.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | Can be pushed or pulled.                                                                    |
|                                                                                                                                                                      | Large chest                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | Can be pushed or pulled, but separates into two chests.                                     |
|                                                                                                                                                                      | Banner Hanging Sign Sign                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | Breaks when pushed or unsupported, turning into drops.                                      |
|                                                                                                                                                                      | Campfire Soul Campfire                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Breaks when pushed, turning to drops when applicable. Cannot be pulled.                     |
|                                                                                                                                                                      | Glazed Terracotta                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Can be pushed, but not pulled.                                                              |
|                                                                                                                                                                      | Carpets (not moss)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | Can be pushed and pulled. Breaks when pulled downward, turning into drops.                  |
| Bell Candle Lantern Soul Lantern                                                                                                                                     | Breaks when pushed, turning to drops when applicable. Cannot be pulled.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Can be pushed or pulled.                                                                    |
|                                                                                                                                                                      | Amethyst Cluster Bamboo Bed Budding Amethyst Button Cactus Cake Carved Pumpkin Cave Vines Chorus Flower Chorus Plant Cobweb Cocoa Dead Bush Decorated Pot Door Dragon Egg[note 1] Fire Flower Pot Flower Frogspawn   Grass Head Item Frame[note 2] [note 3] Jack o'Lantern Ladder Lava Leaves Lever Lily Pad Melon Melon Stem Moss Block Moss Carpet Mushroom Nether Wart Painting[note 4] Pink Petals Pointed Dripstone Pressure Plate Pumpkin Pumpkin Stem Redstone Comparator Redstone Dust Redstone Repeater Redstone Torch Saplings Scaffolding Sculk Vein Sea Pickle Shulker Box Snow Soul Fire Structure Void‌[JE  only] Sugar Cane Suspicious Sand Torch Torchflower Torchflower Crop Tripwire Tripwire Hook Turtle Egg Twisting Vines Vines Water Weeping Vines Weighted Pressure Plate Wheat | Breaks when pushed, turning to drops when applicable. Cannot be pulled.                     |
| Anvil                                                                                                                                                                | Cannot be pulled. Pushable only whenin a falling state.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Can be pushed or pulled, but falls if unsupported. Cannot be pulled whenin a falling state. |
|                                                                                                                                                                      | Concrete Powder Gravel Red Sand Sand                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | Can be pushed or pulled, but falls if unsupported. Cannot be pulled whenin a falling state. |

Pistons do not move blocks that are "attached to a block", as they detach and drop as an item.

##### Exceptions
- Rails: as long as they remain on top of a solid face of a block in their new position, and that block isn't moving at the same time.
	- An exception is when the rail and block supporting it are on two parallelextendedpistons at which the rail remains attached. InJava Edition, in order for the rail to successfully move without breaking, the piston moving the block must be powered 1 block event after the piston moving the rail. Trying to move both on the same piston usingslime blocksdoes not work, nor does moving them on perpendicular pistons (although the latter temporarilyappearsto work because of the bugMC-75716).
	- Rails re-orient themselves after being pushed, similar to when placed manually.



### Powering pistons
Pistons powered by one line of redstone.
Pistons can be powered in various ways:

- If a redstone wire is in a line shape toward the piston. InJava Edition, the wire does not automatically curve to the piston.
- Pistons can be powered by a powered block directly adjacent to them, whether it is strongly powered or weakly powered.
- Pistons can be powered by aredstone torchdirectly adjacent to them.
- InJava Edition, pistons can be powered by any powered block one block above and to the side, including the "activated space" above it (if a piston, both sticky and normal were to be facing up and ablock of redstoneplaced on its head, it extends when powered, but doesn't retract when the power it receives from the side or back turns off). However, the piston doesn't extend or retract until it receives a block update. This property is calledquasi-connectivityand can be used to make aBUD switch.
- A repeater cannot transfer power through a piston, as pistons are a transparent block.
- An upward-facing piston can't be powered by a block above it, unless it is extended InJava Edition.
- InBedrock Editiona redstone torch attached to a piston turns off whenever the piston is powered. This mechanic is called soft inversion.
- Pistons can also be powered by observers. This can create a clock if the setup is correct.

### Slime blocks and honey blocks



A







B





















Piston A may extend because the slime block ignores the adjacent obsidian. Piston B may not extend because the diamond block is prevented from moving by the obsidian and so the slime block also refuses to move.
When a slime block is pushed or pulled by a piston, while moving, adjacent blocks also move with the slime block, unless a non-piston movable block stops the blocks that are "grabbed" by the slime blocks. These blocks may in turn push other blocks, not just the blocks in the line in front of the piston. For example, a slime block sitting on the ground attempts to move the ground block underneath itself, which in turn has to pushsticky additional ground blocks in the direction of motion just as if it were being pushed directly by a piston.

Glazed terracotta is an exception; it does not move when adjacent slime blocks are moved. The same occurs when a slime block is moved by an adjacent slime block. For example, a 2×2×2 cube of slime blocks may be pushed or pulled as a unit by a single piston acting on any of the blocks in the cube. A slime block adjacent to a block that cannot be moved by pistons ignores the immobile block. But if an adjacent block could be moved but is prevented by the presence of an immobile block, the slime block is prevented from moving.

Slime blocks are not pulled by a non-sticky piston, nor are they moved if an adjacent (non-slime) block is moved by a piston. The maximum of 12 blocks moved by a piston still applies. For example, a 2×2×3 collection of slime blocks may be pushed by a piston as long as no other movable blocks are adjacent to it. A piston cannot move itself via a "hook" constructed of slime blocks, but self-propelled contraptions can be created with multiple pistons. For that, see the article Tutorials/Flying machines. The same happens for the honey block, but it does not stick to slime blocks.

## Technical components
Main article: Piston/Technical components
Pistons have 2 technical blocks that cannot be obtained. These include the piston head and moving piston blocks.

## Data values
### ID
Java Edition:

| Name   | Identifier | Form         | Block tags | Translation key        |
|--------|------------|--------------|------------|------------------------|
| Piston | piston     | Block & Item | None       | block.minecraft.piston |

Bedrock Edition:

| Name   | Identifier | Alias ID | Numeric ID | Form                       | Item ID[i 1]   | Translation key  |
|--------|------------|----------|------------|----------------------------|----------------|------------------|
| Piston | piston     | None     | 33         | Block & Giveable Item[i 2] | Identical[i 3] | tile.piston.name |


↑ ID of block's direct item form, which is used in savegame files and addons.

↑ Available with /give command.

↑ The block's direct item form has the same id as the block.


| Name                | Savegame ID |
|---------------------|-------------|
| Piston block entity | PistonArm   |

### Block states
See also: Block states

The piston block uses following block states:

Java Edition:

| Name     | Default value | Allowed values           | Description                                                                                                          |
|----------|---------------|--------------------------|----------------------------------------------------------------------------------------------------------------------|
| extended | false         | falsetrue                | If true, the piston is extended.                                                                                     |
| facing   | north         | downeastnorthsouthupwest | The direction the piston head is pointing.The opposite from the direction the player faces while placing the piston. |

Bedrock Edition:

| Name             | Metadata Bits | Default value | Allowed values | Values forMetadata Bits | Description                                                                                                                    |
|------------------|---------------|---------------|----------------|-------------------------|--------------------------------------------------------------------------------------------------------------------------------|
| facing_direction | 0x10x20x4     | 0             | 012345         | 012345                  | The direction the piston is pointing.0: facing down 1: facing up 2: facing south 3: facing north 4: facing east 5: facing west |

### Block data

  

This feature is exclusive to  Bedrock Edition. 


In Bedrock Edition, a piston has a block entity associated with it that holds additional data about the block.

See Bedrock Edition level format/Block entity format.
## See also
- Slime block
- Redstone
- Tutorials/Piston uses
- Tutorials/Headless pistons
- Mechanics/Redstone/Piston circuits

## Notes

↑  Dragon eggs can be pushed, when in a falling state.

↑ In Java Edition, item frames are entities, 
not blocks. In Bedrock Edition, they are blocks.

↑ In Java Edition, if the "Fixed" NBT tag is set to "1", the item frame does not break when attempting to push it using a piston, but it still does not push. If the "Invulnerable" NBT tag is set to "1", the item frame breaks when pushed.

↑ Paintings are technically entities, not blocks.


