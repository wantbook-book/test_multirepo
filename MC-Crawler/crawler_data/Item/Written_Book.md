# Written Book
A written book is an item created after a book and quill is signed.

## Contents
- 1 Obtaining
	- 1.1 Signing a book and quill
	- 1.2 Copying
- 2 Usage
	- 2.1 Lecterns
	- 2.2 Chiseled bookshelf
- 3 Sounds
- 4 Data values
	- 4.1 ID
	- 4.2 Item data
- 5 History
- 6 Issues
- 7 Trivia
- 8 Gallery
	- 8.1 Textures
	- 8.2 Screenshots
- 9 See also

## Obtaining
### Signing a book and quill
Written books can be obtained by signing a book and quill. After it has been signed, it cannot be edited again. The label does not say "Written Book", but whatever the player titles it. The title appears on the top line of the label, and "by <player>" (the player's username) on the bottom. In Bedrock Edition, this is customizable without commands.

### Copying
A signed written book can be be copied using a crafting table. Books have four generations: "Original", "Copy of Original", "Copy of Copy", and "Tattered". Only books of the generations "Original" and "Copy of Original" may be copied, creating the "Copy of Original" and "Copy of Copy" generations respectively. Books of the generation "Copy of Copy" may not be copied. The "Tattered" generation is unused in normal gameplay.

| SourceGeneration | Copiable? | OutcomeGeneration |
|------------------|-----------|-------------------|
| Original         | Yes       | Copy of Original  |
| Copy of Original | Yes       | Copy of Copy      |
| Copy of Copy     | No        | N/A               |
| Tattered         | No        | N/A               |

| Ingredients                 | Crafting recipe | Description                                                                                                                                                                                                                                                                                                                  |
|-----------------------------|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Book and Quill+Written Book | 2345678         | The input written book is not consumed.The new copies are "Copy of Original" or "Copy of Copy", depending on whether the input written book is "Original" or "Copy of Original".Copies of copies cannot be copied.Copied books of the same generation ("Original", "Copy of Original", "Copy of Copy", or "Tattered") stack. |

## Usage
Written books can be opened by pressing the use control (or holding down on the touchscreen in Bedrock Edition), and display a GUI allowing the player to read it or turn the page.

The contents of a book are an extra set of data attached to the item. This means that when a book is destroyed, its contents are lost with it.

### Lecterns
One can place a written book on an empty lectern.

The lectern then emits a redstone signal depending on the displayed page in the book. On the last page, the lectern emits a signal strength of 15.

### Chiseled bookshelf
Using the chiseled bookshelf while having a written book in the main hand puts the book inside the chiseled bookshelf.

## Data values
### ID
Java Edition:

| Name         | Identifier   | Form | Item tags                    | Translation key             |
|--------------|--------------|------|------------------------------|-----------------------------|
| Written Book | written_book | Item | bookshelf_bookslectern_books | item.minecraft.written_book |

Bedrock Edition:

| Name         | Identifier   | Numeric ID | Form | Item tags                                        | Translation key        |
|--------------|--------------|------------|------|--------------------------------------------------|------------------------|
| Written Book | written_book | 511        | Item | minecraft:bookshelf_booksminecraft:lectern_books | item.written_book.name |

### Item data
Java Edition:

Main article: Item format

 tag: The item's tag tag.
 filtered_pages: Only in Realms. The pages shown to players with the profanity filter turned on instead of some of the regular pages. This compound is automatically given a tag named after the page number and set to "" when a player with the profanity filter turned off closes or signs a book with that specific page containing one or more blocked words, so players with the filter on cannot see the blocked words. If a player with the filter on tries to use blocked words in one or more of the pages, this compound is not given any new tags and the specific page(s) in  pages are instead set to "", which makes the page(s) render completely blank. If multiple pages have been edited before the book is closed, only the pages containing blocked words are blanked.
 filtered_title: Only in Realms. The title shown to players with the profanity filter turned on instead of the regular title. This tag is automatically set to "" when a player with the profanity filter turned off signs a book with a title containing one or more blocked words, so players with the filter on cannot see the blocked words. If a player with the filter on tries to use blocked words in the title, this tag is not added and the  title tag is instead set to "", which makes the title render as "Written Book", as if it weren't named.
 resolved: Optional. Created and set to 1 when the book (or a book from the stack) is opened for the first time after being created. Used to determine whether to resolve advanced components within JSON, because their values become fixed at that point.
 generation: Optional. The copy tier of the book. 0 = original, 1 = copy of original, 2 = copy of copy, 3 = tattered. If the value is greater than 1, the book cannot be copied. Does not exist for original books. If this tag is missing, it is assumed the book is an original. 'Tattered' is unused in normal gameplay, and functions identically to the 'copy of copy' tier.
 author: The author of the written book.
 title: The title of the written book. Lower priority than the item name set by tag.display.Name. Cannot be used to open locked containers.
 pages: The list of pages in the book.
: A single page in the book. Each page is a serialized JSON text.

Bedrock Edition:

See Bedrock Edition level format/Item format.
## See also
- Book
- Bookshelf
- Book and Quill
- Formatting Codes

| Tools, weapons, and armor |                                                                                                                                                                       |
|---------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Tools                     | Axe Brush Elytra Fishing Rod Carrot on a Stick Warped Fungus on a Stick Flint and Steel Hoe Pickaxe Shears ShovelBE & EE only   Glow Stick                            |
| BE&EEonly                 | Glow Stick                                                                                                                                                            |
| Weapons                   | Arrow Tipped Axe Bow Crossbow Egg Fire Charge Shield Snowball Sword TridentJava Edition only   Spectral Arrow   BE & EE only   Ice Bomb   Upcoming   Mace Wind Charge |
| Java Editiononly          | Spectral Arrow                                                                                                                                                        |
| BE&EEonly                 | Ice Bomb                                                                                                                                                              |
| Upcoming                  | Mace Wind Charge                                                                                                                                                      |
| Armor                     | Boots Chestplate Helmet Turtle Shell Horse Armor LeggingsUpcoming   Wolf Armor                                                                                        |
| Upcoming                  | Wolf Armor                                                                                                                                                            |

| BE & EE only | Glow Stick |
|--------------|------------|

| Java Edition only | Spectral Arrow   |
|-------------------|------------------|
| BE&EEonly         | Ice Bomb         |
| Upcoming          | Mace Wind Charge |

| Upcoming | Wolf Armor |
|----------|------------|

| Utilities        |                                                                                                                                                                                                                                                                                                                                                                                             |
|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Vehicles         | Boat with Chest Minecart with Chest with Hopper with TNTJava Edition only   Minecart with Furnace                                                                                                                                                                                                                                                                                           |
| Java Editiononly | Minecart with Furnace                                                                                                                                                                                                                                                                                                                                                                       |
| Aesthetic        | Item Frame Glow Painting                                                                                                                                                                                                                                                                                                                                                                    |
| Music Discs      | 13 Cat Blocks Chirp Far Mall Mellohi Stal Strad Ward 11 Wait Otherside 5 Pigstep Relic                                                                                                                                                                                                                                                                                                      |
| Informational    | Book and Quill Written Clock Compass Recovery Map Empty Explorer Name Tag Spyglass                                                                                                                                                                                                                                                                                                          |
| Utility          | Armor Stand Bone Meal Bottle o' Enchanting Bowl Bucket Water Lava Milk Powder Snow Axolotl Cod Pufferfish Salmon Tadpole Tropical Fish Enchanted Books End Crystal Eye of Ender Firework Rocket Glass Bottle Water Potion Lingering Splash Goat Horn Lead Saddle Totem of UndyingBE & EE only   Balloon    Medicine Sparkler Super Fertilizer   Upcoming   Ominous Bottle Trial Key Ominous |
| BE&EEonly        | Balloon    Medicine Sparkler Super Fertilizer                                                                                                                                                                                                                                                                                                                                               |
| Upcoming         | Ominous Bottle Trial Key Ominous                                                                                                                                                                                                                                                                                                                                                            |

| Java Edition only | Minecart with Furnace |
|-------------------|-----------------------|

| BE & EE only | Balloon    Medicine Sparkler Super Fertilizer |
|--------------|-----------------------------------------------|
| Upcoming     | Ominous Bottle Trial Key Ominous              |

| Food         |                                                                                                                  |
|--------------|------------------------------------------------------------------------------------------------------------------|
| Natural      | Apple Beetroot Carrot Chorus Fruit Glow Berries Melon Slice Sweet Berries Potato Baked Poisonous Spider Eye      |
| Rawmeat      | Raw Beef Raw Chicken Raw Mutton Raw Porkchop Raw Rabbit Raw Cod Raw Salmon Tropical Fish Pufferfish Rotten Flesh |
| Cookedmeat   | Steak Cooked Chicken Cooked Mutton Cooked Porkchop Cooked Rabbit Cooked Cod Cooked Salmon                        |
| Crafted      | Bread Cookie Dried Kelp Honey Bottle Mushroom Stew Beetroot Rabbit Suspicious Pumpkin Pie                        |
| Supernatural | Golden Apple Enchanted Golden Carrot                                                                             |

| Ingredients        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Seeds              | Beetroot Seeds Cocoa Beans Melon Seeds Pitcher Pod Pumpkin Seeds Torchflower Seeds Wheat Seeds                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Raw materials      | Amethyst Shard Blaze Rod Bone Clay Ball Coal Diamond Disc Fragment 5 Dragon's Breath Echo Shard Emerald Ender Pearl Feather Flint Ghast Tear Glowstone Dust Gunpowder Heart of the Sea Honeycomb Ink Sac Glow Lapis Lazuli Leather Magma Cream Nautilus Shell Nether Quartz Nether Star Nether Wart Phantom Membrane Prismarine Shard Prismarine Crystals Rabbit Hide Rabbit's Foot Raw Copper Raw Gold Raw Iron Redstone Dust Shulker Shell Slimeball Stick String Turtle Scute WheatUpcoming   Armadillo Scute Breeze Rod |
| Upcoming           | Armadillo Scute Breeze Rod                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Processed          | Blaze Powder Book Brick Nether Charcoal Copper Ingot Fermented Spider Eye Firework Star Glistering Melon Slice Gold Ingot Nugget Iron Ingot Nugget Netherite Ingot Netherite Scrap Paper Popped Chorus Fruit SugarBE & EE only   Bleach    Compounds                                                                                                                                                                                                                                                                        |
| BE&EEonly          | Bleach    Compounds                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Dyes               | Black Dye Blue Dye Brown Dye Cyan Dye Gray Dye Green Dye Light Blue Dye Light Gray Dye Lime Dye Magenta Dye Orange Dye Pink Dye Purple Dye Red Dye White Dye Yellow Dye                                                                                                                                                                                                                                                                                                                                                     |
| Banner Patterns    | Flower Charge Creeper Charge Skull Charge Thing Globe SnoutBE & EE only   Field Masoned Bordure Indented   Upcoming   Flow Guster                                                                                                                                                                                                                                                                                                                                                                                           |
| BE&EEonly          | Field Masoned Bordure Indented                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Upcoming           | Flow Guster                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Pottery Sherds     | Angler Archer Arms Up Blade Brewer Burn Danger Explorer Friend Heart Heartbreak Howl Miner Mourner Plenty Prize Sheaf Shelter Skull SnortUpcoming   Flow Guster Scrape                                                                                                                                                                                                                                                                                                                                                      |
| Upcoming           | Flow Guster Scrape                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Smithing Templates | Armor Trim Coast Dune Eye Host Raiser Rib Sentry Shaper Silence Snout Spire Tide Vex Ward Wayfinder Wild Netherite UpgradeUpcoming   Flow Bolt                                                                                                                                                                                                                                                                                                                                                                              |
| Upcoming           | Flow Bolt                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

| Upcoming | Armadillo Scute Breeze Rod |
|----------|----------------------------|

| BE & EE only | Bleach    Compounds |
|--------------|---------------------|

| BE & EE only | Field Masoned Bordure Indented |
|--------------|--------------------------------|
| Upcoming     | Flow Guster                    |

| Upcoming | Flow Guster Scrape |
|----------|--------------------|

| Upcoming | Flow Bolt |
|----------|-----------|

| Creative or commands only |                                                                                                                                            |
|---------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| Creativeonly              | Spawn EggsJava Edition only   Debug Stick Minecart with Command Block Unused Paintings   Minecraft Education only   Camera Photo Portfolio |
| Java Editiononly          | Debug Stick Minecart with Command Block Unused Paintings                                                                                   |
| Minecraft Educationonly   | Camera Photo Portfolio                                                                                                                     |
| Commandsonly              | Boss Spawn Eggs Ender Dragon WitherJava Edition only   Bundle Knowledge Book                                                               |
| Java Editiononly          | Bundle Knowledge Book                                                                                                                      |

| Java Edition only       | Debug Stick Minecart with Command Block Unused Paintings |
|-------------------------|----------------------------------------------------------|
| Minecraft Educationonly | Camera Photo Portfolio                                   |

| Java Edition only | Bundle Knowledge Book |
|-------------------|-----------------------|

| Unused              |                                        |
|---------------------|----------------------------------------|
| All editions        | Mundane Potion Thick Potion            |
| Java Editiononly    | Potion of Luck Uncraftable Potion      |
| Bedrock Editiononly | Camera Potion of Decay  Unused Potions |

| Unimplemented       |                                                          |
|---------------------|----------------------------------------------------------|
| All editions        | Quiver Ruby                                              |
| Java Editiononly    | Crystallized Honey Minecart with Dispenser Studded Armor |
| Bedrock Editiononly | Minecart with Furnace Hoglin Meat                        |

| Joke features    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| April Fools 2015 | Obsidian Boat                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| April Fools 2016 | Smarter Watch Reality Vision Ankle Monitor                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| April Fools 2019 | 3D Blue Key Red Key Yellow Key                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| April Fools 2020 | Footprint A Very Fine Item                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| April Fools 2023 | Air Banner Pattern (New Thing) Bit Bottle of Entity Splash Bottle of Void La Baguette Le Tricolore minecraft:dupe_hack Moon Cow Spawn Egg Longer String Potion of Big Splash Lingering Arrow Potion of Small Splash Lingering Arrow Tag                                                                                                                                                                                                                                                                                                                                              |
| April Fools 2024 | Amber Gem Batato Spawn Egg Golden Poisonous Potato Enchanted Dent Hash Browns Hot potato Mega Spud Spawn Egg Plaguewhale Slab Spawn Egg Poisonous Polytra Poisonous Pota-Toes Poisonous Potato Chestplate Poisonous Potato Chips Poisonous Potato Fries Poisonous Potato Plant Poisonous Potato Slices Poisonous Potato Sticks Poisonous Potato Zombie Spawn Egg Poisonous Potato Hammer Potato Eye Potato of Knowledge Potato Oil Poisonous Potato Peeler Potato Peels Corrupted Potatiesh, Greatstaff of the Peasant Toxic Beam Toxic Resin Toxifin Slab Spawn Egg Venomous Potato |

| Removed             |                                                |
|---------------------|------------------------------------------------|
| Java Editiononly    | Cauldron Potions Horse Saddle Reverted Potions |
| Bedrock Editiononly | Copper Horn                                    |
| Legacy Consoleonly  | debug fourj item                               |
| MinecraftEduonly    | Block Inspector                                |

