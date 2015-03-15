...work in progress

**Table of Contents**


# Non-linear editing and Flowblade #

> This wiki text will first analyse definitions and existing solutions in the field of non-linear editing and then it will take a look at how to improve the editing model of Flowblade.

## 1. Defining non-linear editing ##
> Wikipedia defines non-linear editing as **'a system that performs non-destructive editing on source material'**.

> From the point of view of a PC video editing this definition is not interesting; all PC video editing applications satisfy this requirement. Source clips are stored unchanged on hard disk and edits are expressed as in and out point and clip order data.

> For the purpose of discussing PC video editing applications I will use a different definition here:

> A **non-linear video editing system** is a system that allows the editor to **edit the program at any point** of the program and to **perform the edit in constant time**.

> In a **linear editing system** the amount of **work required** by the editor to perform an edit **increases linearly the further back the edit point is** from the end of the program.

## 2. Non-linear edit actions ##
> Let's look at the different classes of edit operations and see how these operations can be performed in constant time.


### Seek and playback ###

> All hard disk based video editing systems perform this operation in constant time trivially, hard disk seek times are constant to a degree required here. No non-computer editing system is able to do this in constant time.

### Clip sequence editing ###

> This is important as a separate class of edit actions as it is the first phase in almost all editing work flows: clips are placed one after another on timeline and edited into a rough cut with only straight cuts.

> This is not the same as single track editing, as quite often this needs to done using two tracks alternating clips with spaces between the clips.

> Video editing applications generally use two different edit models to be able do these type of edits in constant time.


_**Edit Model 1: Free Move/Multi Selection**_

> In this edit model moving or trimming clips have no effect on clips on the track after it. Clips are placed on two tracks so that every other clip is on different track.

> Edits are performed in two stages. **First a clip is stretched or moved to alter edit point** between two clips on different tracks. After that you often **need to move all items after edit point** to restore the next edit in sequence.

**Pros:**
  * It is possible to do all edits in constant time with this approach
  * Work flow is the same for single and multi track editing

**Cons:**
  * Constant amount of work required for each edit is rather big
  * Fixing the next edit after the one worked on easily results in altered program
  * Having to think of edits in terms of top and bottom tracks is not very intuitive
  * Patterns of alternating clips often mismatch when sections of sequence are either deleted or moved
  * Moving clip sequences is difficult and requires work before and after moving the clip sequence
  * It is easy to leave a single empty black frames between clips
  * Positioning clips accurately even with 'magnet' assistance is not comfortable over long periods

> In general this approach works best when editing short programs (about 30s - 4min) with complex compositing (see discussion below). Music videos are another use case well suited for this edit model because image/audio sync is easily retained and the length of a music video is quite short.

> Long documentaries are not a good match for this edit model because of the required high constant for moving clips and sequences around.

> With Flowblade it is possible to edit in this way by using only Overwrite and Roll tools.


_**Edit Model 2: Insert/Trim**_

> This is the preferred method in Flowblade and all the major commercial applications for clip sequence editing.

> In this model the clips are placed after each other on a single track and cuts are fine tuned by trimming individual clips. Clips are "glued" to each other so as clips are lengthened or shortened all other clips on the track move accordingly. Clips and sequences are moved by splicing them out anremoving the resulting gap and then inserting back in between two other clips.

**Pros:**
  * This is both faster and more reliable than free move editing - as long as no multitrack compositions are attempted.

**Cons:**
  * When doing multitrack editing workflow becomes different and more complex

### Multitrack composition editing ###

> Almost all practical editing in modern systems happens in this context to some degree.

> The main problem with non-linear multitrack editing with video/audio compositions is that editing the program may cause multitrack compositions later in the program to break and thus necessitate a linear amount work to repair those compositions.

> There are several ways to achieve constant required work while editing a program with multitrack compositions.


_**Edit Model 1: Free Move /  Multi Selection**_

> Clips are moved and trimmed independently or in selected groups.

**Pros:**

  * Edit operations do not cause any compositions to break later in the program.
  * Multitrack composition editing does not differ much from clip sequence editing

**Cons:**
  * Moving edited multitrack compositions around can very difficult. Complex selections may need to be made, usually with unions of multiple box selections.
  * Creating space for sequences to be moved into often need to be made before sequence is moved
  * Two corrections may need to be applied to remove empty space after a multi track composition is moved.

_**Edit Model 2: Modular with locked offsets**_

> This is the method used by Final Cut X. It has a single special track called 'Spline'. On 'Spline' clips are trimmed and moved like when editing single clip sequence with Insert/Trim paradigm. Multitrack constant edits are achieved by having all the timeline items not on 'Spline' track attached to some 'Spline' clip with a locked offset. A single sequence of modules with possibly multiple media items in each is created in this way

**Pros**
  * Work flow for editing with or without compositions is almost the same

**Cons:**
  * Since multiple items can be attached to single 'Spline' item the resulting object can become quite complex and difficult to further edit.
  * Moving clips and sequences may result in complex automatic conflict resolution between objects with arbitrary dimensions across multiple tracks.
  * Application code will be quite complex compared to other edit models

_**Edit Model 3: Ripple editing**_

> Different versions of this are used by Premiere, Avid and pre-X Final Cut.

> In this edit model a change made at edit point "ripples" down the timeline on all tracks. Usually the spaces between clips are lengthened or shortened to maintain clips on different tracks on same positions in relation to each other.

**Pros**
  * This is faster and more reliable than using free move editing
  * User can still edit in free move style when appropriate
  * Resulting application code is relatively simple

**Cons:**
  * This requires the editor to constantly switch between ripple and non-ripple versions of the same edit
  * Resulting UI is not clearly defined by the model as evidenced by the fact that applications employing this model differ significantly from each other
  * Editors often fail to use ripple and non-ripple edits when appropriate and lose the desired positions between clips on multiple track and need to do work to restore compositions. The amount of this work **has to be constant** or the editor fails to be non.linear as defined in this text.


## 3. Flowblade editing model ##
### Current State ###
> The current Flowblade editing model can shortly be described by the following attributes:
    * Timeline consists of video and audio tracks.
    * Video tracks also play back audio on clips placed on them, audio tracks only playback audio even if the media clip has video
    * Clips do not have corresponding locked audio clips on audio tracks. Audio may be extracted as a separate clip. This audio is not locked but can bu sync marked.
    * For clip sequence editing Flowblade prefers Insert/Trim edit model which can be executed using Insert and Trim tool
    * Inserts and trims only ripple along the track thay are used
    * It is possible to edit with free move / Multi Select model by using Overwrite  and roll tools
    * Selections can only be made on clips on the same track. Any number of selected clips can be moved and inserted / used to overwrite track range
    * Compositing is achieved by placing compositors on the timeline. They apper just below the Source track and Destination track is displayed using a arrow coming out of the compositor
    * Compositors are free flowing and are not locked to clips used to create them but retain relationship with them and can be resynched with origin clips by request
    * Trim / Insert / Delete operation will lose
    * With Flowblade audio data is explicitly extracted from clip to another track and is not locked to image clip. This makes J- and L-cuts essentially multitrack compositions.
    * Tools are not context aware

### Conclusions ###
  * Current edit model does not support non-linear multitrack composition editing as defined in this text
  * Although free move editing can be done, it cannot be done non-linearly because of multi select cannot be done


### Steps to improve Flowblade edit model ###

**Multitrack non-linear editing**

> Current model of setting non-locking sync relations is sufficient for short programs with a llot of compositioning or long programs with small amout of compositioning, but is probably not the optimal solution.

> It was originally decided upon because the alternatives all have their drawbacks too: Free move / Multi select is overall slower, Modular with locked offsets is very difficult to implement and not generally like and Ripple editing causes mental overhead is quite error prone.

> However, it seems that the already existing sync relations functionality will work nicely with Ripple editing and enhance it. If the user loses a previously created composition because of uncorret Ripple editing, then it can be restored using resync functionality.

Solution: **Implement full ripple editing workflow**

**No multiselect available**
> The choice here is between box selection and or something like Premier Track Selection tool. Flowblade already strongly defines selection as single track functionality done by selecting first and last clips of range so this must not be changed.

Solution: **Implement Multitrack Selection tool**
