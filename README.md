# tWriter: A Textile Bundle for Prose

The tWriter bundle is an extended [Textile language](https://github.com/textile) bundle for [TextMate 2](https://macromates.com/). It is meant for people who want a better experience with Textile when writing and editing prose for web publication. Users of [Textpattern CMS](https://textpattern.com) will especially find it beneficial. The overall aesthetic is modelled after the usability of [iA Writer](https://ia.net/writer). To that end, tWriter comes with its own light and dark themes, modelled after the greyscale-like iA Writer experience.

A few examples of the visual effect for various uses of Textile follow below. (You can find more in the [closed issues](https://github.com/wion/tWriter.tmbundle/issues?q=is%3Aissue+is%3Aclosed) for grammar scopes as they are changed or added.)

Some basic formatting, and note the consistent grey out handling of Textpattern syntax (regular HTML is treated the same way). No rainbows needed when all you are trying to do is write prose.

![tWriter basic formatting](https://wion.com/assets/images/temp/tWriter-format.png)

And links are finally like iA Writer links; the Textile syntax is present but standing back from regular text, like a *humane* syntax should do. Dark theme here…

![iA Writer-like Textile links](https://wion.com/assets/images/temp/tWriter-links-dark.png)

And some of the new syntax here showing displayed and embedded quotations and code. Note the smaller size on displayed quotations…

![tWriter quotes and code](https://wion.com/assets/images/temp/tWriter-quotes-code.png)

And the endnotes handling, which also reduces size on the notes…

![tWriter endnotes](https://wion.com/assets/images/temp/tWriter-notes-dark.png)

## Differences from the Standard Textile Bundle

The Textile grammar in the tWriter bundle is modified from, and extended beyond, what the standard Textile bundle for TextMate provides. As depicted above, it accounts for more of the contemporary Textile syntax used in [php Textile](https://github.com/textile/php-textile), which is supported natively in Textpattern. That Textile includes syntax for block quotes, endnotes (advanced footnotes), and (eventually) more complex table structures. Other changes here and there, too.

The tWriter bundle also *excludes* many of the basic menu actions in the standard Textile bundle, deemed pointless for experienced Textile users. New actions for the more advanced Textile syntax may be added eventually.

## Installation

Since this is an extended bundle for a language already available within TextMate by default (the standard bundles), you might want to deactivate, uncheck, turn off the standard Textile bundle via the Bundles index at **TextMate > Preferences > Bundles > [Languages]**. This ensures you do not have duplicate Textile bundles in your application lists confusing you needlessly.

Then, whether sourced from a .zip package or cloned from a repository,  the tWriter bundle should be added to the /Bundles directory at:

```
~/Library/Application\ Support/TextMate/Bundles
``` 

## Setup

The bundle and themes by themselves do not (and cannot by TextMate design) provide the full iA Writer experience. You need to nudge it a little further by doing the following.

### Install the iA Writer Fonts

Using the iA Writer fonts, [Mono, Duo, and Quattro](https://ia.net/writer/blog/a-typographic-christmas), is a critical part of recreating the iA Writer experience through tWriter. The fonts are made available from the [iA-Fonts](https://github.com/iaolo/iA-Fonts) repository, but the specific .ttf files for application use are conveniently included in the bundle at `tWriter.tmbundle/Support/Fonts/iAWriter.zip`. The font license sits next to the .zip file.

Put all twelve .ttf files into `~/Library/Fonts`. The quickest way to do that, perhaps, is copy and run the following five commands in series:

1. `cd ~/Library/Application\ Support/TextMate/Bundles/tWriter.tmbundle/Support/Fonts`
2. `mv iAWriter-fonts.zip ~/Library/Fonts`
3. `cd ~/Library/Fonts`
3. `unzip iAWriter-fonts.zip`
4. `rm -R iAWriter-fonts.zip`

Duo is the base editing font. Mono is for displayed and embedded code examples. Quattro, a typewriter-like font with proportional qualities, will be used in a modified Preview window for the bundle, but that is still to come. You might as well have the font installed and ready. 

### Configure the View

Make the following configurations via the View menu of TextMate:

1. View > **Enable Soft Wrap**
2. View > Wrap Column > **Use Window Frame**
3. View > **Hide Line Numbers** (optional)

That last one is subjective. You won't find line numbers in iA Writer, nor any distracting gutter at all. A gutter remains in TextMate, however, even if line numbers or hidden.

There is no need to mess with font settings under View > Font > Show Fonts. But, if you look in font settings, you will see that the ’iA Writer Duo S' font is selected at size 18 (point). It is reading what is defined in the themes. You could override that by changing font settings, but that defeats the point of the tWriter bundle.

### Set Interlinear Spacing

Interlinear spacing is effectively line height, though established a little differently in client applications than web documents. In iA Writer interlinear spacing is a function of line length, set as characters per line.

In TextMate there is no interlinear spacing (appealing to coders, presumably), which is the same as saying a line heigh of 1. But TextMate's developer was kind enough to provide two [hidden keys](https://github.com/textmate/textmate/wiki/Hidden-Settings), `fontLeadingDelta` and `fontAscentDelta`, for replicating line height. The former controls space above a line, while the latter controls space below a line.

The `defaults` shell application is used to set or change values for these keys; specifically, the `write` or `delete` commands will be used in relation to the application's `com.macromates.TextMate` domain. The values must be set as either floating point numbers (i.e. decimal numbers: 1.3, 1.5, 1.7...) or as integers (i.e. whole numbers: 1, 2, 3...), and for that the `-float` and `-integer` properties are used, respectively (e.g. `-float 1.5`, or `-integer 3`).

I found that a floating point value of `3.7` for both keys establishes iA Writer's interlinear spacing perfectly on my 13-inch laptop when characters per line in iA Writer is set at 72.

So, if you are inclined to edit the interlinear spacing for a better fit with the iA Writer aesthetic, **first quit TextMate**, then copy, paste, and run the following chained `write` commands:

```
defaults write com.macromates.TextMate fontLeadingDelta -float 3.7 && defaults write com.macromates.TextMate fontAscentDelta -float 3.7
```

Open TextMate again to find the interlinear spacing looking a lot more like that in iA Writer.

You can delete the *leading* and *ascent* values and return to a default state by **quitting TextMate again**, then running the following for @delete@:

```
defaults delete com.macromates.TextMate fontLeadingDelta && defaults delete com.macromates.TextMate fontAscentDelta
```

And if you ever forget what you might have set, or not, you can run the following `read` commands, respectively, without having to quit TextMate first (since you are not changing any values here):

```
defaults read com.macromates.TextMate fontLeadingDelta
```

```
defaults read com.macromates.TextMate fontAscentDelta
```

### Establish Desired Line Length

Line length in iA Writer by default is a nice 12 to 15 words per line when characters per line is set at 72, so that is the initial target here.
 
There are two ways to get that usable line length in TextMate. The easy and recommended way (what the author uses) is to drag the window to a width of about 12 to 15 words per line on average. You’ll find there is still a little scrolling in the stage even though the soft wrap is set to wrap at window frame. This is a TextMate bug, apparently, but the scrolling is minor and you get used to it fast.

The other way is to expand the window full screen, and change the soft wrapping from the window frame to a column width value of 72. There is no horizontal scrolling this way, but text in the resulting display is shifted left in the expanded window, which is not an iA Writer experience by any means. There is also another bug (or a different manifestation of the same bug) when going back to a non-expanded window width and wrapping at the window frame again. The stage retains the memory of the column width in the expanded distance and makes the scrolling problem a lot worse. The compounded scrolling can be eliminated by starting a new document tab (which puts you in it automatically), then clicking back to the draft again. The compounded scrolling will magically disappear.

## License

This bundle maintains the license of the [standard TextMate bundle for Textile](https://github.com/textmate/textile.tmbundle), as follows…

If not otherwise specified (see at bottom), files in this repository fall under the following license:

	Permission to copy, use, modify, sell and distribute this
	software is granted. This software is provided "as is" without
	express or implied warranty, and with no claim as to its
	suitability for any purpose.

An exception is made for files in readable text which contain their own license information, or files where an accompanying file exists (in the same directory) with a “-license” suffix added to the base-name name of the original file, and an extension of .txt. For example, the iA Writer fonts are accompanied by ‘iAWriter-fonts-license.txt”.