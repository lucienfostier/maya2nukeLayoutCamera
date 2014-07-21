maya2nukeLayoutCamera
=====================

Example tool for exporting plate layout decisions applied in maya (filmBack_Translates/Rotate/Scale) to a camera in nuke. This translates the plate in nuke so the renders from 3d line up.

Why? So the directors decisions of where to position the plate in a vfx shot is set early in the pipe and all artists see that decision. In Maya using the ImagePlane with the same filmBack_Translate settings allows playblasts with a lined up plate that reflects the position of the plate in the avid edit reference.  

How? Adjust the Render camera in Maya  with these settings to set layout position of plate in frame:
filmback.filmTranslateH
filmback.filmTranslateV
filmback.filmRollValue
filmback.postscale
:link these values to a locater and export as fbx or whatever.
translateX=camera.filmTranslateH
translateY=camera.filmTranslateV
rotatetX=camera.filmRollValue
scaleX=camera.postscale
:you will also need a matchmoveCamera and the render camera in nuke.

Notes: 

If you were developing a pipeline you would do this in a more sophisicated way, my recommendations would be either bake the data into an exr and get it from there, hackIvan's abc Importer, or develop a layoutCamera in Nuke that exports a matrix and use that in nuke. (this would allow for full cornerPin type translates)


licence
===========
By downloading a file from this repository you agree to the general license terms below.
Copyright (c) 2010 till present
All rights reserved.

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:
Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.
Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.
Neither the name of vfxwiki nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.
THIS SOFTWARE IS PROVIDED
