# Settings

## What you will find here

Here you will see a detailed definition of every one of all the settings you can modify to obtain the results you want in your animations.

## All Settings

When you open the program for the first time, you will see the **default settings**. Tweak them to your liking, everything will autosave.

Here's a list with all the settings there are and their default values. Click on any of them to see more information.

| Setting | Default value |
|:-------|:--------------:|
| [Code](#code) | [See default](#code) |
| [Title](#title) | `test.py` |
| [Watermark](#watermark) | `@kodx` |
| [Icon path](#icon-path) | `Default Python Logo` |
| [Show header](#show-header) | `True` |
| [Show line numbers](#show-line-numbers) | `False` |
| [First line number](#first-line-number) | `1` |
| [Extra line numbers](#extra-line-numbers) | `0` |
| [Insert symbol](#insert-symbol) | `-` |
| [Terminal insert symbol](#terminal-insert-symbol) | `█` |
| [Visual indentation spaces](#visual-indentation-spaces) | `2` |
| [In-file indentation spaces](#in-file-indentation-spaces) | `4` |
| [Mode](#mode) | `vertical` |
| [Resolution](#resolution) | `fullhd` |
| [Fps](#fps) | `30` |
| [x](#x) | `1080` |
| [y](#y) | `1920` |
| [Margin top](#margin-top) | `9` |
| [Margin left](#margin-left) | `11.5` |
| [Margin bottom](#margin-bottom) | `40` |
| [Margin right](#margin-right) | `20` |
| [Max terminal height](#max-terminal-height) | `65` |
| [Code font size](#code-font-size) | `5` |
| [Header size](#icon-size) | `6` |
| [Line separation](#line-separation) | `2` |
| [Gap icon-header](#gap-icon-header) | `3` |
| [Gap header-content](#gap-header-content) | `5` |
| [Gap number line-code](#gap-number-line-code) | `8` |
| [Top terminal margin](#top-terminal-margin) | `6` |
| [Gap code-terminal](#gap-code-terminal) | `5` |
| [Cursor color](#cursor-color) | `(255, 255, 255)` |
| [Background color](#background-color) | `(25, 25, 25)` |
| [Terminal background color](#terminal-background-color) | `(15, 15, 15)` |
| [Header color](#header-color) | `(170, 170, 170)` |
| [Watermark color](#watermark-color) | `(80, 80, 80)` |
| [Volume at lower level](#volume-lower-level) | `30` |
| [Filename](#filename) | `video` |
| [Export path](#export-path) | `""` |
| [Only last frame](#only-last-frame) | `False` |


## Code

![Code setting](imgs/set_code.png){ width="200px" }

This is the code that will be animated. See [scripting](20-scripting.md) for more details.

The default value for code is `# Type your code here! ## wait 5 for 25 wait 10\nprint('This is a test') ## wait 5 for voice wait 10`

## Title

![Title setting](imgs/set_title.png){ width="200px" }

The title that will appear next to the icon. **This is not the filename**. [See filename details here](#filename). 
The title is hosted in the header, so [hiding the header](#show-header) will hide the title as well.

## Watermark

![Watermark setting](imgs/set_watermark.png){ width="200px" }

The watermark that will appear at the top right of the video.

> Normally, use your username if you're sharing on social media.

Leave blank for no watermark.
The watermark is hosted in the header, so [hiding the header](#show-header) will hide the watermark as well.

## Icon path

![Icon setting](imgs/set_icon.png){ width="200px" }

The icon that will appear at the top left of the image. The default icon is the Python logo. You can add your own **PNG/JPG** square image. If your image is not square, it will be stretched to be 1/1.

The icon is hosted in the header, so [hiding the header](#show-header) will hide the icon as well.

## Show header

![Show header setting](imgs/set_header.png){ width="405px" }

You can decide whether to show or not the header.