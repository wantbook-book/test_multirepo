## Data values
### ID
Java Edition:

| Name        | Identifier  | Form         | Block tags                                    | Translation key             |
|-------------|-------------|--------------|-----------------------------------------------|-----------------------------|
| Short Grass | short_grass | Block & Item | azalea_log_replaceablelush_plants_replaceable | block.minecraft.short_grass |

Bedrock Edition:

| Name  | Identifier                        | Alias ID      | Numeric ID | Form                       | Item ID[i 1]   | Translation key           |
|-------|-----------------------------------|---------------|------------|----------------------------|----------------|---------------------------|
| Grass | tallgrass                         | None          | 31         | Block & Giveable Item[i 2] | Identical[i 3] | tile.tallgrass.grass.name |
| Grass | short_grass‌[upcoming: BE 1.21.0] | tallgrass / 0 | 31         | Block & Giveable Item[i 2] | Identical[i 3] | tile.tallgrass.grass.name |


↑ ID of block's direct item form, which is used in savegame files and addons.

↑ a b Available with /give command.

↑ a b The block's direct item form has the same id as the block.


### Block states
See also: Block states

Bedrock Edition:

| Name            | Metadata Bits | Default value | Allowed values | Values forMetadata Bits | Description                                                                                         |
|-----------------|---------------|---------------|----------------|-------------------------|-----------------------------------------------------------------------------------------------------|
| tall_grass_type | 0x10x2        | default       | default        | 0                       | Fern(Unused variant which looks identical to grass, but turns into alarge fernwhenbone mealis used) |
|                 |               |               | tall           | 1                       | Grass                                                                                               |
|                 |               |               | fern           | 2                       | Fern                                                                                                |
|                 |               |               | snow           | 3                       | Fern (looks identical to actual fern, but turns intodouble tallgrasswhenbone mealis used)           |

## See also
- Shrub


