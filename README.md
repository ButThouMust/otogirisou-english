![title screen](images/01%20title%20screen.png)   ![sample gameplay](images/04%20normal%20text.png)

![file select](images/02%20file%20select.png)    ![name entry](images/03%20name%20entry.png)

# otogirisou-english

Update April 2, 2025: I have been going through the script again and preparing for another patch release. It will be released when it is ready, but I would give a rough estimate of mid April to early May at the latest.

Patches for an English translation of Otogirisou for Super Famicom. Although I would prefer the whole script translation to be peer-reviewed, I consider it good enough to have my tools and such available for download.

All my source code, tools, reverse engineering notes, etc. are available in [this repository](https://github.com/ButThouMust/otogirisou-tools), which is also included as a submodule here.

**Please let me know** if you would like to contribute to the translation, or would like to use this project as a basis for translating the game to another language! (related [RHDN forum post](https://www.romhacking.net/forum/index.php?topic=38663.0))

**Patch files from here are _not_ to be reuploaded to other sites without my permission.** In other words, just ask if you want to upload them somewhere.

This is a translation project independent of the one by Tom (RetroTranslator) and DDS, for which they released a patch on March 6, 2024.
- This is not to dismiss the quality of their project, but please do not send me suggestions for my project based on theirs (e.g. "they did X, you did Y, you should change Y to be more like X").
- That two separate translation projects exist for the game, I chalk up to unfortunate timing.

# How to patch
Go to the [releases page](https://github.com/ButThouMust/otogirisou-english/releases) to download the most recent patch version. You will need a *legally obtained*, unheadered 1 MB ROM image of the game, which has this specification in the [No-Intro database](https://datomatic.no-intro.org/index.php?page=show_record&s=49&n=1880):
```
CRC32:   8e4befd0
MD5:     ae1e9c92d0b7e6dba6c6007d99c9c3f4
SHA-1:   2c27b89a244abe941b6a9fceb1a674dbefd1f734
SHA-256: d85b6764a35f4dcee3ab5843df1c467ebdfe5f02236043a4e466e6975a3f70ca
```

Two patches are included: one for honorifics on, and one for honorifics off (more details about this below). Use whichever patch you prefer, with any patching utility that supports the BPS format. It should produce a 1.5 MB file. I personally used the utility [Floating IPS](https://www.romhacking.net/utilities/1040/) to generate the patch.

# How to play the game
Otogirisou is a single player sound novel game from Chunsoft (now Spike Chunsoft). It was both their debut title as a game publisher, in 1992, and the first entry in their sound novel series (Kamaitachi no Yoru, Machi, Imabikisou, and 428 Shibuya Scramble).

The controls are fairly simple:
- A/L: Confirm menu selection, advance text
- B: Cancel menu selection, advance text
- X: Scroll a page of text back, if available
- Y: Scroll a page of text forward, if you have already scrolled back at least one page
- R: Unused
- Start: Only used on the title screen (advance to menus) and name entry screen (confirm entered name).
- Select: Only used in the name entry menu. It brings you from the grid to the page selector, while preserving your grid position.

You must first name the protagonist (up to 6 characters). His default name is Kouhei (公平) in the PlayStation remake, but he has no default name in the Super Famicom version. The basic plot is that Kouhei and his girlfriend Nami (奈美) are driving home from a date, when circumstances force them to take shelter from a rainstorm in a creepy mansion. It soon becomes apparent that some kind of presence inside clearly doesn't want them there.

The gameplay, so to speak, consists of reading text and picking a choice from a list when the game presents you with a branching path. This continues until you reach one of several available endings. The game will automatically save your progress whenever you finish a screen of text or reach the credits.

Otogirisou's replayability comes from the different paths you can take, and the different endings you can view. Depending on which and how many unique endings you have seen, the game may present you with new options to pick for choices. For example, a choice you first found with two options may later give you three or even four options. Try to find as many endings as you can, and the game may reward you!

> [!WARNING]
> If you would like to carry over your save file to the next version, you must:
> - [Optional] Finish your playthrough first in whatever version you currently have.
> - Load your save file in the new version, and choose the options `Start` -> `Restart`. This ensures the game is reading text from the proper position in the ROM.
>   - To avoid losing data, I suggest that you have both the older patched game and the newer patched game. Let's say they are `patch_v1.sfc` and `patch_v2.sfc`.
>   - *Make a copy* of your .srm file from, say, `patch_v1.srm` to `patch_v2.srm`.
>   - When you know for sure that your save data has carried over, you can delete the ROM and save data for the old version of the patch.

# Features added for patch
- A more aesthetically pleasing English font than what was originally in the game.
  - Bypassing of the original game's font compression, to more easily add/edit characters if needed.
  - Linebreaking logic that, while imperfect, is better suited for English text and cuts out lots of manual formatting.
  - [Text kerning](https://en.wikipedia.org/wiki/Kerning), both horizontally and vertically.
  - Up to 10 lines of text can be on screen at once, instead of 9 like in the original Japanese game.
- Translation of all important graphics that contain Japanese text.
  - Title screen, credits, menu text, and one certain graphic in the story.
  - There are a few graphics where their Japanese text was left alone because the novel text explains them fine.
- Restoration of some unused content in the game.
  - Translated and restored two screens of text, plus another line, that were unused/inaccessible in the original Japanese script.
  - Made an unused graphic in the game viewable, after I discovered it in the game's data.
- Option to let the player enable or disable honorifics.
  - Normally, I would have left them out altogether, but there is an interesting argument for keeping them in. 
  - The original Japanese game has what you can technically consider a "game mechanic," where Nami uses a different honorific for Kouhei on each playthrough. For example, she may start with san but can switch to kun, chan, etc.
  - In the spirit of the sound novel, I leave this decision up to you, the player! :)

# Submitting issues
For general suggestions or any issues like bad formatting of game text, please contact me *with a screenshot* of where you found the issue. You can create an issue here, reply to the [RHDN forum post](https://www.romhacking.net/forum/index.php?topic=38663.0) I made for this project, or join the [RHDI Discord](https://discord.gg/uAufcgz) and contact me there.

Issues in order from most severe to least concern (current priorities in *italics*; list will be added to as needed):
- Game crash or softlock
- Save file deleted
- Irregularities in game behavior (please specify)
- *Translation errors and/or poor wording*
- *Too many lines of text that overflow past the bottom of the screen*
- *Text doesn't auto line break early enough, with a word overflowing past the right edge of the screen*
- Text auto line breaks too early, when a word can fit in space after break
- Control code mnemonics that slip through as visible text in the script
  - For example, seeing a literal `<LINE 00>` instead of seeing a line break
  - Similar, script comments that begin with `//` that sneak into the game script
- Automatic "wait for player input" triggers too often on punctuation
- Text kerning pairs that should have kerning but don't, or vice versa

# Known issues
- Due to how kerning is currently implemented, the one place it does *not* occur is the protagonist's name.
- I have not thoroughly tested the automatic line breaking while accounting for how you can name the protagonist `I`, `WWWWWW`, or something in between.

# Potential improvements
- Make a more user-friendly option to enable or disable honorifics.
  - Currently, this works by having two different patches. So if you want to switch, you would have to keep two copies of the game (one with honorifics on, another with honorifics off), and rename your save data accordingly.
  - One solution I had brainstormed was implementing the option through the otherwise unused R button.
- Change the kerning implementation to allow for kerning in the player's name.
- Make the automatic linebreaking logic more robust.

# Project credits
Alphabetical list of people who have contributed to this project, directly or indirectly, at some point:
- ["Guest"](https://www.romhacking.net/community/695/): Creator of [original tools (script/font dumpers)](https://web.archive.org/web/20211006124117/https://www.romhacking.net/abandoned/569928.zip) and notes in [abandoned project](https://web.archive.org/web/20220115061924/https://www.romhacking.net/abandoned/) "starter pack" on RHDN
- Karu: Translation assistance
- [Koitsu](https://www.romhacking.net/community/394/): Provided [notes](https://drive.google.com/drive/folders/1PGe1NSHxB6LXuLZH3t8acn7CnwjRYQYr) on the game's font compression format and its VWF implementation
- [Lazermutt4](https://www.romhacking.net/community/7126/): Translated the title logo and a certain graphic in the game; pointed me to the font that I would use for the end credits
- MLagaffe: Provided font for main text; suggested ideas for assembly hacks related to in-game text formatting
- [Squeaky](https://www.romhacking.net/community/8301/): Translation assistance

I would also like to mention the [Open Source Cartridge Reader](https://github.com/sanni/cartreader) project. Building one allowed me to test the translation patch on a real Super Nintendo with an [SF Memory cartridge](https://en.wikipedia.org/wiki/Nintendo_Power_(cartridge)).
