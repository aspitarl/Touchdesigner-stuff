# Movie player improvement TODO

Note: termiology might not be right. Panel = container strips on left and right of video. 

This touch designer patch plays movie files from a selected folder, either in sequential (automatic) mode or with the movie index controlled dynamically through OSC. the folder contains a series of .mov files (sections) and which movie is playing is controlled by OSC too. 

## General questions

binding as master or reference? some things seem to become unbound. 

## Side parameter panel hiding
The side parameter panels are currently laid out in a horizontal arrangement with the video. This worked when we were doing 512x512 videos but pushes a 16/9 video off screen. I implemented a hacky way to fix this by changing the align order of the layout to push the panels off screen by pressing a on the keyboard. 

* Need a better method of hiding the panels that works regardless of video aspect ratio. Possibilities
     * panels are overlaid on top of the video, and the keyboard shortcut makes them appear/disappear
     * Can we have the panels pop out as floating windows? 

* other feature additions TODO:
   * control to quickly swich between a series of pre-selected folder. Currently having to open up file explorer.
   * switch from index mode to sequential mode.
   * Enable disable ableton link (binding becomes broken?)

## FX panel

There are 3 effects tops that can be applied to the video. There is a drop down menu to select `None, Voroni, Flow ABS, ...`. I have the parameters for these FX displaying in the left parameter panel. This is currently really hacky with the FX parameter panels being displayed all the time vertically and needing to be manually shrinked to little stripps.

    
    make groups of osc messages
    button to clear osc messages. 


## OSC communication

Ableton and TouchOSC communicate to touch designer through OSC. These messages show up as touch designer channels on the right parameter panel that can then be mapped to the FX on the left parameter panel. 


    * Any Better way of mapping FX?
        * OSC -> channel display  -> python expression of parameter
        * alternative: scaling in touch desiger and direct map
        * ideally this can be flexible, and automatically change with song somehow...

   * TODO:
      * split osc messages into sub groups e.g. `playback/index`, `FX/hue_shift`
      * the FX select dropdown menu is not following the OSC message (`FX_Index`)
      * add a button to the pulse to clear OSC messages. 

## Other 
cant scroll into the main top level container? have to scroll into some unused portion of the continer. 


# 04-05

group things into Bases and give glogal OP shortcut. create out top and give global shortcut to base ('me.name')

op.SHORTCUT_NAME.op('OUT')

* relative paths
    ../ = parent
    ../../ = parent(2)


* alt+n - null
* need to improve the display of FX parameter 'sub-panels'
     * Ideally, only one large sub-panel for the active FX would be shown. When changing the active FX the parameters for that FX will appear
     * alternatively we could combine FX tabs together. Some FX only have one tab. 

