# Nether Brick Slab
A nether brick slab is a nether brick variant of a slab.

## Contents
- 1 Obtaining
	- 1.1 Breaking
	- 1.2 Crafting
	- 1.3 Stonecutting
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
Nether brick slabs can be mined using any pickaxe.

| Block     | Nether Brick Slab     |
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

1. ↑Times are for unenchanted tools as used by players with no status effects, measured in seconds. For more information, see Breaking Speed.

### Crafting
| Ingredients   | Crafting recipe |
|---------------|-----------------|
| Nether Bricks | 6               |

### Stonecutting
| Ingredients   | Cutting recipe |
|---------------|----------------|
| Nether Bricks | 2              |

## Usage
For information about the placement mechanics of all slabs, see Slab § Usage.

### Crafting ingredient
| Name                   | Ingredients       | Crafting recipe |
|------------------------|-------------------|-----------------|
| Chiseled Nether Bricks | Nether Brick Slab |                 |

### Note blocks
Nether brick slabs can be placed under note blocks to produce "bass drum" sounds.

## Data values
### ID
Java Edition:

| Name              | Identifier          | Form         | Block tags                     | Item tags | Translation key                     |
|-------------------|---------------------|--------------|--------------------------------|-----------|-------------------------------------|
| Nether Brick Slab | `nether_brick_slab` | Block & Item | `slabs`<br/>`mineable/pickaxe` | `slabs`   | `block.minecraft.nether_brick_slab` |

Bedrock Edition:

| Name                     | Identifier                | Alias ID            | Numeric ID | Form                         | Item ID[i 1]                                                    | Translation key                            |
|--------------------------|---------------------------|---------------------|------------|------------------------------|-----------------------------------------------------------------|--------------------------------------------|
| Double Nether Brick Slab | `double_stone_block_slab` | `double_stone_slab` | `43`       | Block & Ungiveable Item[i 2] | `double_stone_block_slab`<br/>Alias ID:`real_double_stone_slab` | `tile.double_stone_slab.nether_brick.name` |
| Nether Brick Slab        | `stone_block_slab`        | `stone_slab`        | `44`       | Block & Giveable Item[i 3]   | `stone_block_slab`<br/>Alias ID:`double_stone_slab`             | `tile.stone_slab.nether_brick.name`        |

1. ↑ID of block's direct item form, which is used in savegame files and addons.
2. ↑Unavailable with /give command
3. ↑Available with /give command.

### Block states
See also: Block states

Java Edition:

| Name        | Default value | Allowed values     | Description                                                  |
|-------------|---------------|--------------------|--------------------------------------------------------------|
| type        | `bottom`      | `bottom`<br/>`top` | Where the slab is within its block.                          |
|             |               | `double`           | The block is a double slab.                                  |
| waterlogged | `false`       | `false`<br/>`true` | Whether or not there's water in the same place as this slab. |

Bedrock Edition:

| Name                    | Metadata Bits             | Default value  | Allowed values     | Values forMetadata Bits | Description                         |
|-------------------------|---------------------------|----------------|--------------------|-------------------------|-------------------------------------|
| minecraft:vertical_half | Not Supported             | `bottom`       | `bottom`<br/>`top` | `Unsupported`           | Where the slab is within its block. |
| stone_slab_type         | `0x1`<br/>`0x2`<br/>`0x4` | `smooth_stone` | `smooth_stone`     | `0`                     | Smooth Stone Slab                   |
|                         |                           |                | `sandstone`        | `1`                     | Sandstone Slab                      |
|                         |                           |                | `wood`             | `2`                     | Petrified Oak Slab                  |
|                         |                           |                | `cobblestone`      | `3`                     | Cobblestone Slab                    |
|                         |                           |                | `brick`            | `4`                     | Brick Slab                          |
|                         |                           |                | `stone_brick`      | `5`                     | Stone Brick Slab                    |
|                         |                           |                | `quartz`           | `6`                     | Quartz Slab                         |
|                         |                           |                | `nether_brick`     | `7`                     | Nether Brick Slab                   |



