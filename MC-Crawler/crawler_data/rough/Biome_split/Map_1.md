#### Other dimensions
While maps in the Nether work, they show only a red-and-gray pattern, regardless of the blocks placed. The only useful function is finding where the player is in relation to framed copies, which show as green pointers. Additionally, the player pointer rapidly spins and is not a good indicator of direction. In Java Edition, banner markers placed in the Nether still show on the map as usual. Despite its unreliability, having a mapped trail can still be useful in some cases, such as while riding a strider over lava. Maps in the End work as usual, mapping the terrain and showing the accurate location and direction of the player.

In Java Edition, holding a map from the Overworld in a different dimension shows the player's last position and direction in the Overworld. This effect is temporary, and the marker disappears after quitting and joining the world/server again.

In Bedrock Edition, an Overworld locator map in the Nether shows the player's relative location and direction in the Overworld. Similarly, a Nether locator map in the Overworld shows the player's relative location in the Nether, but the place marker spins. An Overworld locator map in the End shows the world spawn. A Nether locator map cannot be used in the End — the map appears, but the place marker is not shown anywhere — and similarly, an End locator map cannot be used in the Overworld or the Nether. The place marker changes color depending on the dimension that the player is currently in (white for the Overworld, red for the Nether, and magenta for the End).

### Zooming out
Zooming out a map in a cartography table
A map can be zoomed out up to 4 times, increasing the covered area from 128×128 blocks up to a maximum of 2048×2048 blocks. An empty map cannot be zoomed out; it needs to be activated for the zooming to be possible. Changing the zoom level of a map resets its contents, and terrain needs to be explored again to be drawn on the zoomed out map.

Locked maps cannot be zoomed out.

| Ingredients    | Crafting recipe | Description                       |
|----------------|-----------------|-----------------------------------|
| Paper+<br/>Map |                 | Locked maps cannot be zoomed out. |

| Name                            | Ingredients                   | Anvil usage                   | Description                                                                                       |
|---------------------------------|-------------------------------|-------------------------------|---------------------------------------------------------------------------------------------------|
| Map or Locator Map (zoomed out) | Mapor Locator Map +<br/>Paper | Repair & Name MapLocator Map8 | Bedrock Editiononly.Supplying 8 sheets of paper results in a zoomed-out version of the input map. |

#### Zoom details
The zooming function starts from when the map is created (zoom level 0/4) up to its fourth zoom step (zoom level 4/4).

|                                             |                                      | Zoom step 0    | Zoom step 1        | Zoom step 2         | Zoom step 3         | Zoom step 4                      |
|---------------------------------------------|--------------------------------------|----------------|--------------------|---------------------|---------------------|----------------------------------|
|                                             |                                      |                |                    |                     |                     |                                  |
|                                             | Zoom level                           | 0/4            | 1/4                | 2/4                 | 3/4                 | 4/4                              |
|                                             | 1 map pixel represents               | 1 block        | 4 blocks2×2 blocks | 16 blocks4×4 blocks | 64 blocks8×8 blocks | 256 blocks (1 chunk)16×16 blocks |
|                                             | Scaling ratio                        | 1:1            | 1:2                | 1:4                 | 1:8                 | 1:16                             |
|                                             | Map covers an area of                | 128×128 blocks | 256×256 blocks     | 512×512 blocks      | 1024×1024 blocks    | 2048×2048 blocks                 |
|                                             |                                      | 8×8 chunks     | 16×16 chunks       | 32×32 chunks        | 64×64 chunks        | 128×128 chunks                   |
| Total paper needed to zoom out from Level 0 | in anvil‌[BE  only]or crafting table | -              | 8                  | 16                  | 24                  | 32                               |
|                                             | in cartography table                 | -              | 1                  | 2                   | 3                   | 4                                |

Maps are always aligned to a grid at all zoom levels. That means zooming out any different map in a specific area covered by that map always has the same center. As such, maps are aligned by map width (1024 blocks for a level 3 map) minus 64. A level 3 map generated at X=0 Z=0 covers X and Z coordinates from -64 to 959. All maps generated in this area zoom out to the same coordinates, guaranteeing that they are always 'aligned' on a map wall. For a zoomed-out map to cover a new area, it must start with a base (level 0) map that is in that area.

At zoom level 0, a map created on the point (0,0) has (0,0) at the center of the map. At higher zoom levels of the same map, the coordinate (0,0) is in the top left square of the map.

In Java Edition, the zoom level and the scaling factor are displayed in the tooltip of a map by turning on advanced tooltips (a debug option that can be toggled by using the key combination F3 + H). In Bedrock Edition, the zoom level of a map is always displayed it its tooltip.

### Cloning
Cloning a map in a cartography table
A map can be cloned to create multiple synchronized copies linked to the same map data. Multiple players can hold clones of the same map to record different parts of the world simultaneously.

Upon cloning a map, the parts of the world that have already been explored and mapped are copied; thereafter, newly explored areas appear on all cloned instances automatically. The resulting copies have the same zoom level as the starting map. If one of the maps is later zoomed out, then that map loses its connection to the original and functions as a completely separate map that has to be individually filled by exploring.

All cloned maps stack with each other, unless renamed. Even if renamed, the mapped areas continue to remain in sync.

In Bedrock Edition, both empty maps and empty locator maps may be used to clone a map. Whether the cloned maps show position markers is dependent only on the input map. For this reason, using an empty locator map instead of an empty map for cloning is a waste of a compass.

A cartography table can also be used to clone a map.

| Ingredients        | Crafting recipe | Description                |
|--------------------|-----------------|----------------------------|
| Empty Map+<br/>Map | 23456789        | Cloned maps are stackable. |

| Name                        | Ingredients                       | Anvil usage                                    | Description                                                                                                                                                                                                 |
|-----------------------------|-----------------------------------|------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Map or Locator Map (cloned) | Mapor Locator Map +<br/>Empty Map | Repair & Name MapLocator MapMapLocator Map2222 | Bedrock Editiononly.Only one copy can be made at a time.The non-empty input map must be a locator map for the output to be a locator map. An empty locator map is the same as an empty map for this recipe. |

In Creative mode, a map in an item frame may be cloned by using pick block on it, as long as that map is not also in the player's inventory.

