
# EPW Recaster

![Overview](https://i.snipboard.io/NH7EZg.jpg)

## Download
**[ [ Latest & Older Versions ](https://github.com/KimDebroye/EPW-Recaster/releases) ]**

## In a nutshell
EPW Recaster is a tool that
- automates recasting EPW weapons & gears (_armors_)
- using Optical Character Recognition and
- user-configurable search conditions.
> *EPW Recaster does not rely on nor uses any kind of game hook.<br />It solely relies on what is captured using OCR and performs<br />programmatorical choices & actions based on captured results.*

## TL;DR QuickStart Video Demonstration/Guide

### Version 3
**`( WIP | TODO )`**

### Version 2
[![EPW Recaster ~ Demonstration Video](https://github.com/KimDebroye/EPW-Recaster/blob/master/GitHub%20Assets/YouTube%20Video%20Img%20Link.png)](https://youtu.be/iDBHqHXTZS8)

## Setup
- Extract the contents of the provided package<br />to any folder that has write privileges.<br />( *f.e.* `Desktop` | `C:\Apps\EPW Recaster` | ... )
- Launch `EPW Recaster(.exe)`.
	- **[ Developer Note ]**<br />This tool shouldn't require admin privileges by default.<br />However, if the OS configuration does require it<br />in order for the tool to run properly:
		- Right-click `EPW Recaster(.exe)`<br />and choose `Properties`.
		- In `Compatibility` tab,<br />check `☑ Run this program as an administrator`<br />and confirm by clicking `OK`.

<div>&nbsp;<br />&nbsp;</div>
<div style="page-break-after: always"></div>

## Sections

![Sections](https://i.snipboard.io/cZEa03.jpg)

### General Notes
- Once a preview or an auto-roll is started, the main form will be programmatically minimized and restored after.<br />( *The main form is mainly used for setup purposes only.* )
- On the other hand, the info form will always stay on top of all windows.
- All changes are automatically stored and restored upon relaunch.
- Using any kind of text editor, theming options can be altered in<br />  `.\Config\ThemeColorStyle.cfg` (*includes additional comments*).

<div>&nbsp;<br />&nbsp;</div>
<div style="page-break-after: always"></div>

### 1. ( Main ) Setup Form

___

#### 1-1. See-through Region
- When launching EPW Recaster for the first time
- ( *and/or whenever the in-game location of the recast<br />a.k.a. reshape/manufacture window is changed* ),
- **move the tool around and resize using the size grip handle**
- in order for:
	- the see-through region to fit the in-game recast<br />a.k.a. reshape/manufacture window,
	- the 3 tiny squares ( *hinting click regions* )<br />to be located somewhere over the in-game buttons<br />( `Retain the old attribute` |`Reproduce` | `Use the new attribute` ),
	- the capture region to fit the text to be captured.

> Additional Notes

- **The fitting does not need to be pixel perfect in order for the Optical Character Recognition to work properly.**
  - Depending on the fitting, parts of the in-game UI could be detected as a character<br />( *f.e. the in-game scroll up icon may be detected as capital 'A'* ).<br />This can (usually) be safely ignored.
- **[ ! ] Without any actual game file alterations,<br />it is strongly discouraged to use EPW Recaster<br />to look for stats on weapons that have unique (*long descriptive*) stats**,<br />unless it's (*one of those*) unique stats being sought after.
  - *In other words*, avoid looking for stats on weapons having<br />`Purify Spell`, `God of Frenzy`, `Square Formation`, `Soul Shatter`, `Spirit Blackhole`, ...<br />as a possible stat in order not to miss a stat needing an in-game scroll<br />(*unless the previously mentioned stats are being specifically targeted*).

___

#### 1-2. Capture Region
- ( *A visible preview of* )
- The region setting the boundaries used for Optical Character Recognition.
- Depending in which mode the process will be started, the capture region will either be located:
	- **Preview Mode : full width of see-through region** and a little above the in-game buttons.
	- **Roll Mode : right half of see-through region** and a little above the in-game buttons.

___

#### 1-3. Condition List
- A list containing previously added required roll conditions.
- **Used in order to programmatically stop rolling when one of the listed required conditions is met**.
- The condition list can have both _fixed amount stats_ and _combo stats_ entries mixed.
- The order of entries can be changed by dragging an entry over to another location in the condition list.

<div>&nbsp;<br />&nbsp;</div>

> #### 1-3-1. Fixed Amount Stats
- **Main difference with Combo Stats**:
  - Although **requiring a fixed amount** of a preferred single or grouped stat, rolled results<br />**can have stats that aren't a preferred single or grouped stat**.
- **Will accept if**
  - an exact amount or more of a preferred single stat or of each of the grouped stats is found.
- **Will reject**
  - if a stat has been detected that is not a grouped preferred stat
  - ( *with the exception of a unique stat if none have been added as a grouped preferred stat* ).
- **These condition list entries are**:
  - Recognizable by a blue stat color.
  - Always preceded by a fixed minimum amount of a preferred stat.
  - Can have up to 3 ( _grouped_ ) stat requirements per entry.
  - Mainly used for rolls:
    - having equal stats:
      - _`4 x Interval Between Hits`_
    - needing a certain amount of stats:
      - _`2 x Channelling` & `whatever else`_
      - _`2 x Interval Between Hits` & `hmmm it could use at least one of this stat` & `whatever else`_
      - _`2 x Interval Between Hits` & `hmmm it could use at least one of this stat as well` & `whatever else`_
      - ...
- **Pros**:
  - Precise in targeting what to roll for.
- **Contras**:
  - Requires thinking about adding stat and amount alternatives to the condition list in order<br />not to miss out on other/good/better/similar/exotic rolls.
- **Example**<br />![Example](https://i.snipboard.io/Sgdlwu.jpg)
  - ➥ **Example to be read as**:
    - Must have:
      - _at least_ `2 x Interval Between Hits` **OR**
      - _at least_ `4 x Reduce Physical Damage Taken` **OR**
      - _at least_ `2 x Interval Between Hits` **AND** _at least_ `2 x Critical Hit Rate` **OR**
      - _at least_ `1 x Interval Between Hits` **AND** _at least_ `1 x Critical Hit Rate` **AND** _at least_ `1 x Dexterity` **OR**
      - [ ... ]
  - ➥ **(Auto)Roll Result Examples**:
    - ✅ **Accept** ( _meets first and fourth condition, although would already be accepted at first_ ):
      - **`Interval Between Hits -0.05 seconds`**
      - **`Interval Between Hits -0.05 seconds`**
      - **`Critical Hit Rate +2%`**
      - **`Dexterity +10`**
    - ❌ **Reject** ( _fails any condition | missing `1 x Reduce Physical Damage Taken`_ ):
      - **`Interval Between Hits -0.05 seconds`**
      - **`Reduce Physical Damage Taken +2%`**
      - **`Critical Hit Rate +2%`**
      - **`Dexterity +10`**
    - ❌ **Reject** ( _fails any condition on either amount or a lacking stat_ ):
      - **`Interval Between Hits -0.05 seconds`**
      - **`Critical Hit Rate +2%`**
      - **`Critical Hit Rate +2%`**
      - **`Critical Hit Rate +2%`**
    - ✅ **Accept** ( _meets second condition_ ):
      - **`Reduce Physical Damage Taken +2%`**
      - **`Reduce Physical Damage Taken +2%`**
      - **`Reduce Physical Damage Taken +2%`**
      - **`Reduce Physical Damage Taken +2%`**
    - ❌ **Reject** ( _fails any condition | missing f.e. `2 x Reduce Magical Damage Taken`_ ):
      - **`Reduce Magical Damage Taken +2%`**
      - **`Reduce Magical Damage Taken +2%`**
      - **`Reduce Magical Damage Taken +2%`**
      - **`Reduce Magical Damage Taken +2%`**
    - ❌ **Reject** ( _fails any condition | missing f.e. `3 x Def. Level`_ ):
      - **`Def. Level +25`**
      - **`Def. Level +5`**
      - **`Def. Level +5`**
      - **`Def. Level +5`**
      - **`Def. Level +5`**

<div>&nbsp;<br />&nbsp;</div>

> #### 1-3-2. Combo Stats
- **Main difference with Fixed Amount Stats**:
- Although **not requiring a fixed amount** of a preferred single or grouped stat, rolled results<br />**can't have stats that aren't a preferred single or grouped stat** ( _exceptions being unique stats in certain conditions_ ).
- **Will accept if**
  - a combination of **ANY** amount of each of the preferred grouped stats only is found.
    - **Unique stats are considered wild cards**, unless added as a preferred grouped stat.
      - In other words:
        - If a unique stat hasn't been added to a combo entry,<br />a roll containing any unique stat combined with any amount of other grouped preferred stats<br />would be accepted.
        - If a unique stat has been added to a combo entry,<br />a roll containing any other unique stat combined with any amount of other grouped preferred stats<br />would not be accepted.
- **Will reject if**
  - a stat has been detected that is not a grouped preferred stat
  - ( *with the exception of a unique stat if none has been added as a grouped preferred stat* ).
- **These entries are**:
  - Recognizable by a golden stat color.
  - Are **not** preceded by a fixed minimum amount of a preferred stat.
  - Can have up to 3 ( _grouped_ ) stat requirements per entry.
  - Mainly used for rolls having exotic stats (_cfr. Fixed Ranked Gears_).
- **Pros**:
  - Flexible in targeting what to roll for without having to think about amounts.
- **Contras**:
  - Requires thinking about adding stat alternatives to the condition list in order<br />not to miss out on other/good/better/similar/exotic rolls.
- **Example**<br />![Example](https://i.snipboard.io/OhcZVf.jpg)
  - ➥ **Example to be read as**:
    - Must have:
      - _any combination of_ `Atk. Level` **AND** `Critical Hit Rate` **AND** `Interval Between Hits`<br />**AND** `any unique stat (GoF, SB, ...) as wild-card` **OR**
      - _any combination of_ `Reduce Physical Damage Taken` **AND** `Reduce Physical Damage Taken` **OR**
      - _any combination of_ `Interval Between Hits` **AND** `Critical Hit Rate` **OR**
      - [ ... ]
 - ➥ **(Auto)Roll Result Examples**:
    - ✅ **Accept** ( _meets first condition_ ):
      - **`God of Frenzy`**
      - **`Interval Between Hits -0.05 seconds`**
      - **`Critical Hit Rate +2%`**
      - **`Atk. Level +10`**
    - ✅ **Accept** ( _meets third condition_ ):
      - **`God of Frenzy`**
      - **`Interval Between Hits -0.05 seconds`**
      - **`Critical Hit Rate +2%`**
      - **`Critical Hit Rate +2%`**
    - ❌ **Reject** ( _fails any condition | missing `Interval Between Hits`_ ):
      - **`God of Frenzy`**
      - **`Critical Hit Rate +2%`**
      - **`Critical Hit Rate +2%`**
      - **`Critical Hit Rate +2%`**
    - ✅ **Accept** ( _meets second condition_ ):
      - **`Reduce Magic Damage Taken +2%`**
      - **`Reduce Physical Damage Taken +2%`**
      - **`Reduce Physical Damage Taken +2%`**
      - **`Reduce Physical Damage Taken +2%`**
    - ❌ **Reject** ( _fails any condition | missing `Reduce Magic Damage Taken`_ ):
      - **`Reduce Physical Damage Taken +2%`**
      - **`Reduce Physical Damage Taken +2%`**
      - **`Reduce Physical Damage Taken +2%`**
      - **`Reduce Physical Damage Taken +2%`**
    - ✅ **Accept** ( _meets second condition_ ):
      - **`Reduce Magic Damage Taken +2%`**
      - **`Reduce Magic Damage Taken +2%`**
      - **`Reduce Magic Damage Taken +2%`**
      - **`Reduce Physical Damage Taken +2%`**
    - ✅ **Accept**:
      - **`Reduce Magic Damage Taken +2%`**
      - **`Reduce Physical Damage Taken +2%`**
      - **`Reduce Magic Damage Taken +2%`**
      - **`Reduce Physical Damage Taken +2%`**

___

#### 1-4. Condition Entry (Entries)
- In order to enlist a roll condition:
  - Select a preferred amount and preferred stat to be found.
    - (Optional) Select up to 2 additional preferred amounts and preferred stats to be found/combined.
      - Once a second preferred stat has been selected from the drop-down list,<br />a checkbox to ignore amounts becomes available.<br />If checked, the entry would become a combo entry ( _allowing any amount of selected stats although limiting a roll to only contain the selected stats_ ).
  - Click the green `+` sign.
- Any previously added condition can be removed<br />by pressing the red `x` in the condition list.

> Additional Notes

- **Ignore white stats, only blue stats are to be taken into account**.<br />
  ( *f.e.* `4 x Phys. Res.` *= max, ignoring the fifth white Phys. Res. stat on a gear* ) 
- When (*accidentally*) adding an amount larger than 1 of a unique stat ( *f.e. `Purify Spell`* ),<br />it will instead be enlisted as `1 x`.
- When (*accidentally*) adding a summed amount exceeding the max stats possible,<br />it will instead be enlisted as either `4 x` or `5 x` ( _Atk. & Def. only_ ).
- Using any kind of text editor, the list of selectable stat options can be altered in<br />`.\Config\Stats.cfg` (*includes additional comments*).

<div>&nbsp;<br />&nbsp;</div>
<div style="page-break-after: always"></div>

### 2. Info Form

___

#### 2-1. Form (Un)Chainer
- **A toggle button attaching/detaching the info form to/from the main form.**
	- **Chained Mode** ( *attached forms mode | default at first launch* ) :
		- Only the main form will be movable and resizable.
		- Only the main form location and size will be stored and restored upon relaunch ( *due to the info form following its changes in location and/or size* ).
	- **Unchained Mode** ( *detached forms mode* )
		- Both main and info form will be separately movable and resizable.
		- Both form locations and sizes will be stored and restored upon relaunch.

___

#### 2-2. Log Folder
- **Clicking this button opens the log folder.**
  - For each roll, a resulting text and image file is logged.
  - **[ ! ] Occasionally empty/delete this folder<br />in order to free up storage space**.

___

#### 2-3. OCR Result Info
- Displays text captured together with some additional info when previewing or rolling.

___

#### 2-4. Preview | Roll Mode
- **Preview Mode** ( *default at first launch* ) :
	- Once started, will perform one single text capture.
	- No rolls will be performed in-game.
- **Roll Mode**
	- Once started, will perform a set number of in-game rolls,
		- obeying any previously set conditions &
		- resulting in a programmatically moving mouse cursor and mouse clicks.
	- Can be stopped at any given time by clicking the `Stop` button.
		- Using any kind of text editor, timings can be altered in<br />  `.\Config\Params.cfg` (*includes additional comments*).

<div>&nbsp;<br />&nbsp;</div>
<div style="page-break-after: always"></div>

___

## FAQ

> **Question: "The tool doesn't seem to work for me ... what do I do, doc ?**"<br />
> **Symptoms**: "_No valid roll information detected (yet)._" | "_... doesn't seem necessary to roll any further ... halted ..._" | "_Threw my pc out of the window..._" | ...

➥ **Answer**:
- **In general, each capture/roll produces a logged text and image file that may be worth checking in case it would be an OCR related issue.**<br />Check [ 2.2. Log Folder ](https://github.com/KimDebroye/EPW-Recaster#2-2-log-folder) for more information.
- **It doesn't click/reproduce a roll.**
  - **It's most certainly an admin privilege issue.**<br />Check [ Setup > Developer Note ](https://github.com/KimDebroye/EPW-Recaster#setup) for instructions on how to enable administrative privileges.
    - **[ Developer Note ]** This fixed it for most I've been chatting with that had this issue.<br />If many encounter this, I may include code in an update<br />to elevate administrative privileges programmatically ( _hoping it would skip the manual fix_ ).
  - **Additionally, make sure the capture region has been sized/positioned correctly.**
- **It does click/reproduce a roll but still stops a batch roll after a short while.**
  - **May as well be a timing issue.** On older or _trying-to-avoid-what-fries-and-chips-are-made-of-word_ computers,<br />maybe best to also increase timings ( _add about 500~xxxx milliseconds to timings of choice_ ).<br />Check [ 2-4. Preview | Roll Mode ](https://github.com/KimDebroye/EPW-Recaster#setup) for the config file location.
  - Also, keep in mind that ( _at time of writing_ ) older re-rollable gears ( _Primal / Nirvana / ..._ )<br />don't produce in-game roll results as fast as R8 ones,<br />so also for this purpose it would be best to increase timings.<br />If needed, change the `Await Accept/Reject Action` timing to around 3750 milliseconds.
- **Inform me when the above does not provide a solution to the issue.**

> **Question: "Am I able to contact you in any way ?**"

➥ **Answer**:
- **Sure.** Check below for ways to get in touch with me.

___

## Contact | Feedback

- Post a message in the [ EPW Tool Release Info Thread ](https://epicpw.com/index.php?topic=68651.0).
- Feel free to post-message me in-game | on Discord.
