GOOGLE PLAY
<https://play.google.com/store/apps/developer?id=John+Wilde>

TODO
	* Allow time to be added to each clock during a game
	* Scroll input widget for setting clocks
	* At end of game show a chart with the distribution of time spent per move
	  for each player
 	* Allow clocks to be initialized to different times
	* Let user select image to be displayed on button
	  
DONE
    * Display animated icon showing Bronstein delay countdown (next to clock)
    * Add NumberFormat exception handling for bad initial time or other text input
	* Audio feedback when clock expires
	* Advanced FIDE time controls
	* Bronstein/Fischer timing option
	* Move counter (for eventual use with official FIDE tournament time control)
	* fixed bug whereby String.isEmpty() was being used, but
	  this is only valid for API > 9 (i.e. not for 2.1 or 2.2 devices)
	* Allow clocks to go negative
	* Lock 'portrait' orientation
	* Wake lock to prevent screen from dimming during play
	* Make pause notification persistent (not a 'Toast')
	* Fix bug that allows empty time field in preferences
	* Fixed package name in manifest
	* 'About' screen
	* NOT going to do this: "Haptic feedback on button press" clock is usually on the 
	  table so you can't really feel this.


Some development notes:

DYNAMIC BUTTON RESIZING

	The original plan was to shrink the button of the player whose clock is paused
	and expand the other player's button.  I tried a few techniques to get this 
	working but with no luck: 
	
	* used <scale> drawables which are supposed to resize when the setLevel(int) method
	  is called.  Level can vary between 0 and 10,000; 10,000 should make the image
	  large.
	  
	* specify the layout_weight programatically
	
	However, I couldn't get a these methods to look good so I went for the simpler 
	approach of just adjusting the transparency of the buttons.
  
  
ICON ASSET CREATION:
  
  1. Create icon as 72x72 document in inkscape, export as PNG 72x72
  2. Import into android asset builder
  	- set background to yellow (#ffcc00)
  	- set zoom crop to 10%
  3. Export as zip and extract into res folder
  
  Also, create 512x512 hi-res icon (for website) by scaling image in inkscape 
  to a 512x512 document and using the asset builder tool again.