# Purpur Slab
A purpur slab is a purpur variant of a slab.

## Contents
- 1 Obtaining
	- 1.1 Breaking
	- 1.2 Natural generation
	- 1.3 Crafting
	- 1.4 Stonecutting
- 2 Usage
	- 2.1 Crafting ingredient
	- 2.2 Note blocks
- 3 Sounds
- 4 Data values
	- 4.1 ID
	- 4.2 Block states
- 5 History
- 6 Issues
- 7 References

## Obtaining
### Breaking
Purpur slabs can be mined using any pickaxe.

| Block     | Purpur Slab           |
|-----------|-----------------------|
| Hardness  | 2                     |
| Tool      |                       |
|           | Breakingtime (sec)[A] |
| Default   | 10                    |
| Wooden    | 1.5                   |
| Stone     | 0.75                  |
| Iron      | 0.5                   |
| Diamond   | 0.4                   |
| Netherite | 0.35                  |
| Golden    | 0.25                  |


↑ Times are for unenchanted tools as used by players with no status effects, measured in seconds. For more information, see Breaking Speed.


### Natural generation
Purpur slabs generate as part of end cities and end ships.

### Crafting
| Ingredients     | Crafting recipe | Description              |
|-----------------|-----------------|--------------------------|
| AnyPurpur Block | 6               | ‌[Java Edition  only]    |
| Purpur Block    | 6               | ‌[Bedrock Edition  only] |

### Stonecutting
| Ingredients  | Cutting recipe |
|--------------|----------------|
| Purpur Block | 2              |

## Usage
For information about the placement mechanics of all slabs, see Slab § Usage.

### Crafting ingredient
| Name          | Ingredients | Crafting recipe |
|---------------|-------------|-----------------|
| Purpur Pillar | Purpur Slab |                 |

### Note blocks
Purpur slabs can be placed under note blocks to produce "bass drum" sounds.

## Data values
### ID
Java Edition:

| Name        | Identifier  | Form         | Block tags            | Item tags | Translation key             |
|-------------|-------------|--------------|-----------------------|-----------|-----------------------------|
| Purpur Slab | purpur_slab | Block & Item | slabsmineable/pickaxe | slabs     | block.minecraft.purpur_slab |

Bedrock Edition:

| Name               | Identifier               | Alias ID           | Numeric ID | Form                         | Item ID[i 1]                                             | Translation key              |
|--------------------|--------------------------|--------------------|------------|------------------------------|----------------------------------------------------------|------------------------------|
| Double Purpur Slab | double_stone_block_slab2 | double_stone_slab2 | 181        | Block & Ungiveable Item[i 2] | double_stone_block_slab2Alias ID:real_double_stone_slab2 | —                            |
| Purpur Slab        | stone_block_slab2        | stone_slab2        | 182        | Block & Giveable Item[i 3]   | stone_block_slab2Alias ID:double_stone_slab2             | tile.stone_slab2.purpur.name |


↑ ID of block's direct item form, which is used in savegame files and addons.

↑ Unavailable with /give command

↑ Available with /give command.


### Block states
See also: Block states

Java Edition:

| Name        | Default value | Allowed values | Description                                                  |
|-------------|---------------|----------------|--------------------------------------------------------------|
| type        | bottom        | bottomtop      | Where the slab is within its block.                          |
|             |               | double         | The block is a double slab.                                  |
| waterlogged | false         | falsetrue      | Whether or not there's water in the same place as this slab. |

Bedrock Edition:

| Name                    | Metadata Bits | Default value | Allowed values    | Values forMetadata Bits | Description                         |
|-------------------------|---------------|---------------|-------------------|-------------------------|-------------------------------------|
| minecraft:vertical_half | Not Supported | bottom        | bottomtop         | Unsupported             | Where the slab is within its block. |
| stone_slab_type_2       | 0x10x20x4     | red_sandstone | red_sandstone     | 0                       | Red Sandstone Slab                  |
|                         |               |               | purpur            | 1                       | Purpur Slab                         |
|                         |               |               | prismarine_rough  | 2                       | Prismarine Slab                     |
|                         |               |               | prismarine_dark   | 3                       | Dark Prismarine Slab                |
|                         |               |               | prismarine_brick  | 4                       | Prismarine Brick Slab               |
|                         |               |               | mossy_cobblestone | 5                       | Mossy Cobblestone Slab              |
|                         |               |               | smooth_sandstone  | 6                       | Smooth Sandstone Slab               |
|                         |               |               | red_nether_brick  | 7                       | Red Nether Brick Slab               |




