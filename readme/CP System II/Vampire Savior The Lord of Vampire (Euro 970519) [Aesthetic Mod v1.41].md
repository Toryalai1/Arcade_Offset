Vampire Savior The Lord of Vampire Euro 970519 Aesthetic Mod v1.41 by VMP_KyleW:

        [Details]
Intro
I'm an enthused VSAV player who is often finding new ways to be engaged in the game & it's competitive community. You can reach me on twitter - @VMP_KyleW 

Version: (1.41) Issued for public use, functional only for MisTer.

Update
September 10th, 2024, v1.41
Fix for MiSTer after encryption range updates in the CPS2 core.

February 5th, 2022, v1.4
Bulleta's secret into occurs when she has a win streak, Luna (Concrete Cave Cat) looks during EX attacks, Abaraya's Lady's rage now occurs at a 50% chance when the conditions are met - was previously 1/32. Moebius used Palmod to add Jedah's Japanese blood colors + Forever Torment's blood color into the color banks.

January 3rd, 2021, V1.3
Lei-Lei's ultra rare (MK) win-pose with a delayed Lin-Lin animation now has a condition that relies on the facing direction of Lei-Lei. Left-facing is in sync and right-facing is delayed.  

December 26th, 2020, V1.2
Fetus of God's stage/camera extents are now equal to every other stage in the game. Fetus of God has been added as a playable stage within the player-1 vs player-2 stage select chance tables. Now all stages have a 12/16 chance of being selected while stages associated to the selected characters have an additional 4/16 chance. Every stage, including Iron Horse Iron Terror & Fetus of God, is now available in every match while also having character's home stages maintain a higher probablility. Jedah's home stage is weighted towards Fetus of God.

December 4th, 2020, V1.1
In player-1 versus player-2 mode, stage selection is no longer solely weighted by character selection. Now all stages have a 11/16 chance of being selected while stages associated to the selected characters have an additional 5/16 chance of being selected. Every stage, including Iron Horse Iron Terror, is now available in every match while also having character's home stages maintain a higher probablility.
Each modification provides the decrypted address & data type for reference.

Goal
The goal of this mod adheres to two principles. First and most importantly, I am making a deliberate effort to not alter gameplay, such that this mod could be considered for use in the competitive VSAV Scene. Secondly, I am altering the accessibility of most secret content. This includes changing access conditions to secret character colors, stage colors & numerous rare animations. I did not alter conditions that were already accessible at a 50% probability rate. By undertaking this project, the need to quantify & document all of these rare occurrences arised. VSAV community members collaborated on a Discord channel. The results of everyone's hard work can be found on a new wiki page labeled VSAV Secrets. Users should reference this wiki page for a full list of Secrets and unlock conditions within VSAV. While changing access conditions for all of the rare animations, there are numerous ones that were not achievable, due to factors like, how that individual animation was programmed (Anakaris's alternate intro) or how interconnected the animation is to story mode functions (Jedah's alternate intro).
https://wiki.gbl.gg/w/Vampire_Savior/Secrets

Package Overview:
This (.zip) file contains every file needed to play an encrypted EU rom set. However, only (3) files are unique.
vsav(.key) is the standard encryption key, used to play encrypted roms.
vm3e(.03d) & vm3(.10b) are the only files that I directly modified. This is where conditions for secrets were changed. There was not enough room to add new conditions during the character select input assessment functions, so I had to jump to the free space at the very end of the OpCode and provide the entire function (including my modifications for specific inputs) there. This is why the second (.10b) file is needed.

Thank You to the many people who inspired, consulted & tested along the way: Jais, 9TNine, Alphakami/Tad, Felineki, N-Bee, Moebius, ViperSnake, Rotanibor, @SF2Platinum, JedPossum, ChooseGoose, Typhas, Ken, Ego, Zero-One, VickiViper

You may want to change this (.ZIP) file name to VSAV(.ZIP)

Aesthetic Modification Details are provided below:
_________________________________________________

Alternate Title Screen (0x10D2, OpCode)
This romset defaults to Coine Mode as Free Play, but users may choose to change the Coin Mode, within Service menu 7-1, to another value. If that is done, add a coin without pressing Player-1 or Player-2 START and the alternate title screen will be displayed. Be mindful that an emulator will generate a separate file for managing these temporary menus settings, designed to be writted to the EPROM. If you want to remove the temporary file and go back to the romset defaults, delete (VSAV.NV) within your emulator directory.

Service Menu Settings
I altered three default Euro settings in the Service Menu to align with our tournament standards
Coin Mode = Free Play (No Coins Needed) (0x2456, Data Table)
Regulation = OFF (Blood is on) (0x245C, Data Table)
Game Speed = Turbo 3 (0x2469, Data Table)

Match Demos
I changed the (8) demo matches to show unique characters & new match-ups. Some examples are
Dark Gallon vs Oboro (0x5C08, OpCode)
Demitri vs Demitri (0x5C0C, OpCode)
Anakaris vs Victor(0x5C10, OpCode)
Gallon vs Dark Gallon (0x5C14, OpCode)
Sasquatch vs Sasquatch (0x5C18, OpCode)
Dark Force Zabel vs Dark Force Zabel (They do not attack, this is just for laughs)(0x5C1C, OpCode)
Victor vs Oboro (0x5C20, OpCode)
Lei-Lei vs Jedah (0x5C24, OpCode)

Stage Variants (0x92C2, OpCode)
PL-1 or PL-2 can hold START just before the match loads to enable the boss version of a stage.

Stage Selection (0xC468, Data Table)
All stages have an 12/16 chance of being selected while stages associated to the selected characters have an additional 4/16 chance

Title Version Screen (Splash Page) (0x1C93D, ASCII)
Replaced the title Vampire Savior w/ the text "VSAV AESTHETIC", so users are aware this is not the original rom set. I left "970519EURO" so players know which version was altered. Added my name too.

Fetus of God camera/stage extents (0x1F27C, OpCode)
Starting at this address, values are now equal to 0x01000280. This sets the left & right boundaries equal to every other stage in the game.

Special Character Colors (0x20B38, OpCode moved into the empty space within file #10)
Select any Character with LP+LK or MP+MK to access their Auto-Guard only colors. If two players choose the same character and the same special color, one player will be forced as their default color.

Rankings
I updated the Rankings to represent select Major VSAV tournaments & Japanese Arcades, with the associated character portrait referencing the Tournament Organizor or a prominant player. I wish there were more room to add other references like Apocalypse of Darkstalkers (Chrono Zabel) or BigOne2nd (Nakanishi/OKKB/Nishiken).

Score Rankings (Tournaments)
MWC Felicia - Makai World Cup showing Ailerus Felicia (0x218E4, ASCII)
DPG Q-Bee - Devil's PlayGround showing Sakamoto Q-Bee (0x218F4, ASCII)
DDF Demitri - Darkstalkers Duo Fest showing Dara Demitri (0x21904, ASCII)
DCC Phobos - Darkstalkers Combination Cup, this would show T2ya Zabel, but I chose to depict the unused sprite of Phobos because DDC & T2ya are retired. (0x21914, ASCII)
D.R Morrigan - Darkstakers Death & Rebirth showing KyleW Morrigan (0x21924, ASCII)

VS Rankings (Arcades)
MIK Lei-Lei - Mikado Arcade showing Ego Lei-Lei (0x21944, ASCII)
F1R Jedah - Playland F1R showing Oouchi & Shimatsuya Jedah (0x21954, ASCII)
NAM Gallon - Namba Hills showing Takahashi Gallon (0x21964, ASCII)
SHU Sasquatch - Super Shuttle showing Hosokawa Sasquatch (0x21974, ASCII)
AMF Aulbath - AmFantastica showing Bow Aulbath (0x21984, ASCII)

Intro Animations
Bulleta - Have a win-streak greater than 0 to access vs Gallon & Dark Gallon only intro animation (0x2F6B8, Opcode)
Morrigan - Have a win-streak greater than 0 to access the CPU only intro animation. (0x391F0, OpCode)
Zabel - Hold the LP button before the characters appear to access the vs Lei-Lei only intro animation. (0x38116, OpCode)
Zabel - Hold the LK button before the characters appear to access the vs Bulleta only intro animation. (La Manta will not appear for this animation) (0x3810E, OpCode)
Gallon - Hold any button before the characters appear to access Dark Gallon's intro animation. (0x33550, OpCode) 
Aulbath - Hold any button before the characters appear to access his mirror match only intro animation. (0x44370, OpCode)
Felicia - Hold any button before the characters appear to access her CPU only intro animation. (0x40A1E, OpCode) (0x40A1E, OpCode)
Anakaris - Due to how Anakaris is programmed, I am not able to impliment his vs CPU & vs Felicia custom intros. (0x3E234, OpCode) & (0x409FA, OpCode)
Jedah - Due to how Boss Fight Jedah is programmed, I am not able to impliment his custom Intro in versus mode. (0x529D8, OpCode)

Attacks
Zabel's Dark Force activation now has a 50% chance of the Afro appearing. It was previously a 1/16 probability. (0x38578, OpCode)

Taunts
Zabel - Input LP+Start for a high probability of accessing the Lei-Lei only taunt. (0x37EEE, OpCode)
Zabel - Input LK+Start for a high probability of accessing the Bulleta only taunt. (0x37EF6, OpCode)
Anakaris - Corpse Drop taunt now has a high probability of animating by inputting LP+START. It was previously a low probability of the RNG function. (0x3D97A, OpCode)
Anakaris - Corpse Breakdance taunt is now enabled when the opponent has a projectile on the screen. Input START+Taunt to activate this rare animation. (Does not include MO or LI) (0x3D902, OpCode)
Anakaris - Mummy Dance taunt is now enabled while the opponent is cursed. Input PPP+START to activate this ultra rare animation. (0x3D91C, OpCode) (0x3D9BC, OpCode)

Win-Poses
Bulleta's story-mode win-pose, value 0x0A, is added to here chance-table when there is no button override. (0x2F7AA, OpCode)
Zabel's MK win-animation now has a 50% chance of the Afro appearing. It was previously a 1/16 probability. (0x382C4, OpCode)
Zabel's Perfect+LP win-animation variant is now accessible by holding START+LP. (0x3820E, OpCode)
Morrigan's rare win-poses were added to her chance-table when there is no button override. I added a 4th one, because it works, but it's not designed. The white doll will not float. (0x39322, OpCode)
Anakaris's Enhanced win-poses, are now also unlocked by obtaining a Cheap Finish. The previous condition of a Dark Force Deathblow did not work as designed. (0x3E4CC, OpCode)
Felicia's Perfect-Win fist pump now has a (25%) probability of occuring when there is no button overide. All button overrrides still work normally. Every other win-pose now has a 12.5% chance of occuring. (0x40B94, OpCode)
Lei-Lei's alternate audio is now accessible by obtaining an EX-Finish then selecting the LK or MP win-pose. (0x4ACF4, OpCode)
Lei-Lei's Delayed Lin-Lin - This win-pose is now enabled when Lei-Lei's MK-Win-pose is facing to the right. (0x62EBA, OpCode)
Lilith's story-mode win-pose, value 0x0E, is added to her chance-table when there is no button override. (0x4D45A, OpCode)

Stage Animations
Concrete Cave - Luna the cat now looks at the players during EX attacks (0x7E0E0, OpCode)
Abaraya - Lady enters a rage state at a 50% probability once all otehr conditions are met. This was previously a 1/32 chance. Players must both be low health and use an EX attack. (0x7F106, Opcode Table)

            Vampire Savior The Lord of Vampire (Aesthetic Mod v1.3) by VMP_KyleW (https://twitter.com/VMP_KyleW)
