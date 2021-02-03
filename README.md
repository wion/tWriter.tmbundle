# tWriter

The tWriter bundle is an extended [Textile language](https://github.com/textile) bundle for [TextMate 2](https://macromates.com/). It is specifically meant for people, like yours truly, who use [Textpattern CMS](https://textpattern.com) for personal web publishing, love the usability of [iA Writer](https://ia.net/writer) as a simple prose development application, but prefer Textile over Markdown. To that end, tWriter comes with its own monochrome themes, light and dark, modelled after the iA Writer experience. To be sure, the tWriter bundle for Textile will *not* make sense if any other standard TextMate theme is used. This is a specific bundle for a specific aesthetic experience.

The Textile grammar is extended beyond what the standard Textile bundle for TextMate provides; it accounts for more of the contemporary Textile syntax used in [php Textile](https://github.com/textile/php-textile), which is supported natively in Textpattern. Such syntax accounts for content features like block quotes, endnotes (advanced footnotes), and more complex table structures. The grammar also pulls out a few embedded wrapping pairs that were handled a little too generically in the standard version; whether or not an author may really need them, they are now more visually recognizable. The tWriter bundle will also (but not yet) change many of the menu actions that come in the standard version; removing them for basic Textile and add some for the more advanced elements.

That said, the author is not a developer, not even close, and [TextMate documentation](https://github.com/textmate/textmate/wiki) is deplorable for such a state of mind. So Issues will be created for things the author would like to do but does not know how, or can't figure out after too much time trying. Anyone with insights to solving those issues is more than welcome to chime in.

# Installation

Since this is a custom bundle for a language already provided in TextMate by default, you should first make sure to deactivate, uncheck, turn off the standard Textile bundle in TextMate via the Bundles index at **TextMate > Preferences > Bundes > [Languages]**. This ensures you do not have duplicate 'Textile' entries in your application lists confusing you needlessly.

The tWriter bundle (or any custom bundle) can then be added to the /Bundles directory at:

```
~/Library/Application\ Support/TextMate/Bundles
```

Done. Open TextMate and find 'Textile' available under the Bundles menu, in the bundles editor list, and in the bundle selector options at bottom of window chrome.

# The iA Writer Experience

When using tWriter, the author also recommends deactivating the Themes bundle at **TextMate > Preferences > Bundes > [Themes]**. This will leave only the 'tWriter Light' and 'tWriter Dark' themes in the themes options at **View > Themes > [theme]**. Again, the tWriter bundle was designed for these themes, so eliminating the unusable standard options from the menu is the sensible move. Or, you can always design your own themes against the tWriter grammar.

The tWriter themes will not by themselves give you the full iA Writer experience, however. You should also do the following for the best effect.

First, download and install on your machine the [iA Writer Duospace](https://www.fontsquirrel.com/fonts/ia-writer-duospace) family.

Then, when working on a .textile document, make the followng configurations via the View menu:

1. View > Font > Show Fonts, then set:
   * Collecton: Fixed Width
   * Family: iA Writer Duospace
   * Typeface: Regular
   * Size: 18
2. View > Enable Soft Wrap
3. View > Wrap Column > Use Window Frame

Finally, you may find that dragging the application's window to at least 80% of your screen width (e.g. MBP 13" screen) is necessary to prevent too much scrolling off the right side of the window. Not sure why this off-screen scrolling happens when it should wrap to window frame, but it does. If you expand the application window to full screen, there is no horizontal scrolling, but then the line lengths are rediculous.

Along with one of the tWriter themes, the above configuration is a pretty good approximation of the iA Writer aesthetic. Unfortunately, TextMate does not provide any means for controlling left and right margins inside the editing window. And the one [hidden setting](https://github.com/textmate/textmate/wiki/Hidden-Settings) to control line height, `fontAscentDelta`, does not seem to work for this author. Maybe you have better luck.

# License

This bundle maintains the license of that from which it started, the [standard TextMate bundle for Textile](https://github.com/textmate/textile.tmbundle)...

If not otherwise specified (see at bottom), files in this repository fall under the following license:

	Permission to copy, use, modify, sell and distribute this
	software is granted. This software is provided "as is" without
	express or implied warranty, and with no claim as to its
	suitability for any purpose.

An exception is made for files in readable text which contain their own license information, or files where an accompanying file exists (in the same directory) with a “-license” suffix added to the base-name name of the original file, and an extension of txt, html, or similar. For example “tidy” is accompanied by “tidy-license.txt”.
