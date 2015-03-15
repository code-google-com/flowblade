# Release Notes #

## Flowblade 0.16 ##
**Date: December 2, 2014**

**Flowblade 0.16** is the sixth release of Flowblade.

This release has only one major new feature, and marks a change in the approach until the 1.0 release is done.

The next 2-3 releases will contain at most 1 new major feature along with smaller enhancements and bug fixes. The releases will also come quicker, once every 3-4 months.

The previous release completed the editing concept and feature list needed for 1.0. The 1.0 release will be made before the end of 2015, after which the focus will shift immediately to the porting of the application to gtk3.

The code base refactoring has come to a conclusion with this release, and the focus when improving code readability will now shift to adding and improving comments.

### Main Features in this release ###
  * **Audio Master Meter** has been added to top level GUI to help working with audio.
  * New **Chroma Key** filter works better on blue and green screen keying than the existing Color Select filter
  * **Luma Key** enables keying based on image luma values
  * **Batch Rendering** was changed to use dbus instead of PID files and should now  actually work

#### Other features and enhancements ####
  * Add German translation
  * Add Italian translation
  * Fix Quick Enter and Quick Exit trim white blank display bug
  * Final round of refactoring before 1.0
  * Fix start-up problem from missing threads\_enter() - Louis C. Villa
  * Require pygtk 2.0 to fix start-up on some systems - Louis C. Villa
  * Update timeline tools overlay GUI
  * Make Clip Monitor remember displayed frame
  * Fix flashing black around monitor bug
  * Add keyboard shortcuts ALT + I and ALT + O to move to in and out points
  * View selector for media panel to display all or anly certain types of files
  * Add info on duplicate media items on load
  * Refactor and fix audio monitoring display update and exit



## Flowblade 0.14 ##
**Date: June 18, 2014**

**Flowblade 0.14** is the fifth release of Flowblade.

This release has some good new features and improvements, see below for more info. It also seems clear that the "release every 6 months" schedule suits the project well at this stage, and it will be kept for the future.

In the next release cycle attention  will be paid to rendering output files and media and project management.

New features for the next release have not been decided on yet, but MLT webFX module will be looked at, and there are some other services available that are not yet utilized by Flowblade.

## Installing Flowblade ##
See [Install Instructions](InstallInstructions.md).

### Main Features in this release ###
  * **Color Correction improvements** in this release take a major step forward.
    * New 3 band color correcting filter **Color Grading** makes professional level color manipulation possible on Flowblade
    * Industry standard Catmull-Rom based **Curves** filter (other FLOSS video editors use Bezier based implementations, which in my opinion are inferior)
    * RGB Adjustment filter is equipped with a new and much more intuitive editor and renamed as **Color Adjustment**.

Unfortunately the first two require repository version of **MLT (=>0.9.1)** which is not available on any distributions yet (Arch may have it).
  * **Spacer tool** makes it possible to move all timeline items on all the tracks as a single unit. If Control button is pressed all items on a single track can be moved. This makes it much quicker to restore relative positions of clips after edits that change positions between clips on different tracks.
  * **Audio levels** displayed on clips are now rendered much quicker and some earlier bugs were fixed.
  * **Range Log** functionality has been upgraded.
    * Range Log items can now be dragged onto Timeline
    * Timeline Clips can dragged to create Range Log items
    * Range Log items can be arranged into groups
    * ...and some other minor improvements and bug fixes
  * **Quick Enter and Quick Exit for trim tools** make editing more fluid. When using Trim, Roll and Slip -tools the edit now begins immediately on click. The old behaviour can be restored by setting a preference.

#### Other features and enhancements ####
  * Give info on a too long Fade for Clip
  * Improve Transition handles and error info.
  * Automatically create hidden folder for rendered clips
  * Automatically create hidden folder for thumbnails
  * Spanish translation
  * Make possible use wipe luma files from file system
  * Display media items as they are loaded
  * Add all filters on/off button
  * Add preference that sets last render directory as default on project open
  * Add warning if Render Profile fps different from Project Profile fps
  * Make track mute icons clickable for video/audio muting
  * Enable dragging clip from monitor to Timeline
  * CTRL + A support for media panel
  * Make mouse middle click zoom to sequence length on Timeline
  * Make Monitor playback interpolation user selectable
  * Fix hidden blank after sequence end bug
  * Fix render bug when minimizing windows
  * Fix Audio Mixer crash on exit
  * Fix 0.8 Project files forwards compatibility
  * Fix Titler crash on exit
  * Fix Filters editor delete out of index bug
  * Fix Quick Transition alignment bug
  * Fix Quick Transition undo bug
  * Fix window panels resize bug
  * Fix clip effects editor drag'n'drop bug
  * **GUI updates:** Render time value display before estimated time - speaker icon change sensitivity state - clip rects back into trim overlays - trim overlays GUI update - Image Sequence indicator - Graphics indicator - Render Proxy File menu item - selected compositor color to blue - Timeline overlay update - rendered clip length display in slo-mo dialog - vcodec and acodec info in clip info - audio icon update - artistic filter icon update

## Flowblade 0.12 ##
**Date: January 14, 2014**

**Flowblade 0.12** is the fourth release of Flowblade.

This release was about gradual improvements on features, correctness and stability. The new features in this release may not be useful to all users, but are very much needed by small subsets of users, and make the application useful for wider variety of editing needs.

The continued refactoring and improving of the code base has made it more clear that no major rewrites are needed, and Flowblade can be developed in a gradual and predictable way in the future.

## Installing Flowblade ##
See [Install Instructions](InstallInstructions.md).

### In this release ###
  * **Slip tool** allows changing the media displayed in a clip in a single edit action without changing the position and length of the clip
  * **Proxy editing workflow** can be used to edit material that makes the editing experience unacceptably unresponsive because the material places too high demands on the system
  * **Batch rendering application** makes it possible to render multiple programs in the background
  * **Dark Theme support** optimizes icons and GUI colours for dark themes
  * **Copy Pasting clips** on the timeline is now possible

#### Other features and enhancements ####
  * Watermarks
  * Rendering stopping bugs fixed, incl Motion Clip render bug
  * French and Czech translations
  * Playback frame positioning bug fixed
  * Icons and Tool cursors update
  * Simplify Tool names
  * Fix .mp4 files rendering bug
  * Fix wrong FPS value in File properties window
  * Change Theora rende file extension to .ogv
  * Fix Image Sequence import bug on some numbering styles
  * Remove gnomevfs dependency
  * Add indicator to timeline clip being edited in effects editor
  * Make all thread GUI updates acquire gtk lock
  * Fix SpinButtons value display bug
  * Make Titler layer visibility togglable
  * Make possible to turn off safe and overlay displays in Titler
  * Make Titler window resizable
  * Add entry box to give file extension when rendering with args
  * Improve SVG handling
  * Fix saving bug caused by MLT types SWIG names
  * Fix Redo keyboard shortcut bug
  * Fix Range Log comment editing bug


---

## Flowblade 0.10 ##
**Date: September 13, 2013**

**Flowblade 0.10** is the third release of Flowblade.

This release has a lot of new features and enhancements. The development cycle was longer than the planned 6 months, mainly because of the summer break and a cascade of interconnected changes that all needed to be completed before doing a release.

In future we will hold strictly to a maximum 6 months between releases, and will opt to postpone features in favour of a more reliable release schedule.

### In this release ###
  * **Tools** metaphor is used for editing instead of **Edit Modes** like before
  * **Audio Mixer** window with VU meter + gain and pan controls for all tracks and master out (**Requires MLT 0.8.8**)
  * **Affine Blend** compositor provides single point of control to create keyframed composites with both opacity and affine transform and all the standard blend modes (**Requires Frei0r 1.4**, which isn't widely in repos)
  * **Image sequences** of numbered frames can be imported now as media
  * **Preset rendering options** for commonly used file types are made available to the user
  * **Range Log** panel enables user to save and name Mark In/Out ranges on media files. This is very useful when working with long files that have many areas of interest.
  * **Marks** can now be placed to identify positions on the timeline.
  * **Single track rendered transitions** for quick dissolves and wipes
  * **Auto consolidate blanks**, no more multiple blanks between clips after some edits
  * **GUI Look'n'Feel** was updated with over 20 new icons and new custom buttons

#### Other features and enhancements ####
  * Updated application menu
  * Configurable Tabs position
  * Configurable Timecode display position
  * Keyboard shortcuts list window
  * "Centring" action for Compositor editors
  * TAB key switches between Timeline/Clip display on monitor
  * Keyboard shortcut CTRL+L for logging clip ranges
  * Arrow keys move source image in Compositor editors
  * Project events panel and persistent project events data
  * 8 video/1 audio and 1 video/8 audio track layoutsn for sequences
  * Media objects are now displayed using large thumbnails with information overlays
  * Noise and EBUBars image producers
  * Bin panel is now resizable
  * Colgate white balance plugin
  * Tracks menu
  * Support for Copy/Paste in Title Editor
  * Runtime environment data can be saved into a file
  * Rename and Clip Color features added to Clip context menus
  * Make cut action available when working with trim edit tools
  * Image Grid filter
  * Audio information for clip is displayed with level data instead of waveform
  * Panel sizes are now persistent
  * UP/DOWN arrows move position to In/Out Marks and clip ends on Clip Monitor display
  * HOME/END keys move position to timeline start/end
  * Sync Parent feature GUI update
  * Timeline focus fixes to make keyboard shortcuts available better
  * M keyboard shortcut for adding markers
  * Sync frame offsets visible
  * Display selected range on timeline frame widget
  * Display selected range length for Clips under monitor





---


## Flowblade 0.8 ##
**Date: December 4, 2012**

**Flowblade 0.8** is the second release of Flowblade, and the first one to take advantage of bug reports and feature requests from users.

Although a few important new features were added, much of the effort after **0.6** was spend creating new Frei0r plugins, total of 14 were contributed by the author, 10 of which are available in Flowblade **0.8**. Good new Fre0r plugins were contributed by other people too, so it may be worth while to install Frei0r from source code. See wiki: InstallingFrei0rPluginsFromSource.

### New Features ###

  * Titler
  * Slow/Fast motion clips
  * Flowblade now runs on screens with height of 768 pixels
  * Creating Sequences with different number of tracks is now possible
  * Ability to change Track count of Sequence
  * T, Y and U keyboard shortcuts for insert events
  * J, K, L keyboard playback control
  * Default length of Drag'N'Drop for graphics is configurable
  * 18 new filters added (latest Frei0r needed)
  * Environment information is made available to users

#### Major Bugfixes ####
  * Localisation bug causing non-working compositors fixed
  * Environment detection method changed to direct MLT for better results


---


## Flowblade 0.6 ##
**Date: May 7, 2012**

Initial release.

### Features ###
  * Film style insert/trim editing paradigm
  * 2 move modes and 2 trim modes
  * Image compositing with transformations, blend modes and pattern wipes
  * Close to 100 image and audio filters
  * Supports most common video and audio formats
  * JPEG, PNG, BMP, TGA, TIFF, GIF images and SVG vector graphics
  * Output encoding to multiple formats