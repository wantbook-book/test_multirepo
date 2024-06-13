# Dead Coral Fan
Dead coral fans are the dead variants of coral fans. There are five variants total: tube, brain, bubble, fire, and horn.

## Contents
- 1 Obtaining
	- 1.1 Breaking
	- 1.2 Natural generation
	- 1.3 Post-generation
	- 1.4 Wall dead coral fans
- 2 Usage
	- 2.1 Placement
	- 2.2 Pushing with pistons
- 3 Sounds
- 4 Data values
	- 4.1 ID
	- 4.2 Block states
- 5 History
	- 5.1 Asset history
- 6 Issues
- 7 References

## Obtaining
### Breaking
Dead coral fans can be mined instantly but can be obtained only when mined with a Silk Touch enchanted tool.

In Java Edition, dead coral can only be obtained with a Silk Touch pickaxe.[1]

| Block    | Dead Coral Fan      |
|----------|---------------------|
| Hardness | 0                   |
|          | Breakingtime (secs) |
| Default  | 0.05                |

### Natural generation
Dead coral fans‌[Bedrock Edition  only] naturally generate in coral reef structures. On Java Edition, dead coral fans do not generate naturally.

### Post-generation
Dead coral fans can be obtained by placing live coral fans outside of water, and it turns into its respective dead variant immediately‌[Bedrock Edition  only] or after a few seconds‌[Java Edition  only].

### Wall dead coral fans
Wall dead coral fans cannot be obtained through vanilla means. In Java Edition, they are completely unobtainable, but in Bedrock Edition, they can be obtained through add-ons or inventory editing, though the item form is badly glitched to the point of being completely nameless.

## Usage
Dead coral fans can be used for building or as decoration blocks. It is not possible to turn a dead coral fan back into a live coral fan.

### Placement
All dead coral fans can be placed on the four sides and the top surface of blocks; they cannot be placed on the bottom surface.

### Pushing with pistons
Dead coral fans can be pushed by pistons as long as they are still "supported" in the new position (not floating).

## Data values
### ID
Java Edition:

| Name                       | Identifier                   | Form         | Block tags         | Translation key                              |
|----------------------------|------------------------------|--------------|--------------------|----------------------------------------------|
| Dead Tube Coral Fan        | `dead_tube_coral_fan`        | Block & Item | `mineable/pickaxe` | `block.minecraft.dead_tube_coral_fan`        |
| Dead Brain Coral Fan       | `dead_brain_coral_fan`       | Block & Item | `mineable/pickaxe` | `block.minecraft.dead_brain_coral_fan`       |
| Dead Bubble Coral Fan      | `dead_bubble_coral_fan`      | Block & Item | `mineable/pickaxe` | `block.minecraft.dead_bubble_coral_fan`      |
| Dead Fire Coral Fan        | `dead_fire_coral_fan`        | Block & Item | `mineable/pickaxe` | `block.minecraft.dead_fire_coral_fan`        |
| Dead Horn Coral Fan        | `dead_horn_coral_fan`        | Block & Item | `mineable/pickaxe` | `block.minecraft.dead_horn_coral_fan`        |
| Dead Tube Coral Wall Fan   | `dead_tube_coral_wall_fan`   | Block        | `mineable/pickaxe` | `block.minecraft.dead_tube_coral_wall_fan`   |
| Dead Brain Coral Wall Fan  | `dead_brain_coral_wall_fan`  | Block        | `mineable/pickaxe` | `block.minecraft.dead_brain_coral_wall_fan`  |
| Dead Bubble Coral Wall Fan | `dead_bubble_coral_wall_fan` | Block        | `mineable/pickaxe` | `block.minecraft.dead_bubble_coral_wall_fan` |
| Dead Fire Coral Wall Fan   | `dead_fire_coral_wall_fan`   | Block        | `mineable/pickaxe` | `block.minecraft.dead_fire_coral_wall_fan`   |
| Dead Horn Coral Wall Fan   | `dead_horn_coral_wall_fan`   | Block        | `mineable/pickaxe` | `block.minecraft.dead_horn_coral_wall_fan`   |

Bedrock Edition:

| Name                                      | Identifier                                     | Alias ID             | Numeric ID | Form                         | Item ID[i 1]   | Translation key                                                                                                                                                                                        |
|-------------------------------------------|------------------------------------------------|----------------------|------------|------------------------------|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Dead Coral Fan                            | `coral_fan_dead‌[until BE 1.20.80]`            | None                 | `-134`     | Block & Giveable Item[i 2]   | Identical[i 3] | `tile.coral_fan_dead.blue_fan.name`<br/>`tile.coral_fan_dead.pink_fan.name`<br/>`tile.coral_fan_dead.purple_fan.name`<br/>`tile.coral_fan_dead.red_fan.name`<br/>`tile.coral_fan_dead.yellow_fan.name` |
| Dead Tube Coral Fan                       | `dead_tube_coral_fan‌[upcoming: BE 1.20.80]`   | `coral_fan_dead / 0` | `-134`     | Block & Giveable Item[i 2]   | Identical[i 3] | `tile.coral_fan_dead.blue_fan.name`                                                                                                                                                                    |
| Dead Brain Coral Fan                      | `dead_brain_coral_fan‌[upcoming: BE 1.20.80]`  | `coral_fan_dead / 1` | `-844`     | Block & Giveable Item[i 2]   | Identical[i 3] | `tile.coral_fan_dead.pink_fan.name`                                                                                                                                                                    |
| Dead Bubble Coral Fan                     | `dead_bubble_coral_fan‌[upcoming: BE 1.20.80]` | `coral_fan_dead / 2` | `-845`     | Block & Giveable Item[i 2]   | Identical[i 3] | `tile.coral_fan_dead.purple_fan.name`                                                                                                                                                                  |
| Dead Fire Coral Fan                       | `dead_fire_coral_fan‌[upcoming: BE 1.20.80]`   | `coral_fan_dead / 3` | `-846`     | Block & Giveable Item[i 2]   | Identical[i 3] | `tile.coral_fan_dead.red_fan.name`                                                                                                                                                                     |
| Dead Horn Coral Fan                       | `dead_horn_coral_fan‌[upcoming: BE 1.20.80]`   | `coral_fan_dead / 4` | `-847`     | Block & Giveable Item[i 2]   | Identical[i 3] | `tile.coral_fan_dead.yellow_fan.name`                                                                                                                                                                  |
| Dead Coral Wall Fan<br/>(tube and brain)  | `coral_fan_hang`                               | None                 | `390`      | Block & Ungiveable Item[i 4] | Identical[i 3] | —                                                                                                                                                                                                      |
| Dead Coral Wall Fan<br/>(bubble and fire) | `coral_fan_hang2`                              | None                 | `391`      | Block & Ungiveable Item[i 4] | Identical[i 3] | —                                                                                                                                                                                                      |
| Dead Coral Wall Fan<br/>(horn)            | `coral_fan_hang3`                              | None                 | `392`      | Block & Ungiveable Item[i 4] | Identical[i 3] | —                                                                                                                                                                                                      |

1. ↑ID of block's direct item form, which is used in savegame files and addons.
2. ↑ a b c d e fAvailable with /give command.
3. ↑ a b c d e f g h iThe block's direct item form has the same id as the block.
4. ↑ a b cUnavailable with /give command

### Block states
See also: Block states

Java Edition
Floor:

| Name        | Default value | Allowed values     | Description                                                       |
|-------------|---------------|--------------------|-------------------------------------------------------------------|
| waterlogged | `true`        | `false`<br/>`true` | Whether or not there's water in the same place as this coral fan. |

Wall:

| Name        | Default value | Allowed values                            | Description                                                                                                                                                    |
|-------------|---------------|-------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| facing      | `north`       | `east`<br/>`north`<br/>`south`<br/>`west` | The direction in which the coral fan juts out from the block it is attached to.<br/>For example, a coral fan facing north is attached to a block to its south. |
| waterlogged | `true`        | `false`<br/>`true`                        | Whether or not there's water in the same place as this coral fan.                                                                                              |

Bedrock Edition
Floor:

| Name                | Metadata Bits             | Default value | Allowed values | Values forMetadata Bits | Description                                                  |
|---------------------|---------------------------|---------------|----------------|-------------------------|--------------------------------------------------------------|
| coral_color         | `0x1`<br/>`0x2`<br/>`0x4` | `blue`        | `blue`         | `0`                     | Tube Coral Fan                                               |
|                     |                           |               | `pink`         | `1`                     | Brain Coral Fan                                              |
|                     |                           |               | `purple`       | `2`                     | Bubble Coral Fan                                             |
|                     |                           |               | `red`          | `3`                     | Fire Coral Fan                                               |
|                     |                           |               | `yellow`       | `4`                     | Horn Coral Fan                                               |
| coral_fan_direction | `0x8`                     | `0`           | `0`<br/>`1`    | `0`<br/>`1`             | The direction the coral is facing. East-west or north-south. |

Wall:

| Name                | Metadata Bits   | Default value | Allowed values              | Values forMetadata Bits     | Description                                                                                                                                                                    |
|---------------------|-----------------|---------------|-----------------------------|-----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| coral_hang_type_bit | `0x1`           | `false`       | `false`<br/>`true`          | `0`<br/>`1`                 | Which coral it is; depends on the ID.<br/>For`hang`false means tube and true means brain.<br/>For`hang2`false means bubble and true means fire.<br/>For`hang3`false mean horn. |
| coral_direction     | `0x4`<br/>`0x8` | `0`           | `0`<br/>`1`<br/>`2`<br/>`3` | `0`<br/>`1`<br/>`2`<br/>`3` | The direction the top of the fan is facing.0: west<br/>1: east<br/>2: north<br/>3: south<br/>                                                                                  |
| dead_bit            | `0x2`           | `false`       | `false`<br/>`true`          | `0`<br/>`1`                 | Whether or not this coral is dead.                                                                                                                                             |



