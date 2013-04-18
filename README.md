xmonad-layout-padding
=====================

A layout module for xmonad featuring window padding

## Usage

Since this is not yet included in Xmonad-Contrib, simply download
Padding.hs and place it in your '~/.xmonad/lib/' folder (create it if
it doesn't exist). Then it can be imported with

~~~
import Padding
~~~

The `Padding` module only exports a single function: `padding`, which
takes two arguments: the first is the amount of padding for the
top/bottom of windows, the second is for the sides (just as with css).

## Example

~~~{.haskell}
-- File: xmonad.hs
import XMonad

import Padding

main = xmonad $ defaultConfig
	{ -- Whatever your usual configs are
      layoutHook = myLayoutHook
	}


-- Use whatever layouts you want
myLayoutHook = centered ||| tiled ||| Full
    where  
        -- Padding modifies a layout
        -- the centered layout is like Full, except with 175 pixels of
        -- space on the left and right sides.
        centered = padding 0 175 $ Full

        -- the tiled layout is like Tall, except each window will have 5
        -- pixels of space on top and 2 on the sides
        tiled = padding 5 2 $ Tall 1 (5/8) (5/100)
~~~

## Acknowledgements

This module is based extremely heavily (as in - I barely changed
anything at all) on Xmonad.Layout.Spacing, (c) Brent Yorgey, originally
(and still) licensed under a BSD3 license.
