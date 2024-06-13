# Seed (world generation)
Seeds are values made up of character(s) (including negative or positive integers) that are used as the basis for generating every Minecraft world.[1]

## Contents
- 1 Compatibility
- 2 World generation
- 3 Determining the seed
- 4 Notable seeds
- 5 Technical
	- 5.1 Realms
	- 5.2 General
	- 5.3 Overlap between editions
	- 5.4 Generation quirks
		- 5.4.1 Changing terrain without changing some structures
		- 5.4.2 Repetition
- 6 Video
- 7 History
- 8 References
- 9 External links
	- 9.1 Bedrock and Java Editions
	- 9.2 Java Edition only

## Compatibility
Seeds are somewhat compatible across editions, with terrain generation and biomes being the same. However, the placement of generated structures differs between Java Edition and Bedrock Edition.

## World generation
Main article: World generation
Whenever the game has to generate a new world, it calls upon an algorithm known as Perlin noise. This algorithm outputs a pseudo-random value that is then used to determine the characteristics and features of the world. However, the algorithm always outputs the same value each time for a constant starting point (seed). Thus, the same seed generates the same terrain every time.

A world's seed is set when that world is created. By default, it is decided automatically, but it can also be set manually. Setting and reusing a seed from one world generates the same world. Either a number or a word/phrase can be used, including negatives. If a word/phrase is used, it is converted into a 32-bit integer.

Whenever the world generation algorithm is updated (usually by adding new biomes to the game), the same seed no longer generates the same terrain. If the seed or generator changes in a saved world, new chunks are based on the new seed and no longer match those from the old seed. Deleted chunks can regenerate if the seed and generator remain the same, but changes if either the seed or generator changes. In fact, deleting chunks is sometimes done to let newly-introduced features appear in an old world; see Tutorials/Updating old oceans in 1.13 using MCEdit.

Because seeds are simply random values read into an algorithm and not actually names of different worlds, using a certain seed does not result in a world with any relevance to the value of that seed. For instance, using a biome name as the seed does not necessarily result in the creation of a world with primarily that biome, nor does it spawn the player within the said biome.

An interactive widget is being loaded. If this does not work for you, please reload the page or check if JavaScript is enabled.
## Determining the seed
In Java Edition, the player can enter the command /seed to view the world's seed. This command is available in singleplayer worlds even if cheats are off. The player can also select 'Re-create' in the Worlds menu to see the seed.

In Bedrock Edition, the seed can be found on the world options screen. There are also seed templates that offers the player several pre-set seeds to generate worlds with specific features near the spawn point. Additionally, the beta version has a visible seed on the top of the screen.

## Notable seeds

  

This feature is exclusive to  Java Edition. 


The following map seeds have, at one point or another, been used for generating official Minecraft maps and resources or otherwise significant community material.

- TheJava Editiondemo world seed can be played in the full version by enteringNorth Carolinain the seed input.
- The PC Gamer demo world seed can be played in the appropriate era by enteringglacier, all lowercase unlike the famous seed where the G is capitalized, in the seed input.
- The seed for eachtitle screenpanoramaare as follows:
	- The panorama used betweenBeta 1.8 Pre-releaseand18w22cis either2151901553968352745or8091867987493326313,[2]generated betweenBeta 1.6.6andBeta 1.7.
	- Java Edition 1.13 is1458140401, which is the seed resulting from typing18w22ain as a seed, generated in snapshot18w22a.
	- Java Edition 1.14 is2802867088795589976, taken in18w48a.
	- Java Edition 1.15 is-4404205509303106230, taken in19w40a.
	- Java Edition 1.16 is6006096527635909600, taken in20w13a.
	- Java Edition 1.18 is2151901553968352745, taken in21w40a.
	- Java Edition 1.19 is-1696067516, which is the seed resulting from typingthewildupdatein as a seed, generated in snapshot22w15a.
	- Java Edition 1.20 is8554477380691140270, taken in23w14a.
- The seed for the originalpack.pngfile is3257840388504953787, generated inAlpha v1.2.2, and is also MinecraftBedrock Edition's New UI of Create New World's Example Seed sinceBedrock Edition beta 1.18.20.21and this seed spawns the player in aSavannaBiome inPosition: -208, 65, 0with these structures and other biomes since Bedrock beta 1.18.20.21.[3]It can also be generated betweenAlpha v1.2.0andBeta 1.7.3with minor population differences.
- The seed for the Skull on Firepaintingis either-6984854390176336655or-1044887956651363087, generated inAlpha v1.1.2_01or prior.[4]
- The seed used for the originalHerobrinedoctored screenshot is478868574082066804, generated inAlpha v1.0.16_02.
- The seed used for the originalHerobrinehoax livestream is3609313613745973624, generated inAlpha v1.0.17_04.

