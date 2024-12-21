-------------------------------------------------------------------------------------------------------

# General Changes

- The Sector 0 Trailer Access Conditions have been changed from '0F 0F 0F' (which is invalid and will lock the tag in Read-Only mode) to 'FF 07 80' (which is valid and keeps the tag in Read/Write mode) for all dumps, including Imaginators as well.
As a result, no more new NFC tags will be permanently bricked by incorrect flashing. Regardless of what you do, the tags will always remain Re-Writable.

# SuperChargers

- "6) Eon's Elite" folder had three Special dumps, instead of Eon's Elite ones. They were all fixed.

	Eon's Elite Slam Bam.dump
	
	Eon's Elite Voodood.dump
	
	Eon's Elite Zook.dump
	
-------------------------------------------------------------------------------------------------------