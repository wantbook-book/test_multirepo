# Cut Sandstone Slab
A cut sandstone slab is a cut sandstone variant of a slab.

## Contents
- 1 Obtaining
	- 1.1 Breaking
	- 1.2 Crafting
	- 1.3 Stonecutting
- 2 Usage
	- 2.1 Note blocks
- 3 Sounds
- 4 Data values
	- 4.1 ID
	- 4.2 Block states
- 5 History
- 6 Issues
- 7 References

## Obtaining
### Breaking
Cut sandstone slabs can be mined using any pickaxe.

| Block     | Cut Sandstone Slab    |
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


### Crafting
| Ingredients   | Crafting recipe |
|---------------|-----------------|
| Cut Sandstone | 6               |

### Stonecutting
| Ingredients              | Cutting recipe | Description              |
|--------------------------|----------------|--------------------------|
| SandstoneorCut Sandstone | 2              | ‌[Java Edition  only][1] |

## Usage
For information about the placement mechanics of all slabs, see Slab § Usage.

### Note blocks
Cut sandstone slabs can be placed under note blocks to produce "bass drum" sounds.

## Data values
### ID
Java Edition:

| Name               | Identifier         | Form         | Block tags            | Item tags | Translation key                    |
|--------------------|--------------------|--------------|-----------------------|-----------|------------------------------------|
| Cut Sandstone Slab | cut_sandstone_slab | Block & Item | slabsmineable/pickaxe | slabs     | block.minecraft.cut_sandstone_slab |

Bedrock Edition:

| Name                      | Identifier               | Alias ID           | Numeric ID | Form                         | Item ID[i 1]                                             | Translation key                     |
|---------------------------|--------------------------|--------------------|------------|------------------------------|----------------------------------------------------------|-------------------------------------|
| Double Cut Sandstone Slab | double_stone_block_slab4 | double_stone_slab4 | 423        | Block & Ungiveable Item[i 2] | double_stone_block_slab4Alias ID:real_double_stone_slab4 | —                                   |
| Cut Sandstone Slab        | stone_block_slab4        | stone_slab4        | 421        | Block & Giveable Item[i 3]   | stone_block_slab4Alias ID:double_stone_slab4             | tile.stone_slab4.cut_sandstone.name |


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

| Name                    | Metadata Bits | Default value     | Allowed values    | Values forMetadata Bits | Description                         |
|-------------------------|---------------|-------------------|-------------------|-------------------------|-------------------------------------|
| minecraft:vertical_half | Not Supported | bottom            | bottomtop         | Unsupported             | Where the slab is within its block. |
| stone_slab_type_4       | 0x10x20x4     | mossy_stone_brick | mossy_stone_brick | 0                       | Mossy Stone Brick Slab              |
|                         |               |                   | smooth_quartz     | 1                       | Smooth Quartz Slab                  |
|                         |               |                   | stone             | 2                       | Stone Slab                          |
|                         |               |                   | cut_sandstone     | 3                       | Cut Sandstone Slab                  |
|                         |               |                   | cut_red_sandstone | 4                       | Cut Red Sandstone Slab              |



