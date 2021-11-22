# bgKeysState_simple

This technique is based on a forum post with contributions from Harvey Moon and Idzard 
that can be [found here:](https://forum.derivative.ca/t/chop-with-mouse-position-outside-touchdesigner-window/8857)

The bgKeyboardMouse component brings to DAT/CHOP space the state of the keyboard and mouse when another program
is in focus and TouchDesigner is in the background

These components work by leveraging the ctypes library and windll.User32.GetKeyState functions 
to access keyboard and mouse information when TouchDesigner is in the background;  
by default if TD is not the in focus app these processes don't run.

We do this be importing the library and cooking the query every frame with an execute dat, 
which is something i like to turn off if I'm not using it by toggling of the relevant Active flag.

Since we are querying the state of every key every frame, an editable query table 
allows us to define the order and scope of the desired keys we're polling for.

the GetAsyncKeyState() function requires the virtual key unicode value as defined [here:](http://www.kbdedit.com/manual/low_level_vk_list.html) and [here:](https://docs.microsoft.com/en-us/windows/win32/inputdev/virtual-key-codes). 

For ease of use this _simple component converts user defined characters from the table to CHOP/DAT land with the windll.User32.VkKeyScanW(ord(c)) char2key function.
This is fine for getting a few letters and numbers, but doesn't give us access to characters like 'spacebar', 'enter' etc. that aren't represented by a single character. 

to get all keys, use the _all component (still under developement) to get values directly from virtual keys



