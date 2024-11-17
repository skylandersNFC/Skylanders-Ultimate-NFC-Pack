Imaginators Error Bypass for Consoles

Instructions:

1. Place the Heartbreaker Buckshot NFC tag on the portal.
2. When the magic element symbol appears on-screen, unplug the portal before the "Your Skylander may be corrupted" message is displayed.
3. Remove the Heartbreaker Buckshot NFC tag and replace it with the Error Bypass NFC tag while the portal remains unplugged.
4. Plug the portal back in.
5. The Error Bypass tag will bypass the error screen and load the Heartbreaker Buckshot NFC tag from RAM.

Note: Changes cannot be saved to this Heartbreaker Buckshot, but it can still be used for gameplay on consoles.

Second Note: The "Heartbreaker Buckshot (Max Level Bottom/Top Path)" dumps won't have any effect on real consoles.
You will still receive a Level 1 Heartbreaker Buckshot.
These dumps are intended for Cemu with the "Removing Digital Signatures Mod".

Special thanks to Texthead, ItsSecretNate, Salty and BoomBringer for making this possible.

#################################

Tehnical Explanation by Texthead:

Hi there. The error bypass dump is a reskin of a dump I created a while ago to load Heartbreaker Buckshot into Imaginators. The method it uses does work for all other figures, with the caveat being it’ll act as a “ghost tag”, so the Portal will not read any successful data from the figure nor write any of it back.

The way it works isn’t due to overloading the Portal thread, but instead due to a memory allocation issue if both the RAM of the game and the “RAM” (figure indices cached in the Portal’s memory) are synced up correctly. If the figure index for the error bypass dump correlates to the exact same figure index of a previous figure (of which’s ID will remain cached), when the game processes the tag header, it fails to correctly read the rest of this tag and incidentally ends up pulling the data from that very cached figure.

This happens due to a small exploit and issue regarding byte 0x13 of the figure/tag header. When this is not 0, the game is meant to reject the figurine, but this is only functionally complete in SSA, SG, and STT. In SSF, SSC, and SI, it’ll do the undefined behaviour as stated.

Aligning the figure indices of the Portal is much easier using an emulated portal, as all you need to do is load the new tag in the same slot as the previous one. However, for use with physical Portals, you can reset the figure indices either by sending commands to it using software, whilst the game is interacting with it, or simply unplug and replug the Portal before scanning the first tag to put it in slot 0, and repeat for the second tag.

If any additional information is required, you may be able to find it here:
https://github.com/Texthead1/Runes/blob/master/Docs/SkylanderFormat.md#error-byte