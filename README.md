# tWriter for Textile Authors

The tWriter bundle is an extended [Textile language](https://github.com/textile) bundle for [TextMate 2](https://macromates.com/). It is specifically meant for people who use [Textpattern CMS](https://textpattern.com) for personal web publishing, love the usability of [iA Writer](https://ia.net/writer) as a simple prose development application, but prefer Textile over Markdown. To that end, tWriter comes with its own monochrome themes, light and dark, modelled after the iA Writer experience.

The Textile grammar is extended beyond what the standard Textile bundle for TextMate provides; it accounts for more of the contemporary Textile syntax used in [php Textile](https://github.com/textile/php-textile), which is supported natively in Textpattern. Such syntax accounts for content features like block quotes, endnotes (advanced footnotes), and more complex table structures. The grammar also pulls out a few embedded wrapping pairs that were handled a little too generically in the standard version; whether or not an author may really need them, they are now more visually recognizable.

The tWriter bundle also changes many of the menu actions that come in the standard Textile bundle; removing those for basic Textile and (eventually) adding some new ones for the more advanced elements.

Finally, the themes include scopes for [Textpattern’s own tag language](https://github.com/wion/textpattern.tmbundle), txp, so that draft articles destined for Textpattern CMS can include such markup and have it treated visually with the same monochrome colour as Textile; that is, full separation of all language syntax from text prose.

# Work in Progress

The author is not a developer, not even close, and [TextMate documentation](https://github.com/textmate/textmate/wiki) is deplorable for such a state of mind. So Issues will be created for things the author would like to do but does not know how, or can't figure out after too much time trying. Anyone with insights to solving those issues is more than welcome to chime in.

The author does not expect this to be a perpetual work-in-progress, though, so once it gets to the point of _good enough for the author’s liking_, which is not far away, that will probably be it. Also, progress will be slow, probably.

This section of the ReadMe will disappear when the bundle has reached the author’s _good enough_ point.

# Installation

Since this is an extended bundle for a language already provided in TextMate by default, you might want to deactivate, uncheck, turn off the standard Textile bundle in TextMate via the Bundles index at **TextMate > Preferences > Bundles > [Languages]**. This ensures you do not have duplicate Textile bundles in your application lists confusing you needlessly.

The tWriter bundle should be added to the /Bundles directory at:

```
~/Library/Application\ Support/TextMate/Bundles
```

Done.

Open TextMate and find ’tWriter’ available under the Bundles menu and in the bundles editor list. It will appear as ‘Textile’ in the language selector options at bottom of window chrome because the grammar file is still named ‘Textile’. If you prefer seeing ‘Textile’ consistently throughout, edit the name in the info.plist file. 

# The iA Writer Experience

When using tWriter, it is sensible to deactivate the Themes bundle at **TextMate > Preferences > Bundles > [Themes]**. This will leave only the 'tWriter Light' and 'tWriter Dark' themes in the themes options at **View > Themes > [theme]**. Again, the tWriter bundle was designed for these themes, so eliminating the unusable standard options from the menu is practical. Or, you can always customize a theme against tWriter’s grammar.

The tWriter themes will not give you the full iA Writer experience by themselves. You should also do the following if you want to go further with it.

## Stage Configuration

First, download and install on your machine the [iA Writer Duospace](https://www.fontsquirrel.com/fonts/ia-writer-duospace) family.

Then, when working on a .textile document, make the following configurations via the View menu:

1. **View > Font > Show Fonts**...
   * Collecton: Fixed Width
   * Family: iA Writer Duospace
   * Typeface: Regular
   * Size: 18
2. **View > Enable Soft Wrap**
3. **View > Wrap Column > Use Window Frame**

Combined with one of the tWriter themes, the above configuration is a pretty good approximation of the iA Writer aesthetic under the constraints of TextMate, with the exception of one real problem: controlling a usable, readable line length in relation to text.

## Line Length Problem

The iA Writer application was designed with reading and text comprehension in mind, therefore making it an ideal application for developing prose instead of code. To see this, one needs to consider some of the many usability studies over the past three decades on reading/comprehension in digital screens. Paul Olyslager offers a good [summation of the main text factors influencing reading comprehension](https://www.paulolyslager.com/optimal-text-layout-line-length/), which are line length, font size, characters per line, letter spacing, and interlinear spacing (i.e. line height).

In web design, the above text usability factors are easily dealt with by picking a sensible font and controlling layout and behaviour via CSS, whether or not most designers or site owners make the effort. For example, it is possible to create a font-size to line-length ratio in desktop conditions that stays the same no matter what width a user drags their browser window to, or to set a max width on line length so font size does not get comically large. This may not be possible in client applications (don't know), but iA Writer somewhat handles it by using margins in the window stage, ensuring a max width on line lengths no matter how wide the application window is expanded, and allows font sizing adjustments *indirectly* by way of changing the number of characters per line only. Otherwise, font characteristics and line height are not editable; they are part of the editor’s design according to sensible usability; there's no direct, needless manipulation of them.

<<<<<<< Updated upstream
Likewise, the one [hidden setting](https://github.com/textmate/textmate/wiki/Hidden-Settings) to control line height, `fontAscentDelta`, does not seem to work for this author. Try it yourself and see if you have better luck...

Close TextMate, then run the following command ('1.5' is the line height value, use the value you want; 1.3, 1.7, 2, whatever):
=======
TextMate, on the other hand, is quite different. There is no optimal font size, line height, or specific font family fixed in place. That's understandable for the type of editor it is, a code editor, and who it is for, coders. But the one manner in which it does allow control over line length—by way of the wrap column and soft wrap controls—is either terribly confusing or very buggy, its hard to know which. And here is why...

You may notice after making the above recommended configurations in TextMate for this bundle's themes that even though you have set a soft wrap at width of window, there is still some horizontal scrolling inside the stage due to text moving past the right side of the stage. If you drag the application window to about 80% of your screen width (e.g. on 13-inch laptop screen), the scrolling is reduced to a manageable level, but the stage still jumps around as you type and reach ends of lines, and that is annoying. The only way for the scrolling to go away is to expand the window full screen, but then line lengths are ridiculously long because there is no way to control text margins.

If anyone knows why this scrolling happens under these conditions, or knows how to set margins in the stage, please chime in.  

## Line Height

Line height in TextMate can supposedly be set by way of a [hidden setting](https://github.com/textmate/textmate/wiki/Hidden-Settings), `fontAscentDelta`. But it does not seem to work for this author. Try it yourself and see if you have better luck.

You are recommended to first close TextMate. Then run the following command, where `1.5` is the line height value, though you can use whatever value you want (`1.3`, `1.7`, `2`, etc.):
>>>>>>> Stashed changes

```
defaults write com.macromates.TextMate fontAscentDelta 1.5
```

Open TextMate again.

That will supposedly apply a line height in TextMate for the value you set. You can verify what line height might be set by running:

```
 defaults read com.macromates.TextMate fontAscentDelta
```

Or delete a set value by running:

```
defaults delete com.macromates.TextMate fontAscentDelta
```

Even if you do not succeed in setting a slightly taller line height, as appears in iA Writer, the themes and View configurations still look pretty close, barring the line length problem mentioned previously.

# Muse: Application Level Customization

Although not the goal here, the idea of converting TextMate to a veritable iA Writer for Textile, by way of TextMate’s unique and flexible bundles, does make for curious reflection. 

Olyslager, mentioned earlier, also points out that text layout is another factor influencing reading comprehension, though more so in web and print media design, where other content elements and bullshit advertising might mix in.

In the case of text editors, this is not a problem, though we could consider differences in chrome design, and TextMate might score *busier* in that case due to features like the left-side gutter (for line numbers) and tabbed panes (when used), but these are not impacts on reading and comprehension in the stage.

Nevertheless, could they be changed, if wanted? If one were so inclined to try customizing TextMate into a veritable mimic of iA Writer but for Textile instead of Markdown, could the following be done:

* Restructure the application menus as they exist in iA Writer
* modify window chrome (e.g. removing the gutter, and whatever)
* Customize stage and associated preferences to improve line length control (i.e. line margins and character per line control)
* Include iA Writer’s specific Focus menu functionality— focus mode, parts of speech highlighting, and style checker—in TextMate’s unique way, via bundles.

An insane amount of work, yes, even if it could be done, but it would be the only option on the market that has the usability of iA Writer but for support of Textile. Besides only five people wanting it, why does that editor not exist?

Such a conversion would mean letting go of TextMate as a code editor, dropping all the other standard language bundles and themes that can be used. They would not make sense in a mimic of iA Writer for Textile.

If any skilled developer tries to go down that path, please let this author know what repository to follow.

# Resetting TextMate

For the rest of us, TextMate can be reset to its initial default state by clearing a few locations. Make sure to backup custom bundles first (or reinstall them from source). Then run the following commands.

This one removes the /Bundles directory, thereby clearing out all custom bundles, and delta files for standard bundles, in one shot:

```
rm -R ~/Library/Application\ Support/Textmate
```

This next command removes any preferences that TextMate may have set in the course of you editing bundles, configuring the View, and so forth:

```
rm -R ~/Library/Preferences/com.macromates.*
```

And this last command ensures any cached files or links are removed that may have been tied with any previous custom conditions:  

```
rm -R ~/Library/Caches/com.macromates.TextMate
```

Not all locations may have anything to remove, but it's okay to run the commands to make sure.

# License

This bundle maintains the license of the bundle from which it started, the [standard TextMate bundle for Textile](https://github.com/textmate/textile.tmbundle)...

If not otherwise specified (see at bottom), files in this repository fall under the following license:

	Permission to copy, use, modify, sell and distribute this
	software is granted. This software is provided "as is" without
	express or implied warranty, and with no claim as to its
	suitability for any purpose.

An exception is made for files in readable text which contain their own license information, or files where an accompanying file exists (in the same directory) with a “-license” suffix added to the base-name name of the original file, and an extension of txt, html, or similar. For example “tidy” is accompanied by “tidy-license.txt”.