### Cover
Snow covered grass block, mycelium or podzol.
If the snow is on a grass block (or mycelium or podzol in Java Edition[6]) the ground cover turns white on the top and around the sides. Snow does not damage tilled and hydrated field areas – it cannot be placed on farmland. A gravity-affected block like sand or gravel does not fall if snow covers the block below it, but the gravity-affected block does replace a snow layer when falling onto it. The texture of the grass block changes to snowy when a single layer of snow is placed on top.[7][8] Thicker layers of snow causes the grass block to revert to plain dirt when the block receives a random tick, similar to regular grass when covered by an opaque block. A plain dirt block with a single layer of snow on top gains a snowy texture if grass spreads to it.

Snow layers placed on top of nylium revert it to netherrack.[9]

In Bedrock Edition, if leaves are topped with a layer of snow, particles of snow appear to fall through the leaves from the snow layer.

In Bedrock Edition, snow layers can occupy the same space as one-block flowers, mushrooms, and one-block ferns and short grass, (however two-block tall plants do not work)[10] and can be layered and mined normally. Placing snow on already-existing plant blocks causes snow to appear around them, but placing plants into an area where there is snow removes the snow.[11]

### Melting
Powered redstone lamps melting nearby snow.
Snow melts if there is a heat block,‌[BE & edu  only] or block light level of 12 or more. In Bedrock Edition, it also melts in dry biomes, regardless of block light or daylight level. If there are multiple layers, layers melt gradually in Bedrock Edition, but they melt all at once in Java.

Some light sources can melt snow but many cannot. The melt radius is taxicab distance.

| Item                      | Melt radius |
|---------------------------|-------------|
| Beacon                    | 3           |
| Campfire                  | 3           |
| Soul Campfire             | -           |
| Conduit                   | 3           |
| Glow Lichen               | -           |
| Glowstone                 | 3           |
| Jack o'Lantern            | 3           |
| Lantern                   | 3           |
| Soul Lantern              | -           |
| Lava                      | 3           |
| Redstone Lamp             | 3           |
| Respawn Anchor1/4 Charge  | -           |
| Respawn Anchor 2/4 Charge | -           |
| Respawn Anchor 3/4 Charge | -           |
| Respawn Anchor 4/4 Charge | 3           |
| 1Sea Pickle               | -           |
| 2 Sea Pickles             | -           |
| 3 Sea Pickles             | -           |
| 4 Sea Pickles             | 3           |
| Shroomlight               | 3           |
| Froglight                 | 3           |
| End Rod                   | 2           |
| Torch                     | 2           |
| Soul Torch                | -           |
| Redstone Torch            | -           |
| Ender Chest               | -           |
| Furnace                   | 1           |
| Blast Furnace             | 1           |
| Smoker                    | 1           |
| Crying Obsidian           | -           |
| Magma Block               | -           |
| Brewing Stand             | -           |
| Brown Mushroom            | -           |
| Dragon Egg                | -           |
| Redstone Ore              | -           |
| End Portal Frame          | -           |
| Fire                      | 3           |
| Soul Fire                 | -           |
| Nether Portal             | -           |
| Sea Lantern               | 3           |

### Foxes
When a fox gets stuck in the snow after missing an attack on prey, it emits particles as it emerges from the snow.

## Data values
### ID
Java Edition:

| Name | Identifier | Form         | Block tags                                                  | Translation key        |
|------|------------|--------------|-------------------------------------------------------------|------------------------|
| Snow | `snow`     | Block & Item | `inside_step_sound_blocks`<br/>`snow`<br/>`mineable/shovel` | `block.minecraft.snow` |

Bedrock Edition:

| Name     | Identifier   | Numeric ID | Form                       | Item ID[i 1]   | Translation key        |
|----------|--------------|------------|----------------------------|----------------|------------------------|
| Top Snow | `snow_layer` | `78`       | Block & Giveable Item[i 2] | Identical[i 3] | `tile.snow_layer.name` |

1. ↑ID of block's direct item form, which is used in savegame files and addons.
2. ↑Available with /give command.
3. ↑The block's direct item form has the same id as the block.

### Block states
See also: Block states

Java Edition:

| Name   | Default value | Allowed values                                              | Description                                                                                                                                          |
|--------|---------------|-------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| layers | `1`           | `1`<br/>`2`<br/>`3`<br/>`4`<br/>`5`<br/>`6`<br/>`7`<br/>`8` | The number of layers thick.<br/>Each layer adds two pixels to the block height, and each layer after the first adds two pixels to the collision box. |

Bedrock Edition:

| Name        | Metadata Bits             | Default value | Allowed values                                              | Values forMetadata Bits                                     | Description                                           |
|-------------|---------------------------|---------------|-------------------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------|
| height      | `0x1`<br/>`0x2`<br/>`0x4` | `0`           | `0`<br/>`1`<br/>`2`<br/>`3`<br/>`4`<br/>`5`<br/>`6`<br/>`7` | `0`<br/>`1`<br/>`2`<br/>`3`<br/>`4`<br/>`5`<br/>`6`<br/>`7` | The number of layers in addition to the bottom layer. |
| covered_bit | `0x8`                     | `false`       | `true`<br/>`false`                                          | `0`<br/>`1`                                                 | True if the snow is covering a plant.                 |



## Notes



