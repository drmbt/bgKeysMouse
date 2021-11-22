# bgKeysMouse
python keyboard and mouse input state while TD is not in focus

these components work by leveraging the ctypeslibrary and windll.User32.GetKeyState functions to access keyboard and mouse information when TouchDesigner is in the background;  
by default if TD is not the in focus app these processes don't run.

We do this be importing the library and cooking the query every frame with an execute dat, 
which is something i like to turn off if I'm not using it.  
The technique is based on a forum post with contributions from Harvey Moon and Idzard 
that can be [found here:](https://forum.derivative.ca/t/chop-with-mouse-position-outside-touchdesigner-window/8857)




