# Ladder
Ladders are solid blocks used for climbing walls either vertically or horizontally. They can be placed only on the sides of other blocks.

## Contents
- 1 Obtaining
	- 1.1 Breaking
	- 1.2 Natural generation
	- 1.3 Crafting
- 2 Usage
	- 2.1 Placement
	- 2.2 Climbing
	- 2.3 Fuel
- 3 Sounds
- 4 Data values
	- 4.1 ID
	- 4.2 Block states
- 5 History
- 6 Issues
- 7 Trivia
- 8 Gallery
	- 8.1 Renders
	- 8.2 Screenshots
- 9 References

## Obtaining
### Breaking
Ladders can be broken using any tool, but an axe is the quickest.

| Block     | Ladder                |
|-----------|-----------------------|
| Hardness  | 0.4                   |
| Tool      |                       |
|           | Breakingtime (sec)[A] |
| Default   | 0.6                   |
| Wooden    | 0.3                   |
| Stone     | 0.15                  |
| Iron      | 0.1                   |
| Diamond   | 0.1                   |
| Netherite | 0.1                   |
| Golden    | 0.05                  |

1. ↑Times are for unenchanted tools as used by players with no status effects, measured in seconds. For more information, see Breaking Speed.

### Natural generation
Ladders occur naturally in library rooms of strongholds and in intersection rooms with a wooden ceiling. Ladders can also be found in village structures such as plains and taiga temples and many small or medium houses, as well as in churches. They may also be found leading to the basements of igloos, in end ships on the pillar leading up to the crow's nest, and in rail rooms of woodland mansions. Ladders also generate in ancient cities and in trail ruins.

### Crafting
| Ingredients | Crafting recipe |
|-------------|-----------------|
| Stick       | 3               |

## Usage
Ladders provide a way to cushion a player's impact after a free fall. Upon entering a ladder's area of effect, the player's speed is reduced instantly to normal ladder descent speed and no damage is taken. Falling onto the narrow top surface of the ladder incurs falling damage as normal.

Holding the sneak key while climbing a ladder causes the player to grab hold of the ladder and not fall off. While the player is holding on to a ladder, mining speed decreases.

Any mob can climb a ladder in the same way a player does: by pushing against it. Mobs are not smart enough to use ladders deliberately — they do not remain on a ladder to get somewhere, but a ladder directly in their path lets them climb up.

### Placement
Ladders can be placed on any full solid block face.

Ladders displace lava blocks to create an air pocket and can be used instead of glass to let lava light shine through a ceiling. They also displace flowing water, but a ladder placed inside a water source block becomes waterlogged and does not create an air pocket.

### Climbing
A ladder takes effect whenever the player's lower half is in the block occupied by a ladder. These effects are:

- If the player pushes against a wall, the player moves upward at about 2.35 blocks per second instead of horizontally. (Thus inside a 1×1 ladder shaft, the player can use any movement key to move upward.)
- If a player occupies the 1×1 ladder shaft, the player can ascend the ladder by holdingjumpinstead of using a horizontal movement key.
- If a player moving perpendicular to the ladder block enters the ladder block, the player begins to move upward, but then falls off the ladder shortly afterward if the player continues to move horizontally.
- The player's maximum downward speed is reduced to a "descending ladder" speed, at about 3 blocks per second.
- The player's horizontal movement friction is the same as onice. (That is, moving around in the tiny space the player is in while still hanging on the ladder at the same level.)

Additionally:

- In Bedrock Edition, a player can hold down the jump button while climbing a ladder to make the climbing speed faster.
- Also in Bedrock Edition, waterlogged ladders cannot be climbed.
- InJava Edition, when atrapdoorsatisfies the following conditions, it also becomes climbable:
	- The trapdoor is placed directly above a ladder.
	- The trapdoor is opened.
	- The trapdoor and the ladder directly below it face the same direction.
- A player on aslabin front of the ladder must jump to get on the ladder despite being only 1/2 block down.
- Likevines, ladders slow the player down when walked through.
- Consumingfood, blocking with ashieldor pulling back abow, do not slow the player down while climbing ladders (unlike whenwalking,sprintingandswimming).[1]

### Fuel
A ladder can be used as fuel in furnaces, smelting 1.5 items per ladder.‌[Java Edition  only]

## Data values
### ID
Java Edition:

| Name   | Identifier | Form         | Block tags  | Translation key          |
|--------|------------|--------------|-------------|--------------------------|
| Ladder | `ladder`   | Block & Item | `climbable` | `block.minecraft.ladder` |

Bedrock Edition:

| Name   | Identifier | Numeric ID | Form                       | Item ID[i 1]   | Translation key    |
|--------|------------|------------|----------------------------|----------------|--------------------|
| Ladder | `ladder`   | `65`       | Block & Giveable Item[i 2] | Identical[i 3] | `tile.ladder.name` |

1. ↑ID of block's direct item form, which is used in savegame files and addons.
2. ↑Available with /give command.
3. ↑The block's direct item form has the same id as the block.

### Block states
See also: Block states

Java Edition:

| Name        | Default value | Allowed values                            | Description                                                            |
|-------------|---------------|-------------------------------------------|------------------------------------------------------------------------|
| facing      | `north`       | `east`<br/>`north`<br/>`south`<br/>`west` | The direction from the block the ladder is attached to, to the ladder. |
| waterlogged | `false`       | `false`<br/>`true`                        | Whether or not there's water in the same place as this ladder.         |

Bedrock Edition:

| Name             | Metadata Bits             | Default value | Allowed values              | Values forMetadata Bits     | Description                                                                                                                                                                      |
|------------------|---------------------------|---------------|-----------------------------|-----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| facing_direction | `0x1`<br/>`0x2`<br/>`0x4` | `2`           | `2`<br/>`3`<br/>`4`<br/>`5` | `2`<br/>`3`<br/>`4`<br/>`5` | The direction from the block the ladder is attached to, to the ladder.2: Ladder facing north<br/>3: Ladder facing south<br/>4: Ladder facing west<br/>5: Ladder facing east<br/> |
|                  |                           |               | `0`<br/>`1`                 | `0`<br/>`1`                 | Unused                                                                                                                                                                           |

