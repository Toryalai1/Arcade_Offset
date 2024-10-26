# Vampire Savior The Lord of Vampire Euro 970519 Aesthetic Mod v1.5 by VMP_KyleW and VMP_MBD
---

## Table of Contents
---

- Foreword
- Revision History
- Goal
- Package Overview
- Aesthetic Modification Details
	- Service Menu Settings
	- Oboro Bishamon
	- Training Mode
	- Match Demos
	- Miscellaneous Changes
	- Rankings
	- Intro Animations
	- Attacks
	- Taunts
	- Win-Poses
	- Stage Animations/Changes
- Special Thanks


## Foreword
---

### VMP_KyleW

I'm an enthused VSAV player who is often finding new ways to be engaged in the game and its competitive community. You can reach me on twitter - @VMP_KyleW 

### VMP_MBD

Hello. I'm MBD, also an enthused Vsav player and hacker/engineer, and good pals with KyleW.

When Jotego updated the MiSTer CPS2 core encryption ranges in 2022, Aesthetic Edition broke on MiSTer. While there were some workarounds, I vowed to someday fix it, and I did end up doing that in September of 2024, just in time for Makai World Cup 2024.

During that event, I couldn't help but think of a few changes I wanted to make, and with KyleW's partnership and blessing, I bring you Aesthetic Edition v.1.5!

I also built some tooling to aid in the reverse engineering and development process for CPS2 ROMhacking ([GitHub](https://github.com/MBDesu)). You can also reach me on [Twitter](https://twitter.com/VMP_MBD) or [BlueSky](https://bsky.app/profile/vmpmbd.bsky.social).


## Revision History
---

### October 31, 2024, v1.5

Full details below, but briefly:

- Oboro is playable (and toggleable)
- There's a training mode (it's toggleable, too)
- There's an instant rematch now (optional for both players)
- Dark Gallon is easier to select
- Original versions of BI's 22PP deathblows vs BI and VI have a 50% chance to occur
- Demo match characters have colors other than LP now, and the demo matchups have been updated
- Title screen (the one with blue text -- er, well, it's orange now) has been updated to show more detailed version information
- Many Easter eggs
- A full writeup of changes, including code, can be found [here](https://publish.obsidian.md/mbd/Projects/CPS2/AE+1.5/AE+1.5+Notes)

### September 10th, 2024, v1.41

Fix for MiSTer after encryption range updates in the CPS2 core.

### February 5th, 2022, v1.4

Bulleta's secret into occurs when she has a win streak, Luna (Concrete Cave Cat) looks during EX attacks, Abaraya's Lady's rage now occurs at a 50% chance when the conditions are met - was previously 1/32. Moebius used Palmod to add Jedah's Japanese blood colors + Forever Torment's blood color into the color banks.


### January 3rd, 2021, v1.3

Lei-Lei's ultra rare (MK) win-pose with a delayed Lin-Lin animation now has a condition that relies on the facing direction of Lei-Lei. Left-facing is in sync and right-facing is delayed.  


### December 26th, 2020, v1.2

Fetus of God's stage/camera extents are now equal to every other stage in the game. Fetus of God has been added as a playable stage within the player-1 vs player-2 stage select chance tables. Now all stages have a 12/16 chance of being selected while stages associated to the selected characters have an additional 4/16 chance. Every stage, including Iron Horse Iron Terror & Fetus of God, is now available in every match while also having character's home stages maintain a higher probablility. Jedah's home stage is weighted towards Fetus of God.

### December 4th, 2020, v1.1

In player-1 versus player-2 mode, stage selection is no longer solely weighted by character selection. Now all stages have a 11/16 chance of being selected while stages associated to the selected characters have an additional 5/16 chance of being selected. Every stage, including Iron Horse Iron Terror, is now available in every match while also having character's home stages maintain a higher probablility.
Each modification provides the decrypted address & data type for reference.


## Goal
---

The goal of this mod adheres to two principles:

- No altered gameplay.
	This is so this mod could be considered for use in the competitive VSAV scene, and gameplay alterations would discourage this.

- Accessibility of secret content.
	This includes changing access conditions to secret character colors, stage colors, and numerous rare animations. Conditions that were already accessible at a 50% probability rate were not altered. In the undertaking of this project, the need to quantify and document all of these rare occurrences arose. VSAV community members collaborated on a Discord channel, and the results of everyone's hard work can be found on a new wiki page labeled [VSAV Secrets](https://wiki.gbl.gg/w/Vampire_Savior/Secrets). Users should reference this wiki page for a full list of Secrets and unlock conditions within VSAV.
	
	Though many secret conditions were made more accessible, there were numerous ones that were not achievable, due to factors like how that individual animation was programmed (Anakaris's alternate intro) or how interconnected the animation is to story mode functions (Jedah's alternate intro).

## Package Overview
---

This `.zip` file contains every file needed to play an encrypted EU rom set. However, only (4) files are unique.
`vsav.key` is the standard encryption key, used to play encrypted ROMs.

`vm3e.03d`, `vm3e.04d` and `vm3.10b` are the only files that have been directly modified. This is where the below changes were made.


You may want to change this `.zip` file name to `vsav.zip`.


## Aesthetic Modification Details
---

### Service Menu Settings

Three settings in the Service Menu were changed to align with competitive tournament standards:

|    Setting | Value          | Code Location(s) |
| ---------: | -------------- | :--------------: |
|  Coin Mode | Free Play      |     `0x2456`     |
| Regulation | OFF (blood on) |     `0x245c`     |
| Game Speed | Turbo 3        |     `0x2469`     |


### Oboro Bishamon

Oboro Bishamon is playable. You may toggle the ability to select Oboro by setting Coin Mode to `1 COIN 1 CREDIT`, which has been renamed to `OBORO MODE`.

To select Oboro, while the Coin Mode is set to `OBORO MODE`, press Down while Bishamon is highlighted.

Custom code that checks if the current character is Bishamon and if Down was pressed *and* Coin Mode is `1 COIN 1 CREDIT` was written at `0xbf6ae`, and code at `0x20a7c` was altered to jump there. Additionally, the text at `0xf752` for the coin mode was altered.


### Training Mode

There is a training mode. You can toggle TOREMO on by setting Lives to 1, which has been renamed to `TOREMO`.

|                         Feature | Description                                                                                                                                                                                                                       |                                              Code Location(s)                                              |
| ------------------------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------: |
|                          Toggle | Set Lives to 1 (`TOREMO`) in the service menu to toggle training mode on; set to anything else to turn it off                                                                                                                     |                                                 `0x1064a`                                                  |
|                 Infinite Health | While training mode is active and in a match, both players have effectively infinite health and bats. Health will refill after a player has been at neutral for 64 (`0x40`) frames. If a player is KO'd, the game will not end    | `0xa6a0`,<br>`0x18a7c`,<br>`0x281a6`,<br>`0x2090e`,<br>`0x2980a`,<br>`0xbf880`,<br>`0xbf8e6`,<br>`0xbf8fe` |
|   P1 Start presses P2 Start too | While training mode is active, on the title screen/character select, pressing P1 Start will also press P2 Start. This is to enable single controller training mode when combined with the ability for P1 to select P2's character |                                           `0x8cc4`,<br>`0xbf98a`                                           |
|                   Infinite Time | While training mode is active and in a match, the in match clock will not decrease                                                                                                                                                |                                           `0x9822`,<br>`0xbf8c8`                                           |
|       P1 Selects P2's Character | While training mode is active, P1 can select P2's character with the same controller after selecting their own, unless P2 selects first (it is a 2 player game!)                                                                  |                                          `0x20974`,<br>`0xbf948`                                           |
| Fast Return to Character Select | While training mode is active and in a match, pressing `Up`+`Start` on either controller will quickly return to character select                                                                                                  |                                          `0x223ee`,<br>`0xbf8ac`                                           |
|                  Infinite Meter | While training mode is active and in a match, performing any meter gaining action will grant 99 meters                                                                                                                            |                                          `0x29a3a`,<br>`0xbf970`                                           |


### Instant Rematch

When both players hold `LP`+`MP` for 1 second at match end, before the win pose advances too far, rematch with same characters will happen instantly. Input window begins immediately after the deathblow lands.


### Easy Dark Gallon Selection

You may select Dark Gallon by pressing Up while Gallon is highlighted. This also enables the player to select unintended palettes for Dark Gallon, which have varying flashy graphics that may or may not warrant a seizure warning.

Code change is a single byte change at `0x211f7` (data), setting it to `0x12`.


### Match Demos

The eight demo matches were changed to reference/spotlight members of the community and memorable grand finals from the competitive scene.

| Demo Number |                                     Matchup                                      | Code Location(s) |
| :---------: | :------------------------------------------------------------------------------: | :--------------: |
|      1      | [Sev (BI) vs MBD (DE)](https://youtu.be/hce3U_k5Uzw?si=E9CdPC0F2Po__AZB&t=7621)  |     `0x5c08`     |
|      2      |                      YetiGhettoSlang (SA) vs MiniMaww (GA)                       |     `0x5c0c`     |
|      3      |                          Ailerus (FE) vs Zero-One (FE)                           |     `0x5c10`     |
|      4      |                           Kajoq (LE) vs MightyMar (AN)                           |     `0x5c14`     |
|      5      |    [Takahashi (GA) vs Kame (VI)](https://www.youtube.com/watch?v=OYcfbY34hnI)    |     `0x5c18`     |
|      6      | [Kaji (LI) vs Bow (AU)](https://youtu.be/djLeAZnCdpc?si=GCFyp26NAYFqJRhJ&t=8055) |     `0x5c1c`     |
|      7      |                           Oboro vs Bishamon (funsies)                            |     `0x5c20`     |
|      8      |   Bulleta vs Bulleta (funsies, check out the command grab on the second loop!)   |     `0x5c24`     |

 Additionally, code was written at `0xa3d0` and `0xbf6d4` to set character costume colors in demo matches.


### Miscellaneous Changes

|                   Change | Description                                                                                                                                                                                                                                                                                                                                                                                                                                   |  Code Location(s)   |
| -----------------------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----------------: |
|           Stage variants | Hold `Start` before a match begins to access the boss color variant of any stage that has one                                                                                                                                                                                                                                                                                                                                                 |      `0x92c2`       |
|          Stage selection | All stages have an equal (12/16) chance of being selected while stages associated with the selected character have an additional 4/16 chance                                                                                                                                                                                                                                                                                                  |      `0xc468`       |
|     Title version screen | The title screen that shows before the copyright warning has been updated to show `V S A V   A E S T H E T I C` along with the version information. `EURO 970519` is displayed to ensure players know the version this hack originated from. The text has been changed to orange. The authors are also credited.                                                                                                                              | `0x4f26`, `0x1c93d` |
| Special character colors | Select any character with `LP`+`LK` or `MP`+`MK` to access their P1 or P2 Auto-Guard colors, respectively. If two players choose the same character and Auto-Guard color, the second will be defaulted to their `LP` color. *Note:* the code for this overwrote an unused/debug test menu option for debugging messages. Prior to 1.41, this code was in empty space at the end of `vm3.10b`, but this is the change that broke AE on MiSTer! |      `0x10bec`      |
|   Alternate title screen | Aesthetic Edition changes the default coin mode to Free Play via `nvram` (EEPROM), but if it is changed to any other setting, the original Jedah's Damnation title screen is accessible by inserting a coin before pressing start before the title screen                                                                                                                                                                                     |      `0x10d2`       |


### Rankings

The various rankings shown between demo matches were updated to represent select major Vampire Savior tournaments and Japanese arcades, with signature players or tournament organizers from them being represented by their character.

Would have loved to reference Apocalypse of Darkstalkers (Chrono Zabel) or BigOne2nd (Nakanishi/OKKB/Nishiken) as well!


#### Score Rankings (Tournaments)

| Initials | Description                                                                                                                                           | Code Location(s) |
| :------: | ----------------------------------------------------------------------------------------------------------------------------------------------------- | :--------------: |
|   MWC    | Makai World Cup, showing Ailerus Felicia                                                                                                              |    `0x218e4`     |
|   DPG    | Devil's PlayGround, showing Sakamoto Q-Bee                                                                                                            |    `0x218f4`     |
|   DDF    | Darkstalkers Duo Fest, showing Dara Demitri                                                                                                           |    `0x21904`     |
|   DCC    | Darkstalkers Combination Cup, showing Phobos. This would show T2ya Zabel, but they are retired, and so the unused Phobos sprite was shown off instead |    `0x21914`     |
|   D.R    | Darkstalkers: Death and Rebirth, showing KyleW Morrigan                                                                                               |    `0x21924`     |


#### VS Rankings (Arcades)

| Initials | Description                                       | Code Location(s) |
| :------: | ------------------------------------------------- | :--------------: |
|   MIK    | Mikado Arcade, showing Ego Lei-Lei                |    `0x21944`     |
|   F1R    | Playland F1R, showing Oouchi and Shimatsuya Jedah |    `0x21954`     |
|   NAM    | Namba Hills, showing Takahashi Gallon             |    `0x21964`     |
|   BOX    | Game Box Q3, showing Hosokawa Sasquatch           |    `0x21974`     |
|   AMF    | Okayama Fantasista, showing Bow Aulbath           |    `0x21984`     |


### Intro Animations

| Character | Description                                                                                                                                                |                              Code Location(s)                              |
| --------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------: |
|   Bulleta | vs Gallon and Dark Gallon intro animation is accessible with a win streak greater than 0                                                                   |                                 `0x2f6b8`                                  |
|  Morrigan | vs CPU intro animation is accessible with a win streak greater than 0                                                                                      |                                 `0x391f0`                                  |
|     Zabel | vs Lei-Lei intro animation is accessible if holding `LP` before the characters appear at round start                                                       |                                 `0x38116`                                  |
|     Zabel | vs Bulleta intro animation is accessible if holding `LK` before the characters appear at round start (Le Marta will not appear)                            |                                 `0x3810e`                                  |
|    Gallon | Dark Gallon's intro animation is accessible if holding any button before the characters appear at round start                                              |                                 `0x33550`                                  |
|   Aulbath | vs Aulbath intro animation is accessible if holding any button before the characters appear at round start                                                 |                                 `0x44370`                                  |
|   Felicia | vs CPU intro animation is accessible if holding any button before the characters appear at round start                                                     |                                 `0x40a1e`                                  |
|  Anakaris | Anakaris's vs CPU and vs Felicia intros are not accessible due to how they are programmed :(                                                               |                           `0x3e234`<br>`0x409fa`                           |
|     Jedah | Jedah's boss intro is not accessible due to how it is programmed :(                                                                                        |                                 `0x529d8`                                  |
|     Oboro | Oboro's intro animations have been significantly shortened and his vs Bishamon intro has been removed. The floating armor could not be sped up, however :( | `0x53cec`<br>`0x5400a`<br>`0x54050`<br>`0x54092`<br>`0x540a8`<br>`0x540be` |


### Attacks

| Character | Description                                                                    | Code Location(s) |
| --------: | ------------------------------------------------------------------------------ | :--------------: |
|     Zabel | Zabel's Dark Force has a 50% chance of having an afro (previously 1/16 chance) |    `0x38578`     |


### Taunts

| Character | Description                                                                                           | Code Location(s) |
| --------: | ----------------------------------------------------------------------------------------------------- | :--------------: |
|     Zabel | Input `LP`+`Start` for a high probability of performing the unique vs Lei-Lei taunt                   |    `0x37eee`     |
|     Zabel | Input `LK`+`Start` for a high probability of performing the unique vs Bulleta taunt                   |    `0x37ef6`     |
|  Anakaris | Input `LP`+`Start` for a high probability of performing the Corpse Drop taunt                         |    `0x3d97a`     |
|  Anakaris | Input `PPP`+`Start` to perform the Corpse Breakdance when the opponent has a projectile on the screen |    `0x3d902`     |
|  Anakaris | Input `PPP`+`Start` to perform the Mummy Dance taunt when the opponent is cursed                      |    `0x3d91c`     |


### Win-Poses

| Character | Description                                                                                                                                                                                                                                                           |                                Code Location(s)                                 |
| --------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----------------------------------------------------------------------------: |
|   Bulleta | Bulleta's story mode win pose may occur when the player does not override with a button                                                                                                                                                                               |                                    `0x2f7aa`                                    |
|     Zabel | Zabel's `MK` win pose has a 50% chance of having an afro (previously 1/16)                                                                                                                                                                                            |                                    `0x382c4`                                    |
|  Morrigan | Morrigan's rare conditional win poses may occur when the player does not override with a button. A 4th taunt was also added, but it will not animate as designed (white doll)                                                                                         |                                    `0x39322`                                    |
|  Anakaris | Anakaris's deathblow-dependent win poses are now also possible to attain with a Cheap Finish (previously, a Dark Force deathblow, which did not work as intended)                                                                                                     |                                    `0x3e4cc`                                    |
|  Anakaris | Anakaris's coins win pose (`LK`) will now always shoot big coins when the player is the `PP` color. This is an homage to the one and only MightyMar, who is said to have never caught a big coin.                                                                     |                 `0x5d3fc`; additional code written at `0xbf69a`                 |
|   Felicia | Felicia's Perfect win pose with the first pump has a 25% chance of occurring when the player does not override with a button. Every other win pose has a 12.5% chance of occurring                                                                                    |                                    `0x40b94`                                    |
|  Bishamon | Bishamon's Togakubi Sarashi (aka Slap Chop) (`22`+`PP`) has unique deathblow animations and sprites against the entire cast. In the Euro ROM, these sprites were altered or censored in some cases. They have a 50% chance to be their uncensored version (vs BI, VI) | `0x6d674`,<br>`0x6d67a`,<br>additional code written at: `0xbf708`,<br>`0xbf75e` |
|   Lei-Lei | Alternate Lei-Lei audio will play when the player receives an EX Finish deathblow and selects the `LK` or `MP` win pose                                                                                                                                               |                                    `0x4acf4`                                    |
|   Lei-Lei | Lei-Lei's delayed Lin-Lin win pose is enabled when Lei-Lei is facing right (previously a 1/256 chance)                                                                                                                                                                |                                    `0x62eba`                                    |
|    Lilith | Lilith's story mode win pose may occur when the player does not override with a button                                                                                                                                                                                |                                    `0x4d45a`                                    |


### Stage Animations/Changes

|         Stage | Description                                                                                                                                  | Code Location(s) |
| ------------: | -------------------------------------------------------------------------------------------------------------------------------------------- | :--------------: |
| Concrete Cave | Luna the cat now looks at the players when they perform EX attacks                                                                           |    `0x7e0e0`     |
|       Abaraya | Obaa-chan's rage state now has a 50% chance of occurring when the conditions are met (both players low health and one performs an EX attack) |    `0x7f106`     |
|       Abaraya | Hype Dog's palette has been modified to resemble Moebius's puppers, Monty (normal) and Lola (boss)                                           |                  |
|  Fetus of God | Camera/stage boundaries are now equal to `0x01000280`, the same as every other stage in the game                                             |    `0x1f27c`     |


## Special Thanks

Thank You to the many people who inspired, consulted & tested along the way:

- Jais
- 9TNine
- Alphakami/Tad
- Felineki
- N-Bee
- Moebius
- ViperSnake
- Rotanibor
- @SF2Platinum
- JedPossum
- ChooseGoose
- Typhas
- Ken
- Ego
- Zero-One
- VickiViper
- Dom
- Ciara
- Lucy
- Ada
