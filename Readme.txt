Addendum by Tasunke for Codename: 1240 AD Mod

Inspired by CIV and Md2:TW

This Mod is a way for the two games to interact with each other.

Due to the nature of play caused by the interaction of these two games, a system developed by myself, I have 
edited the way that the game (CIV) works in order to accomodate the increased pace.














Created by Mikel Olson for Civilization IV Beyond the Sword

V6.0 07-11-2009
Updated for Beyond the Sword v3.19
Beyond the Sword v3.19 introduced some changes to the code for global warming which I've merged with my own changes to make what should be the best of both worlds.  Forests and other features decrease the chance of global warming as introduced in v3.19, but you'll get fallout instead of a desert whenever it should occur.  This is of course still optional, and engaged by setting the GLOBAL_WARMING_PROB to something greater than 100 in the xml .

V5.1 07-05-2007
Fixed a bug I created when I updated the global warming code to match the new technique.

V5.0 07-05-2007
Contains solver changes through 07-05-2007 release (v019)
The big update this time is for the new, relativly I'm a little slow this time, 3.17 patch.  They appear to have made a couple changes to the global warming system detailed a little below:
First: Certain features on the planet will decrease the effect of global warming.  I didn't get too deep into it but it looks like forests and certain city improvements play big roles.
Second: The system used to remove features on the land and convert them to "eWarmingTerrain" (desert) but now if a feature exists on the tile it will only remove the feature the first time it hits it.  Only when a tile has no feature will it convert to desert.
These changes should slow down the impact of global warming but I still prefer my reversible method of global warming.  I've combined it with the preventative processes they added so that the only net change of my method is as follows: if the tile was going to get a feature removed, or turned to desert it will instead get coated in fallout.  As noted below this is still an entirely optional change which is off by default.

V4.0 10-04-2007
A couple significant changes have been made to this version first and foremost being that this version is updated for v3.13.  Because 3.13 fixed everything in Solver's patch those changes have now been removed.
The patch also changed the way that colony maintenance is handled so I have removed my governed colony changes.  I did this to eliminate the need for my changes to the globaldefines.xml file and to try out the new system they have implemented.  They have put a limit on colony chanrges based on distance from the capital and may have patched out the need for my method altogether.  If that is not the case, rest assured I will put governedcolonies back in.
On a final note, they completely buggered up the way that colony leaders are chosen.  To get this release out ASAP for 3.13 I only did a precursory check and change on the colony leader choosing methods.  Based on my limited testing it seems to work but if you run into any trouble creating a colony with >= 32 civs let me know.
Source code is also missing for this round, I've been out of town all day and really need to go to sleep.  Look for it in the next revision.

A recap:
Up to 40civs: IN
Colonies when >32 civs: IN
Fallout Changes: IN
Governed Colonies: OUT
Sourcecode: OUT

Let me know if you have any trouble in my thread over at civfanatics and have fun with the new version!


V3.1 08-29-2007
Contains solver changes through 08-29-2007 release

Updated to include new solver changes released today.  Also updated the source code files which now include the changes I made for the global warming options.  I forgot to update the source code files last time, oops.


V3.0 08-16-2007
Contains solver changes through 08-16-2007 release

I've added a new alternative form of global warming in this release.  Instead of turning random tiles to desert, it will drop fallout on the random tiles.  As with my governed colony option, this is off be default (instead using the normal desert technique).  To activate this new form of global warming open your GlobalDefines.xml file in a text editor.  Find the GLOBAL_WARMING_PROB value and add 100 to the value.  Any value over 100 will use my new method and be treated as that value less 100.
Ex:
A value of 20 will turn tiles to desert with a probability of 20% (The default shipping method)
A value of 120 will drop fallout on tiles with a probability of 20%

I prefer this method of global warming because you can stave off the effects with enough workers scrubbing.


V2.1 08-15-2007

I've added in the latest version of solver's unoffical patch.  If you prefer not to use it, just keep using V2.  I've added a copy of my working 34civ worldbuilder save in the 40civs mod folder and I've also included the source files I modified as per a request.  Some notes about the source code changes are below:

I've changed three files.  You can find them in the 40civs21Source.zip under the 40civs folder.  I've marked all my changes with a comment of my name (Mikel) so they should be pretty easy to find.  If you use my changes in another mod, I'd appreciate a byline in your readme/notes.  NOTE: The three source files included here contain other changes by solver and thus may not compile without additional files.  My code changes can be copy pasted and work just fine though.
CvDefines.h - Changed the define value for max players from 18 to 40
CvCity.cpp - Added code for governing a colony - uses a value in xml to decrease colony costs on a continent with a gov center (versilles/forbidden palace)
CvPlayer.cpp - Modified the SplitEmpire code to allow colonies to spawn as teams already in play.

An important note: The CvCity.cpp changes request a new value in your GlobalDefines.xml
	<Define>
		<DefineName>GOVERNED_COLONY_MULTIPLYER</DefineName>
		<fDefineFloatVal>1</fDefineFloatVal>
	</Define>
A 1 for the value disables it making gameplay EXACTLY the same as default.  I think that a value of 0.667 improves gameplay, feel free to adjust it to whatever you prefer.


V2

I've exposed a new variable to the globaldefines.xml file "GOVERNED_COLONY_MULTIPLYER"
This multiplier affects colonies where there is a government center like the forbidden palace or the versaiiles.  It defaults to 1 which makes it exactly like the default game but can be changed to any floating point value.
Ex: If it's set to 0.5 a colony on the same continent as the forbidden palace would only have 1/2 the normal colony costs.

Because the dll now uses this modified XML file it is more complicated to combine it with other mods.  To combine it you now must add the following lines to your globaldefines.xml:

<Define>
	<DefineName>GOVERNED_COLONY_MULTIPLYER</DefineName>
	<fDefineFloatVal>1</fDefineFloatVal>
</Define>


V1

This modified dll changes the way that colonies are started so that colonies can be formed as a civilization type already in play.  Leaders who are in play should not appear as colony leaders.
I also increased the player limit to 40 so that all 34 civilizations can be in play AND colonies can still be formed.  I do NOT recommend starting a game with more than 34 players.

Installation/Usage:
Extract the 40civs folder to your Beyond the Sword\Mods folder.
The dll file should work with any other mod that doesn't modify the dll file.