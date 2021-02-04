# tWriter for Textile Authors

The tWriter bundle is an extended [Textile language](https://github.com/textile) bundle for [TextMate 2](https://macromates.com/). It is specifically meant for people who use [Textpattern CMS](https://textpattern.com) for personal web publishing, love the usability of [iA Writer](https://ia.net/writer) as a simple prose development application, but prefer Textile over Markdown. To that end, tWriter comes with its own monochrome themes, light and dark, modelled after the iA Writer experience.

The Textile grammar is extended beyond what the standard Textile bundle for TextMate provides; it accounts for more of the contemporary Textile syntax used in [php Textile](https://github.com/textile/php-textile), which is supported natively in Textpattern. Such syntax accounts for content features like block quotes, endnotes (advanced footnotes), and more complex table structures. The grammar also pulls out a few embedded wrapping pairs that were handled a little too generically in the standard version; whether or not an author may really need them, they are now more visually recognizable.

The tWriter bundle also changes many of the menu actions that come in the standard Textile bundle; removing those for basic Textile and (eventually) adding some new ones for the more advanced elements.

# Work in Progress

The author is not a developer, not even close, and [TextMate documentation](https://github.com/textmate/textmate/wiki) is deplorable for such a state of mind. So Issues will be created for things the author would like to do but does not know how, or can't figure out after too much time trying. Anyone with insights to solving those issues is more than welcome to chime in.


# Installation


The tWriter bundle should be added to the /Bundles directory at:

```
~/Library/Application\ Support/TextMate/Bundles
```

Done.

Open TextMate and find ’tWriter’ available under the Bundles menu and in the bundles editor list. It will appear as ‘Textile’ in the language selector options at bottom of window chrome because the grammar file is still named ‘Textile’. If you prefer seeing ‘Textile’ consistently throughout, edit the name in the info.plist file. 

# The iA Writer Experience


The tWriter themes will not give you the full iA Writer experience by themselves. You should also do the following if you want to go further with it.

First, download and install on your machine the [iA Writer Duospace](https://www.fontsquirrel.com/fonts/ia-writer-duospace) family.

Then, when working on a .textile document, make the following configurations via the View menu:

1. **View > Font > Show Fonts**...
   * Collecton: Fixed Width
   * Family: iA Writer Duospace
   * Typeface: Regular
   * Size: 18
2. **View > Enable Soft Wrap**
3. **View > Wrap Column > Use Window Frame**



Likewise, the one [hidden setting](https://github.com/textmate/textmate/wiki/Hidden-Settings) to control line height, `fontAscentDelta`, does not seem to work for this author. Try it yourself and see if you have better luck...

Close TextMate, then run the following command ('1.5' is the line height value, use the value you want; 1.3, 1.7, 2, whatever):

```
defaults write com.macromates.TextMate fontAscentDelta 1.5
```

Open TextMate again.

That will supposedly apply a line height in TextMate for the value you set. You can verify what line height might be set by running:

```
 defaults read com.macromates.TextMate fontAscentDelta
```


```
defaults delete com.macromates.TextMate fontAscentDelta
```


# License


If not otherwise specified (see at bottom), files in this repository fall under the following license:

	Permission to copy, use, modify, sell and distribute this
	software is granted. This software is provided "as is" without
	express or implied warranty, and with no claim as to its
	suitability for any purpose.

