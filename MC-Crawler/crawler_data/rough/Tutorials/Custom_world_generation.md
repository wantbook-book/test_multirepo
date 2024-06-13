# Tutorials/Custom world generation
Custom world generation is very complex and difficult for most data pack or mod creators. To create a more complete world, it is necessary to refer to how the world is generated in the vanilla version.

This tutorial roughly explains some of the vanilla world generation files in 1.20.1, making it easy for creators to read and understand the vanilla world generation.

## Contents
- 1 How to obtain vanilla world generation files
- 2 Final density function of the overworld
- 3 Surface rules of the overworld
	- 3.1 Notes
		- 3.1.1 Basin
		- 3.1.2 Carver
- 4 Biome source parameter list presets
- 5 See also

## How to obtain vanilla world generation files
After 22w42a, most of world generation files can be found in the data/minecraft/worldgen directory in client.jar or server.jar. However, multi-noise biome source parameter list files do not contain details of biome parameter list presets of the vanilla overworld and nether.

Through running the data generator, you can directly generate all vanilla data pack files, as well as biome source parameter list presets of the overworld and the nether.

The vanilla world generation files before 22w42a can be obtained on Slicedlime's github, located at examples repository. Missing versions in the repository commit history mean that the world generation files have not changed in these versions.

## Final density function of the overworld
Final density function of the overworld is the final_density field in worldgen/noise_settings/overworld.json.

{  //Final density function of the overworld
"type": "minecraft:min",
"argument1":
{  //Brings its value closer to 0, which affects the generation of barriers between different liquid bodies in the aquifer. The smaller the negative value of final_density, the less likely it is to generate barriers

"type": "minecraft:squeeze",
"argument": {
"type": "minecraft:mul",
"argument1": 0.64,
"argument2":
{  //Interpolating

"type": "minecraft:interpolated",
"argument":
{  //Transition to legacy 256-block-high chunks generated in old versions

"type": "minecraft:blend_density",
"argument":
{  //From Y=-40 to Y=-64, the density function value gradually changes to a fixed value of 0.1171875 to avoid too deep caves that expose or even penetrate the bedrock layer

"type": "minecraft:add",
"argument1": 0.1171875,
"argument2": {
"type": "minecraft:mul",
"argument1": {
"type": "minecraft:y_clamped_gradient",
"from_y": -64,
"to_y": -40,
"from_value": 0,
"to_value": 1
},
"argument2": {
"type": "minecraft:add",
"argument1": -0.1171875,
"argument2":
{  //From Y=-40 to Y=-64, the density function value gradually changes to a fixed value of -0.078125 to avoid too high terrain

"type": "minecraft:add",
"argument1": -0.078125,
"argument2": {
"type": "minecraft:mul",
"argument1": {
"type": "minecraft:y_clamped_gradient",
"from_y": 240,
"to_y": 256,
"from_value": 1,
"to_value": 0
},
"argument2": {
"type": "minecraft:add",
"argument1": 0.078125,
"argument2":
{  //Using sloped_cheese's 1.5625 as the boundary, divides the world into surface and underground parts

"type": "minecraft:range_choice",
"input": "minecraft:overworld/sloped_cheese",
"min_inclusive": -1000000,
"max_exclusive": 1.5625,
"when_in_range":
{  //Surface part

"type": "minecraft:min",
"argument1": "minecraft:overworld/sloped_cheese",  //Determines the height and shape of the surface terrain
"argument2":
{  //Noise cave entrances, i.e., some caves that connect the surface and underground caves

"type": "minecraft:mul",
"argument1": 5,
"argument2": "minecraft:overworld/caves/entrances"
}

},
"when_out_of_range":
{  //Underground part

"type": "minecraft:max",
"argument1":
{  //Spaghetti, cheese caves, and cave entrances. Takes the minimum value of the three. It is necessary to call the cave entrance again here, otherwise the cave entrance would only be generated in the surface part and cut off at the underground part

"type": "minecraft:min",
"argument1":
{  //Cheese caves and cave entrances

"type": "minecraft:min",
"argument1":
{  //Cheese caves

"type": "minecraft:add",
"argument1":
{  //Make caves smaller and more irregular in shape. The value of this field is always positive

"type": "minecraft:mul",
"argument1": 4,
"argument2": {
"type": "minecraft:square",
"argument": {
"type": "minecraft:noise",
"noise": "minecraft:cave_layer",
"xz_scale": 1,
"y_scale": 8
}
}

},
"argument2":
{

"type": "minecraft:add",
"argument1":
{  //Cheese caves. Cheese caves generate only at places where this field is less than zero

"type": "minecraft:clamp",
"input": {
"type": "minecraft:add",
"argument1": 0.27,
"argument2": {
"type": "minecraft:noise",
"noise": "minecraft:cave_cheese",
"xz_scale": 1,
"y_scale": 0.6666666666666666
}
},
"min": -1,
"max": 1

},
"argument2":
{  //Increases density near the surface to reduce the generation of cheese caves near the surface. This field is 0 when the value of slope_cheese is greater than 2.34375, gradually increasing to 0.5 until the slope_cheese reaches 1.5625

"type": "minecraft:clamp",
"input": {
"type": "minecraft:add",
"argument1": 1.5,
"argument2": {
"type": "minecraft:mul",
"argument1": -0.64,
"argument2": "minecraft:overworld/sloped_cheese"
}
},
"min": 0,
"max": 0.5

}

}

},
"argument2": "minecraft:overworld/caves/entrances"  //Cave entrances

},
"argument2":
{  //Spaghetti caves

"type": "minecraft:add",
"argument1": "minecraft:overworld/caves/spaghetti_2d",
"argument2": "minecraft:overworld/caves/spaghetti_roughness_function"
}

},
"argument2":
{  //Noise pillars in noise caves

"type": "minecraft:range_choice",
"input": "minecraft:overworld/caves/pillars",
"min_inclusive": -1000000,
"max_exclusive": 0.03,
"when_in_range": -1000000,
"when_out_of_range": "minecraft:overworld/caves/pillars"
}

}

}
}
}

}
}
}

}

}

}
}
},
"argument2": "minecraft:overworld/caves/noodle"  //Noodle caves
}

In which, the sloped_cheese used to determine the height and shape of the surface terrain is located in data/minecraft/worldgen/density_function/overworld/sloped_cheese.json.

{  //sloped_cheese
"type": "minecraft:add",
"argument1":
{  //Multiplies the factor minecraft:overworld/factor to determine the distribution of 3D terrain. Then multiplies positive values by 4 to avoid deep underground region being affected by base_3d_noise

"type": "minecraft:mul",
"argument1": 4.0,
"argument2": {
"type": "minecraft:quarter_negative",
"argument": {
"type": "minecraft:mul",
"argument1":
{

"type": "minecraft:add",
"argument1": "minecraft:overworld/depth",  //Determines the height of the surface terrain in general, with negative values above the surface and positive values below the surface
"argument2":
{  //Increases or decreases density in high mountainous areas to obtain jagged small peaks. This field is a two-dimensional density function

"type": "minecraft:mul",
"argument1": "minecraft:overworld/jaggedness",  // Using a spline function, obtains the distribution of mountain ranges based on continentalness, erosion, PV value, and weirdness value. It is 0 in most places, but positive in areas with high continentalness, low erosion, and high PV values, and larger in areas with negative weirdness
"argument2": {  //Noise factor to convert mountain ranges into small peaks
"type": "minecraft:half_negative",
"argument": {
"type": "minecraft:noise",
"noise": "minecraft:jagged",
"xz_scale": 1500.0,
"y_scale": 0.0
}
}

}

},
"argument2": "minecraft:overworld/factor"  //This factor uses spline function to determine the distribution of 3D terrain according to continentalness, erosion, weirdness and PV value. It is always positive. Values are smaller at the positions where windswept savannas or shattered biomes should be generated, and higher at other places to reduce the impact of base_3d_noise
}
}

},
"argument2": "minecraft:overworld/base_3d_noise"  //A 3D noise used to create 3D surface terrain shape
}
In which, the depth to determine the height of general surface terrain is located in data/minecraft/worldgen/density_function/overworld/depth.json.

{  //depth
"type": "minecraft:add",
"argument1":
{  //For each block down, the depth decreases by 1⁄128 (0.0078125), and it is 0 at Y=128

"type": "minecraft:y_clamped_gradient",
"from_value": 1.5,
"from_y": -64,
"to_value": -1.5,
"to_y": 320

},
"argument2": "minecraft:overworld/offset"  //The terrain height offset using a spline function based on continentalness, erosion, and PV values
}
## Surface rules of the overworld
Surface rules of the overworld are the surface_rule field in worldgen/noise_settings/overworld.json.

{  //Surface rules of the overworld
"type": "minecraft:sequence",
"sequence": [
//Bedrock layers
{

"type": "minecraft:condition",
"if_true":   //Blocks at Y=-64 are always bedrocks, and between Y=-64 to Y=-60 is noise gradient of bedrocks.
{

"type": "minecraft:vertical_gradient",
"random_name": "minecraft:bedrock_floor",
"true_at_and_below": {
"above_bottom": 0
},
"false_at_and_above": {
"above_bottom": 5
}

},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:bedrock"
}
}

},
//Surface layers (such as grass blocks and dirt in plains)
{

"type": "minecraft:condition",
"if_true": {  //Whether to generate surface layers (such as grass blocks and dirt in plains). The preliminary_surface is generally offset by about 2 to 8 blocks down from the initial terrain height that generated by initial_density_without_jaggedness in noise settings. It is usually very low relative to the actual surface layer thickness to ensure the generation of the surface layers. If there were no this conditions, the surface layers would also be generated at the ground of deep caves.
"type": "minecraft:above_preliminary_surface"
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//The topmost layer of some distinctive biomes
{

"type": "minecraft:condition",
"if_true":   //The topmost layer (with air above, or separated from air block above by some liquid blocks) (including the ground of noise caves near the surface (above the preliminary_surface))
{

"type": "minecraft:stone_depth",
"offset": 0,
"surface_type": "floor",
"add_surface_depth": false,
"secondary_depth_range": 0

},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//At the topmost layer of high places in a wooded badlands, coarse dirt and grass blocks are distributed alternately, and when grass blocks are underwater, they become dirt.
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:wooded_badlands"
]
},
"then_run": {
"type": "minecraft:condition",
"if_true": {
"type": "minecraft:y_above",
"anchor": {
"absolute": 97
},
"surface_depth_multiplier": 2,
"add_stone_depth": false
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//Coarse dirt
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:surface",
"min_threshold": -0.909,
"max_threshold": -0.5454
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:coarse_dirt"
}
}

},
//Coarse dirt
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:surface",
"min_threshold": -0.1818,
"max_threshold": 0.1818
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:coarse_dirt"
}
}

},
//Coarse dirt
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:surface",
"min_threshold": 0.5454,
"max_threshold": 0.909
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:coarse_dirt"
}
}

},
//Default to grass block (or dirt when underwater)
{

"type": "minecraft:sequence",
"sequence": [
//Grass block when there is no water above
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:water",
"offset": 0,
"surface_depth_multiplier": 0,
"add_stone_depth": false
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:grass_block",
"Properties": {
"snowy": "false"
}
}
}

},
//Dirt otherwise
{

"type": "minecraft:block",
"result_state": {
"Name": "minecraft:dirt"
}

}
]

}
]
}
}

},
//When the topmost layer of swamps is at Y=62, it is randomly replaced with water based on noise to form marsh-like terrain. Y=62 is usually on the shore of a river, lake, or ocean.
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:swamp"
]
},
"then_run": {
"type": "minecraft:condition",
"if_true":   //If Y>=62
{
"type": "minecraft:y_above",
"anchor": {
"absolute": 62
},
"surface_depth_multiplier": 0,
"add_stone_depth": false
},
"then_run": {
"type": "minecraft:condition",
"if_true":   //If Y<63
{
"type": "minecraft:not",
"invert": {
"type": "minecraft:y_above",
"anchor": {
"absolute": 63
},
"surface_depth_multiplier": 0,
"add_stone_depth": false
}
},
"then_run": {
"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:surface_swamp",
"min_threshold": 0,
"max_threshold": 1.7976931348623157e+308
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:water",
"Properties": {
"level": "0"
}
}
}
}
}
}

},
//When the topmost layer of mangrove swamps is at Y=60—62, it is randomly replaced with water based on noise to form marsh-like terrain. Y=60—62 is usually on the shore or beneath shallow water.
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:mangrove_swamp"
]
},
"then_run": {
"type": "minecraft:condition",
"if_true":   //If Y>=60
{
"type": "minecraft:y_above",
"anchor": {
"absolute": 60
},
"surface_depth_multiplier": 0,
"add_stone_depth": false
},
"then_run": {
"type": "minecraft:condition",
"if_true":   //If Y<63
{
"type": "minecraft:not",
"invert": {
"type": "minecraft:y_above",
"anchor": {
"absolute": 63
},
"surface_depth_multiplier": 0,
"add_stone_depth": false
}
},
"then_run": {
"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:surface_swamp",
"min_threshold": 0,
"max_threshold": 1.7976931348623157e+308
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:water",
"Properties": {
"level": "0"
}
}
}
}
}
}

}
]
}

},
//The topmost layer of badlands, eroded badlands and wooded badlands
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:badlands",
"minecraft:eroded_badlands",
"minecraft:wooded_badlands"
]
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//The topmost layer
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:stone_depth",
"offset": 0,
"surface_type": "floor",
"add_surface_depth": false,
"secondary_depth_range": 0
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//The topmost layer at an extremely high altitude is orange terracotta. It does not take effect because there is no block at all at Y=256 and above in the vanilla overworld
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:y_above",
"anchor": {
"absolute": 256
},
"surface_depth_multiplier": 0,
"add_stone_depth": false
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:orange_terracotta"
}
}

},
//At Y=(74 + surface_depth) or above, the topmost layer is terracotta and various stained terracotta
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:y_above",
"anchor": {
"absolute": 74
},
"surface_depth_multiplier": 1,
"add_stone_depth": true
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//Terracotta
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:surface",
"min_threshold": -0.909,
"max_threshold": -0.5454
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:terracotta"
}
}

},
//Terracotta
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:surface",
"min_threshold": -0.1818,
"max_threshold": 0.1818
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:terracotta"
}
}

},
//Terracotta
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:surface",
"min_threshold": 0.5454,
"max_threshold": 0.909
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:terracotta"
}
}

},
//Bands of terracotta and various stained terracotta
{

"type": "minecraft:bandlands"

}
]
}

},
//Red sand when there is no water above (or red sandstone if floating)
{

"type": "minecraft:condition",
"if_true":   //If there is no liquid above
{

"type": "minecraft:water",
"offset": -1,
"surface_depth_multiplier": 0,
"add_stone_depth": false

},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//Red sandstone if there is no block support below
{
"type": "minecraft:condition",
"if_true": {
"type": "minecraft:stone_depth",
"offset": 0,
"surface_type": "ceiling",
"add_surface_depth": false,
"secondary_depth_range": 0
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:red_sandstone"
}
}
},
//Red sand otherwise
{
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:red_sand"
}
}
]
}

},
//When there is water above, if the surface depth is positive, orange terracotta is generated
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:not",
"invert": {
"type": "minecraft:hole"
}
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:orange_terracotta"
}
}

},
//Default to white terracotta when under shallow water
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:water",
"offset": -6,
"surface_depth_multiplier": -1,
"add_stone_depth": true
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:white_terracotta"
}
}

},
//Default to gravel when under deep water (or stone if floating)
{

"type": "minecraft:sequence",
"sequence": [
//Stone if there is no block support below
{
"type": "minecraft:condition",
"if_true": {
"type": "minecraft:stone_depth",
"offset": 0,
"surface_type": "ceiling",
"add_surface_depth": false,
"secondary_depth_range": 0
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:stone"
}
}
},
//Gravel
{
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:gravel"
}
}
]

}
]
}

},
//Surface layers when terrain height >= (63-surface_depth)
{

"type": "minecraft:condition",
"if_true":   //terrain height >= (63-surface_depth)
{
"type": "minecraft:y_above",
"anchor": {
"absolute": 63
},
"surface_depth_multiplier": -1,
"add_stone_depth": true
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//Orange terracotta when Y>=63 and terrain height < (74+surface_depth)
{

"type": "minecraft:condition",
"if_true":   //Y>=63
{
"type": "minecraft:y_above",
"anchor": {
"absolute": 63
},
"surface_depth_multiplier": 0,
"add_stone_depth": false
},
"then_run": {
"type": "minecraft:condition",
"if_true":   //terrain height < (74+surface_depth)
{
"type": "minecraft:not",
"invert": {
"type": "minecraft:y_above",
"anchor": {
"absolute": 74
},
"surface_depth_multiplier": 1,
"add_stone_depth": true
}
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:orange_terracotta"
}
}
}

},
//Bands otherwise
{

"type": "minecraft:bandlands"

}
]
}

},
//Surface layers when there's no water above or there's shallow water above
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:stone_depth",
"offset": 0,
"surface_type": "floor",
"add_surface_depth": true,
"secondary_depth_range": 0
},
"then_run": {
"type": "minecraft:condition",
"if_true":   //when there's no liquid above or there's shallow liquid above
{
"type": "minecraft:water",
"offset": -6,
"surface_depth_multiplier": -1,
"add_stone_depth": true
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:white_terracotta"
}
}
}

}
]
}

},
//The topmost layer when there's no water above
{

"type": "minecraft:condition",
"if_true":   //The topmost layer
{
"type": "minecraft:stone_depth",
"offset": 0,
"surface_type": "floor",
"add_surface_depth": false,
"secondary_depth_range": 0
},
"then_run": {
"type": "minecraft:condition",
"if_true":   //When there's no liquid above. Note that during carver generation, this condition is always successful regardless of whether there is liquid above or not, as detailed in #Notes
{
"type": "minecraft:water",
"offset": -1,
"surface_depth_multiplier": 0,
"add_stone_depth": false
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//Basin. See #Notes for details
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:frozen_ocean",
"minecraft:deep_frozen_ocean"
]
},
"then_run": {
"type": "minecraft:condition",
"if_true": {
"type": "minecraft:hole"
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [

{
"type": "minecraft:condition",
"if_true":
{
"type": "minecraft:water",
"offset": 0,
"surface_depth_multiplier": 0,
"add_stone_depth": false
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:air"
}
}
},

{
"type": "minecraft:condition",
"if_true": {
"type": "minecraft:temperature"
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:ice"
}
}
},

{
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:water",
"Properties": {
"level": "0"
}
}
}
]
}

}

},
//The topmost layer
{

"type": "minecraft:sequence",
"sequence": [
//The topmost layer of frozen peaks is ice, snow block, and packed ice.
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:frozen_peaks"
]
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//Packed ice at steep slopes behind the sun
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:steep"
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:packed_ice"
}
}

},
//Packed ice in strips
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:packed_ice",
"min_threshold": 0,
"max_threshold": 0.2
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:packed_ice"
}
}

},
//Ice generated occasionally
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:ice",
"min_threshold": 0,
"max_threshold": 0.025
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:ice"
}
}

},
//Defaults to snow block
{

"type": "minecraft:condition",
"if_true":  &emsp//Condition for carvers. See #Notes
{
"type": "minecraft:water",
"offset": 0,
"surface_depth_multiplier": 0,
"add_stone_depth": false
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:snow_block"
}
}

}
]
}

},
//The topmost layer of snowy slopes is powder snow, snow block and stone
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:snowy_slopes"
]
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//Stone at steep slopes behind the sun
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:steep"
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:stone"
}
}

},
//Powder snow in strips
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:powder_snow",
"min_threshold": 0.35,
"max_threshold": 0.6
},
"then_run": {
"type": "minecraft:condition",
"if_true": 	//Condition for carvers. See #Notes.
{
"type": "minecraft:water",
"offset": 0,
"surface_depth_multiplier": 0,
"add_stone_depth": false
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:powder_snow"
}
}
}

},
//Defaults to snow block
{

"type": "minecraft:condition",
"if_true": 	//Condition for carvers. See #Notes.
{
"type": "minecraft:water",
"offset": 0,
"surface_depth_multiplier": 0,
"add_stone_depth": false
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:snow_block"
}
}

}
]
}

},
//The topmost layer of jagged peaks is snow block and stone
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:jagged_peaks"
]
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//Stone at steep slopes behind the sun
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:steep"
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:stone"
}
}

},
//Defaults to snow block
{

"type": "minecraft:condition",
"if_true": 	//Condition for carvers. See #Notes.
{
"type": "minecraft:water",
"offset": 0,
"surface_depth_multiplier": 0,
"add_stone_depth": false
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:snow_block"
}
}

}
]
}

},
//The topmost layer of groves is powder snow and snow block
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:grove"
]
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//Powder snow in strips
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:powder_snow",
"min_threshold": 0.35,
"max_threshold": 0.6
},
"then_run": {
"type": "minecraft:condition",
"if_true": 	//Condition for carvers. See #Notes.
{
"type": "minecraft:water",
"offset": 0,
"surface_depth_multiplier": 0,
"add_stone_depth": false
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:powder_snow"
}
}
}

},
//Defaults to snow block
{

"type": "minecraft:condition",
"if_true": 	//Condition for carvers. See #Notes.
{
"type": "minecraft:water",
"offset": 0,
"surface_depth_multiplier": 0,
"add_stone_depth": false
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:snow_block"
}
}

}
]
}

},
//The topmost layer of some biomes is sand or stone
{

"type": "minecraft:sequence",
"sequence": [
//The topmost layer of stony peaks is calcite and stone
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:stony_peaks"
]
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//Calcite in strips
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:calcite",
"min_threshold": -0.0125,
"max_threshold": 0.0125
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:calcite"
}
}

},
//Defaults to stone
{

"type": "minecraft:block",
"result_state": {
"Name": "minecraft:stone"
}

}
]
}

},
//The topmost layer of stony shore is gravel and stone
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:stony_shore"
]
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//Gravel in strips (or stone if floating)
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:gravel",
"min_threshold": -0.05,
"max_threshold": 0.05
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
{
"type": "minecraft:condition",
"if_true":   //Stone if there is no block support below
{
"type": "minecraft:stone_depth",
"offset": 0,
"surface_type": "ceiling",
"add_surface_depth": false,
"secondary_depth_range": 0
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:stone"
}
}
},
{
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:gravel"
}
}
]
}

},
//Defaults to stone
{

"type": "minecraft:block",
"result_state": {
"Name": "minecraft:stone"
}

}
]
}

},
//When the surface depth is deep, the topmost layer of windswept hills is stone
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:windswept_hills"
]
},
"then_run":   //Stone when the surface depth is deep
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:surface",
"min_threshold": 0.12121212121212122,
"max_threshold": 1.7976931348623157e+308
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:stone"
}
}

}

},
//The topmost layer of warm ocean, beach, and snowy beach is sand and sandstone
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:warm_ocean",
"minecraft:beach",
"minecraft:snowy_beach"
]
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//Sandstone if floating
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:stone_depth",
"offset": 0,
"surface_type": "ceiling",
"add_surface_depth": false,
"secondary_depth_range": 0
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:sandstone"
}
}

},
//Defaults to sand
{

"type": "minecraft:block",
"result_state": {
"Name": "minecraft:sand"
}

}
]
}

},
//The topmost layer of desert is sand and sandstone
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:desert"
]
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//Sandstone if floating
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:stone_depth",
"offset": 0,
"surface_type": "ceiling",
"add_surface_depth": false,
"secondary_depth_range": 0
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:sandstone"
}
}

},
//Defaults to sand
{

"type": "minecraft:block",
"result_state": {
"Name": "minecraft:sand"
}

}
]
}

},
//The topmost layer of dripstone caves is stone, although this biome is rarely generated on the surface
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:dripstone_caves"
]
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:stone"
}
}

}
]

},
//At most places, the topmost layer of windswept savanna is stone and coarse dirt
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:windswept_savanna"
]
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//Stone when the surface depth is very deep
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:surface",
"min_threshold": 0.21212121212121213,
"max_threshold": 1.7976931348623157e+308
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:stone"
}
}

},
//Coarse dirt when the surface depth is a little deep
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:surface",
"min_threshold": -0.06060606060606061,
"max_threshold": 1.7976931348623157e+308
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:coarse_dirt"
}
}

}
]
}

},
//The topmost layer of windswept gravelly hills is gravel, stone and grass block
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:windswept_gravelly_hills"
]
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//Gravel when the surface depth is very deep (or stone if floating)
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:surface",
"min_threshold": 0.24242424242424243,
"max_threshold": 1.7976931348623157e+308
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
{
"type": "minecraft:condition",
"if_true": {
"type": "minecraft:stone_depth",
"offset": 0,
"surface_type": "ceiling",
"add_surface_depth": false,
"secondary_depth_range": 0
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:stone"
}
}
},
{
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:gravel"
}
}
]
}

},
//Stone when the surface depth is a little deep
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:surface",
"min_threshold": 0.12121212121212122,
"max_threshold": 1.7976931348623157e+308
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:stone"
}
}

},
//Grass block when the surface depth is a little shallow
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:surface",
"min_threshold": -0.12121212121212122,
"max_threshold": 1.7976931348623157e+308
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//Condition for carvers. See #Notes.
{
"type": "minecraft:condition",
"if_true": {
"type": "minecraft:water",
"offset": 0,
"surface_depth_multiplier": 0,
"add_stone_depth": false
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:grass_block",
"Properties": {
"snowy": "false"
}
}
}
},
{
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:dirt"
}
}
]
}

},
//Defaults to gravel (or stone if floating)
{

"type": "minecraft:sequence",
"sequence": [
{
"type": "minecraft:condition",
"if_true": {
"type": "minecraft:stone_depth",
"offset": 0,
"surface_type": "ceiling",
"add_surface_depth": false,
"secondary_depth_range": 0
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:stone"
}
}
},
{
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:gravel"
}
}
]

}
]
}

},
//At most places, the topmost layer of old growth pine taiga and old growth spruce taiga is coarse dirt and podzol
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:old_growth_pine_taiga",
"minecraft:old_growth_spruce_taiga"
]
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//Coarse dirt when the surface depth is very deep
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:surface",
"min_threshold": 0.21212121212121213,
"max_threshold": 1.7976931348623157e+308
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:coarse_dirt"
}
}

},
//Podzol when the surface depth is a little deep
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:surface",
"min_threshold": -0.11515151515151514,
"max_threshold": 1.7976931348623157e+308
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:podzol",
"Properties": {
"snowy": "false"
}
}
}

}
]
}

},
//The topmost layer of ice spikes is snow block
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:ice_spikes"
]
},
"then_run": {
"type": "minecraft:condition",
"if_true": 	//Condition for carvers. See #Notes.
{
"type": "minecraft:water",
"offset": 0,
"surface_depth_multiplier": 0,
"add_stone_depth": false
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:snow_block"
}
}
}

},
//The topmost layer of mangrove swamp is mud
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:mangrove_swamp"
]
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:mud"
}
}

},
//The topmost layer of mushroom fields is mycelium
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:mushroom_fields"
]
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:mycelium",
"Properties": {
"snowy": "false"
}

}
}

},
//The topmost layer defaults to grass block
{

"type": "minecraft:sequence",
"sequence": [
{
"type": "minecraft:condition",
"if_true":	//Condition for carvers. See #Notes.
{
"type": "minecraft:water",
"offset": 0,
"surface_depth_multiplier": 0,
"add_stone_depth": false
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:grass_block",
"Properties": {
"snowy": "false"
}
}
}
},
{
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:dirt"
}
}
]

}
]

}
]
}
}

},
//Surface layers under shallow water (including the topmost layer), and surface layers without water above (excluding the topmost layer, since the topmost layer without water above has been processed above). And additional secondary surface layers under surface layers in some biomes.
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:water",
"offset": -6,
"surface_depth_multiplier": -1,
"add_stone_depth": true
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//Basin. See #Notes for details.
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:stone_depth",
"offset": 0,
"surface_type": "floor",
"add_surface_depth": false,
"secondary_depth_range": 0
},
"then_run": {
"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:frozen_ocean",
"minecraft:deep_frozen_ocean"
]
},
"then_run": {
"type": "minecraft:condition",
"if_true": {
"type": "minecraft:hole"
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:water",
"Properties": {
"level": "0"
}
}
}
}
}

},
//Surface layers
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:stone_depth",
"offset": 0,
"surface_type": "floor",
"add_surface_depth": true,
"secondary_depth_range": 0
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//Surface layers of frozen peaks are ice, snow block and packed ice
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:frozen_peaks"
]
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//Packed ice at steep slopes behind the sun
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:steep"
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:packed_ice"
}
}

},
//Packed ice in strips
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:packed_ice",
"min_threshold": -0.5,
"max_threshold": 0.2
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:packed_ice"
}
}

},
//Ice generated occasionally
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:ice",
"min_threshold": -0.0625,
"max_threshold": 0.025
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:ice"
}
}

},
//Snow block only if there's no water above
{

"type": "minecraft:condition",
"if_true": 	//With air above, or separated from air block above by some non-liquid blocks
{
"type": "minecraft:water",
"offset": 0,
"surface_depth_multiplier": 0,
"add_stone_depth": false
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:snow_block"
}
}

}
]
}

},
//Surface layers of snowy slopes are powder snow, snow block, and stone
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:snowy_slopes"
]
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//Stone at steep slopes behind the sun
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:steep"
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:stone"
}
}

},
//Powder snow in strips only if there's no water above
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:powder_snow",
"min_threshold": 0.45,
"max_threshold": 0.58
},
"then_run": {
"type": "minecraft:condition",
"if_true": {
"type": "minecraft:water",
"offset": 0,
"surface_depth_multiplier": 0,
"add_stone_depth": false
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:powder_snow"
}
}
}

},
//Snow block only if there's no water above
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:water",
"offset": 0,
"surface_depth_multiplier": 0,
"add_stone_depth": false
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:snow_block"
}
}

}
]
}

},
//Surface layers of jagged peaks are stone
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:jagged_peaks"
]
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:stone"
}
}

},
//Surface layers of groves is powder snow and dirt
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:grove"
]
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//Powder snow in strips only if there's no water above
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:powder_snow",
"min_threshold": 0.45,
"max_threshold": 0.58
},
"then_run": {
"type": "minecraft:condition",
"if_true": {
"type": "minecraft:water",
"offset": 0,
"surface_depth_multiplier": 0,
"add_stone_depth": false
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:powder_snow"
}
}
}

},
//Defaults to dirt
{

"type": "minecraft:block",
"result_state": {
"Name": "minecraft:dirt"
}

}
]
}

},
//Surface layers of some biomes are sand and stone
{

"type": "minecraft:sequence",
"sequence": [
//Surface layers of stony peaks are calcite and stone
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:stony_peaks"
]
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//Calcite in strips
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:calcite",
"min_threshold": -0.0125,
"max_threshold": 0.0125
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:calcite"
}
}

},
//Defaults to stone
{

"type": "minecraft:block",
"result_state": {
"Name": "minecraft:stone"
}

}
]
}

},
//Surface layers of stony shore are gravel and stone
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:stony_shore"
]
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//Gravel in strips (or stone if floating)
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:gravel",
"min_threshold": -0.05,
"max_threshold": 0.05
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
{
"type": "minecraft:condition",
"if_true": {
"type": "minecraft:stone_depth",
"offset": 0,
"surface_type": "ceiling",
"add_surface_depth": false,
"secondary_depth_range": 0
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:stone"
}
}
},
{
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:gravel"
}
}
]
}


},
//Defaults to stone
{

"type": "minecraft:block",
"result_state": {
"Name": "minecraft:stone"
}

}
]
}

},
//Surface layers of windswept hills are stone when when the surface depth is deep
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:windswept_hills"
]
},
"then_run": {
"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:surface",
"min_threshold": 0.12121212121212122,
"max_threshold": 1.7976931348623157e+308
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:stone"
}
}
}

},
//Surface layers of warm ocean, beach, snowy beach are sand and sandstone
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:warm_ocean",
"minecraft:beach",
"minecraft:snowy_beach"
]
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//Sandstone if floating
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:stone_depth",
"offset": 0,
"surface_type": "ceiling",
"add_surface_depth": false,
"secondary_depth_range": 0
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:sandstone"
}
}

},
//Defaults to sand
{

"type": "minecraft:block",
"result_state": {
"Name": "minecraft:sand"
}

}
]
}

},
//Surface layers of desert are sand sandstone
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:desert"
]
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//Sandstone if floating
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:stone_depth",
"offset": 0,
"surface_type": "ceiling",
"add_surface_depth": false,
"secondary_depth_range": 0
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:sandstone"
}
}

},
//Defaults to sand
{

"type": "minecraft:block",
"result_state": {
"Name": "minecraft:sand"
}

}
]
}

},
//Surface layers of dripstone caves are stone, although this biome is rarely generated on the surface
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:dripstone_caves"
]
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:stone"
}
}

}
]

},
//Surface layers of windswept savanna is stone when the surface depth is deep
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:windswept_savanna"
]
},
"then_run": {
"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:surface",
"min_threshold": 0.21212121212121213,
"max_threshold": 1.7976931348623157e+308
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:stone"
}
}
}

},
//Surface layers of windswept gravelly hills are gravel, stone, and dirt
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:windswept_gravelly_hills"
]
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//Gravel when the surface depth is very deep (or stone if floating)
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:surface",
"min_threshold": 0.24242424242424243,
"max_threshold": 1.7976931348623157e+308
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
{
"type": "minecraft:condition",
"if_true": {
"type": "minecraft:stone_depth",
"offset": 0,
"surface_type": "ceiling",
"add_surface_depth": false,
"secondary_depth_range": 0
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:stone"
}
}
},
{
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:gravel"
}
}
]
}

},
//Stone when the surface depth is a little deep
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:surface",
"min_threshold": 0.12121212121212122,
"max_threshold": 1.7976931348623157e+308
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:stone"
}
}

},
//Dirt when the surface depth is a little shallow
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:noise_threshold",
"noise": "minecraft:surface",
"min_threshold": -0.12121212121212122,
"max_threshold": 1.7976931348623157e+308
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:dirt"
}
}

},
//Defaults to gravel (or stone if floating)
{

"type": "minecraft:sequence",
"sequence": [
{
"type": "minecraft:condition",
"if_true": {
"type": "minecraft:stone_depth",
"offset": 0,
"surface_type": "ceiling",
"add_surface_depth": false,
"secondary_depth_range": 0
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:stone"
}
}
},
{
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:gravel"
}
}
]

}
]
}

},
//Surface layers of mangrove swamp are mud
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:mangrove_swamp"
]
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:mud"
}
}

},
//Surface layers defaults to dirt
{

"type": "minecraft:block",
"result_state": {
"Name": "minecraft:dirt"
}

}
]
}

},
//Secondary surface layers under surface layers of warm ocean, beach, and snowy beach are sandstone
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:warm_ocean",
"minecraft:beach",
"minecraft:snowy_beach"
]
},
"then_run": {
"type": "minecraft:condition",
"if_true": {
"type": "minecraft:stone_depth",
"offset": 0,
"surface_type": "floor",
"add_surface_depth": true,
"secondary_depth_range": 6
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:sandstone"
}
}
}

},
//Secondary surface layers under surface layers of desert are sandstone
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:desert"
]
},
"then_run": {
"type": "minecraft:condition",
"if_true": {  //Secondary surface layers often exceed the the preliminary_surface due to they are extremely thick. Restricted by the condition "minecraft:above_preliminary_surface", sandstones generate only above the preliminary_surface
"type": "minecraft:stone_depth",
"offset": 0,
"surface_type": "floor",
"add_surface_depth": true,
"secondary_depth_range": 30
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:sandstone"
}
}
}

}
]
}

},
//The topmost layer under deep water
{

"type": "minecraft:condition",
"if_true": 	//The topmost layer
{
"type": "minecraft:stone_depth",
"offset": 0,
"surface_type": "floor",
"add_surface_depth": false,
"secondary_depth_range": 0
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
//The topmost layer under deep water of frozen peaks and jagged peaks is stone
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:frozen_peaks",
"minecraft:jagged_peaks"
]
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:stone"
}
}

},
//The topmost layer under deep water of warm ocean, lukewarm ocean and deep lukewarm ocean is sand (or sandstone if floating)
{

"type": "minecraft:condition",
"if_true": {
"type": "minecraft:biome",
"biome_is": [
"minecraft:warm_ocean",
"minecraft:lukewarm_ocean",
"minecraft:deep_lukewarm_ocean"
]
},
"then_run": {
"type": "minecraft:sequence",
"sequence": [
{
"type": "minecraft:condition",
"if_true": {
"type": "minecraft:stone_depth",
"offset": 0,
"surface_type": "ceiling",
"add_surface_depth": false,
"secondary_depth_range": 0
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:sandstone"
}
}
},
{
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:sand"
}
}
]
}

},
//The topmost layer under deep water defaults to gravel (or stone if floating)
{

"type": "minecraft:sequence",
"sequence": [
{
"type": "minecraft:condition",
"if_true": {
"type": "minecraft:stone_depth",
"offset": 0,
"surface_type": "ceiling",
"add_surface_depth": false,
"secondary_depth_range": 0
},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:stone"
}
}
},
{
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:gravel"
}
}
]

}
]
}

}
]
}

},
//Deepslate layers
{

"type": "minecraft:condition",
"if_true":   //Blocks at Y=0 and below are deepslates; at Y=8 and above are stone. Between Y=0 to Y=8 is noise gradient of them.
{

"type": "minecraft:vertical_gradient",
"random_name": "minecraft:deepslate",
"true_at_and_below": {
"absolute": 0
},
"false_at_and_above": {
"absolute": 8
}

},
"then_run": {
"type": "minecraft:block",
"result_state": {
"Name": "minecraft:deepslate",
"Properties": {
"axis": "y"
}
}
}

}
]
}
### Notes
#### Basin
Basins (aka. erosions) existed in all biomes before the surface rules were added. When the surface depth is less than or equal to 0, the topmost layer of the terrain is directly removed, leaving a bare stone basin. However, after the surface rules were added, they are somehow limited to only two biomes, frozen ocean and deep frozen ocean, and there is a bug when judging the water surface. In previous basins, blocks above sea level (blocks with Y>=63) were air, otherwise they were ice or water (Note that there were no aquifers or noise caves at that time). In the current vanilla surface rules, it is air when there is no water above it, which can lead to flowing water along the coast.

#### Carver
Due to a mistake in the code about carver, the behavior of the minecraft:water condition during carver generation is inconsistent with that during terrain generation. When generating terrain, the offset value is relative to the air-liquid contact surface (i.e. the block position of the air block). While during carver generation, the offset value is relative to the block position of the top liquid block. And because during carver generation, surface rules are only applied to dirt below when carving grass blocks or mycelium. The game assumes that there is no water above grass blocks and mycelium. Then during carving, grass blocks and mycelium may be carved into water, so there is at most one block of water above the dirt being processed by surface rules. Therefore, the offset value during carver generation can also be said to be relative to the top surface of the processing dirt.

Therefore, when generating terrain, offset values of 0 and -1 have the same effect: only succeed when there is no liquid above. But When carvers generates, if the offset value is -1, the condition is always successful, regardless of whether there is liquid above.

When surface rules were first added into the game (21w41a), the developers were not aware of the mistake in carver code and set the offset value to -1 when checking whether there is water above. As a result, grass blocks can be generated underwater during carver generation. Afterwards (21w43a and 22w07a), in order to resolve this bug, additional redundant minecraft:water conditions with offset values of 0 was added to the blocks that should not be generated underwater. Therefore, the current overworld surface rules in the vanilla game are slightly chaotic, but they can basically work as expected.

For pack and mod creators, it is important to avoid setting offset value to -1 in minecraft:water to ensure that it behaves the same during carver generation and terrain generation.

## Biome source parameter list presets
Through running the data generator, biome source parameter list presets of the overworld and the nether can be obtained. They are located in generated/reports/biome_parameters/. The biome generation defined therein is explained in detail on the Biome page.

